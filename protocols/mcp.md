# MCP (Model Context Protocol)

## What it is (brief)

MCP (Model Context Protocol) is a standard way to let an AI assistant connect to **external tools and data sources** through “MCP servers”.

Instead of hardcoding every integration inside your app/agent, MCP defines a consistent interface so a model can:

- Discover available **tools** (capabilities) exposed by a server
- Call those tools with structured inputs/outputs
- Access **resources** (documents, files, metadata) in a uniform way

In practice, MCP helps you plug an assistant into systems like GitHub, Jira, databases, filesystems, internal APIs, etc., in a safer and more structured manner than free-form “call an API somehow”.

## Examples of MCP servers

Common categories:

- **Source control / code hosting**: GitHub (PRs, issues, diffs, checks)
- **Project management**: Jira (issues, transitions, comments)
- **Databases**: Postgres (read queries, metadata)
- **Files & documents**: filesystem access, Drive/Docs connectors
- **Browser automation**: page navigation, snapshots, form filling (useful for testing web apps)

## When to use it

Use MCP when:

- You need the model to interact with **real systems** (create issues, query a DB, fetch repo data)
- You want **standardized integrations** across different tools/providers
- You want a clear boundary between:
  - your application logic, and
  - the set of tool capabilities the model can access

## When *not* to use it

Avoid MCP (or keep it out of the critical path) when:

- The task can be solved with a **static prompt** or offline documents
- You only need a couple of simple API calls and a direct SDK is cleaner
- You have strong constraints on **latency, cost, or reliability** and tool calls would add overhead
- Security requirements demand extremely tight control and auditing, and you’re not ready to govern tool access properly

## Notes / good practices

- Keep tool scopes small and explicit (principle of least privilege).
- Prefer read-only tools where possible; require explicit user intent for side effects.
- Log tool calls and outputs for debugging and auditability.

