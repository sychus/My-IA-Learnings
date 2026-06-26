# MemPalace Setup Skill

## Purpose

Install and configure MemPalace as a local-first AI memory system for Claude Code using Docker. MemPalace stores conversation history verbatim, indexes it with local semantic search (no API key required), and exposes it to Claude Code as an MCP server.

## When to use

The user says "setup mempalace", "install mempalace", "configure mempalace", or asks to set up persistent memory for Claude Code.

## What you will do

Work through each phase in order. **Stop and report to the user if any phase fails** before continuing.

---

### Phase 1 — Verify prerequisites

Check that Docker is installed and running:

```bash
docker info
```

If Docker is not running, tell the user to start Docker Desktop and wait before continuing.

---

### Phase 2 — Build the Docker image

Build directly from the GitHub repo (no clone needed):

```bash
docker build -t mempalace https://github.com/MemPalace/mempalace.git
```

This takes a few minutes. It bundles the `extract` and `spellcheck` extras by default.

---

### Phase 3 — Download the embedding model

Run the container once so it downloads and caches the embedding model (~300 MB) into the named volume. CPU will spike — this is normal and only happens once:

```bash
docker run --rm -v mempalace-data:/data mempalace python -m mempalace.onboarding
```

If the onboarding command is not available, trigger the download by running a dummy mine:

```bash
docker run --rm -v mempalace-data:/data mempalace mine /tmp --mode convos 2>/dev/null || true
```

Wait until the process exits cleanly before continuing.

---

### Phase 4 — Register as MCP server in Claude Code

Read the current `~/.claude/claude.json`:

```bash
cat ~/.claude/claude.json
```

Add `mempalace` to the `mcpServers` block. The final entry must look exactly like this:

```json
"mempalace": {
  "command": "docker",
  "args": ["run", "-i", "--rm", "-v", "mempalace-data:/data", "mempalace"]
}
```

> **Critical:** the `-i` flag is required — JSON-RPC needs stdin. Without it the server silently fails.

After editing, validate the JSON is well-formed:

```bash
python3 -m json.tool ~/.claude/claude.json > /dev/null && echo "valid" || echo "INVALID JSON"
```

If invalid, fix it before continuing.

---

### Phase 5 — Backfill existing Claude Code transcripts

Mine all existing Claude Code sessions into the palace:

```bash
docker run --rm \
  -v mempalace-data:/data \
  -v ~/.claude/projects:/transcripts:ro \
  mempalace mine /transcripts --mode convos
```

This is idempotent — safe to run multiple times. Large transcript collections may take several minutes.

---

### Phase 6 — Verify the MCP server is reachable

Test that the container starts and responds correctly:

```bash
echo '{"jsonrpc":"2.0","id":1,"method":"initialize","params":{"protocolVersion":"2024-11-05","capabilities":{},"clientInfo":{"name":"test","version":"0.0.1"}}}' \
  | docker run -i --rm -v mempalace-data:/data mempalace
```

A valid response contains `"result"` in the output. If you see JSON back, the server is working.

Tell the user to open a new Claude Code session and run `/mcp` — `mempalace` should appear as connected with its tools listed.

---

### Phase 7 — Report to the user

Summarize:

| Check                                  | Status |
| -------------------------------------- | ------ |
| Image built                            | ✓/✗    |
| Embedding model cached                 | ✓/✗    |
| MCP server registered in `claude.json` | ✓/✗    |
| Transcripts backfilled                 | ✓/✗ (N sessions processed) |
| Server responds to initialize          | ✓/✗    |

Tell the user:

- To open a **new** Claude Code session for the MCP server to be picked up
- To run `/mcp` to confirm `mempalace` is listed as connected
- That from now on, Claude can call `mempalace_search` and `mempalace_recall` directly during sessions

---

## Notes

- All data persists in the Docker named volume `mempalace-data`. **Never delete this volume** unless intentionally resetting.
- To mine a specific project into its own wing:
  ```bash
  docker run --rm -v mempalace-data:/data -v /path/to/project:/work mempalace mine /work --wing project-name
  ```
- To search from the CLI:
  ```bash
  docker run --rm -v mempalace-data:/data mempalace search "your query"
  ```
- GPU variant (faster embeddings):
  ```bash
  docker build -f Dockerfile.gpu -t mempalace:gpu .
  ```
  Then use `--gpus all` in the run args.
