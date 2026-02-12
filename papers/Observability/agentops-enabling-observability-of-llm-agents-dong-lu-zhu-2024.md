# AGENTOPS: Enabling Observability of LLM Agents (Dong et al., 2024) — Summary

## Citation / reference

- Liming Dong, Qinghua Lu, Liming Zhu (Data61, CSIRO) (Dec 2024). **“AGENTOPS: Enabling Observability of LLM Agents.”** arXiv:2411.05285v2 (Nov 2024).  
  PDF (in this repo): [`ENABLING OBSERVABILITY OF LLM AGENTS.pdf`](./ENABLING%20OBSERVABILITY%20OF%20LLM%20AGENTS.pdf)  
  arXiv: `https://arxiv.org/abs/2411.05285`

## What problem it addresses

LLM agents are autonomous, non-deterministic, and can evolve over time. This makes them harder to operate safely than “single-call” LLM apps. From a DevOps perspective, we need **observability** to understand what agents did and why, detect anomalies, and prevent failures—especially when accountability is shared across stakeholders (agent owners, model providers, tool providers).

## What the paper contributes

The paper introduces **AgentOps**, a DevOps paradigm tailored to LLM agents, and proposes:

- An **artifact relationship model** for key agent artifacts and how they relate across the lifecycle.
- A **taxonomy of AgentOps** that specifies which artifacts and metadata should be traced to enable effective observability.

The taxonomy is developed from a **systematic mapping study** of existing AgentOps/observability tools (including open-source and commercial platforms).

## Key idea (high signal)

Observability should go beyond “LLM call metrics” and include **agent-specific artifacts** such as:

- goals and constraints
- reasoning outputs
- plans and historical plans
- workflows, tasks, and tool interactions
- evaluation results
- guardrails (targets and actions)

In other words: if you can’t trace the agent’s **plans, tools, and decisions**, you can’t reliably debug or govern it.

## What to trace (how the taxonomy looks, conceptually)

The paper models a run as traces/spans and describes agent-relevant spans such as:

- **Agent span**: role/persona metadata
- **Reasoning span**: context, retrieved knowledge, inference rules/boundaries, outcome
- **Planning span**: goal, constraints, context, historical plans
- **Workflow / task / tool spans**: tasks, dependencies, operational context, execution history, tool name/version/config
- **Evaluation span**: test cases, metrics, results
- **Guardrail span**: guardrail targets + actions (block/validate/filter/etc.)
- **LLM span**: model name/version/parameters (e.g., temperature, max tokens)

## Practical takeaways

- Treat agent operations like production systems: implement **monitoring, logging, tracing, and analytics** for agent artifacts—not just prompts.
- Add explicit **evaluation and guardrail spans** so safety policies are observable and auditable.
- Use the taxonomy as a checklist when designing an “AgentOps” layer for your agents (what you must capture to debug incidents and prove compliance).

## Limitations and future work (as stated)

- Tool selection may miss some rapidly emerging AgentOps tools.
- The taxonomy may not cover all possible traceable attributes.
- Future work: validate the taxonomy through real-world case studies and build an AgentOps tool prototype.

