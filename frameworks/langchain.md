# LangChain

## What it is (brief)

LangChain is a framework for building applications around LLMs. It provides building blocks to:

- Compose prompts and model calls
- Integrate external tools/APIs
- Retrieve data (RAG) using vector stores and retrievers
- Add memory/state and build multi-step “chains”
- Add observability patterns and common integrations

## When to use it

Use LangChain when you need to build an LLM application that benefits from **composition + integrations**, for example:

- RAG apps (docs → embeddings → retrieval → answer)
- Tool-using agents (LLM decides actions + calls tools)
- Pipelines where steps are reusable (extract → validate → transform → summarize)
- Prototypes that need to connect many providers quickly

## Why / the value

- **Integration surface**: lots of connectors (LLMs, vector DBs, loaders, tools).
- **Faster iteration**: standardized abstractions for chains, tools, retrievers.
- **Maintainability**: shared patterns for common LLM app architectures.

## When *not* to use it

- If the app is a single prompt + single model call (plain SDK may be simpler).
- If you want maximum control/minimal abstraction (direct provider SDKs).

## Related

- For stateful, graph-based multi-agent workflows, see [LangGraph](./langgraph.md).

