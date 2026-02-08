# LangGraph

## What it is (brief)

LangGraph is a framework for building **stateful, multi-step LLM workflows** as graphs. Instead of a linear chain, you model your application as:

- **Nodes** (steps: call LLM, call tool, route, validate, etc.)
- **Edges** (transitions: deterministic or conditional)
- **State** (shared memory passed and updated across steps)

This is useful when your application has branching, loops, retries, or multiple agents collaborating.

## When to use it

Use LangGraph when you need:

- **Orchestration with control flow** (branching, cycles, fallbacks)
- **Multi-agent** setups (planner/executor, reviewer, specialized agents)
- **Long-running workflows** with checkpoints/resume
- **More predictable behavior** than a purely free-form agent loop

## Why / the value

- **Explicit control flow**: the graph makes execution paths visible and testable.
- **Reliability**: easier to add guards, retries, validation, and routing.
- **State management**: clear model of what is remembered and why.

## When *not* to use it

- If your workflow is simple and linear (a basic chain or a few function calls).
- If you don’t need explicit state/control flow (keep it simpler).

## Related

- If you mainly need integrations and reusable building blocks, see [LangChain](./langchain.md).

