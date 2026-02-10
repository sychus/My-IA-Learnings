# Proposals

Working documents and ideas that are meant to be iterated on (not final “definitions”).

## Index

- [Standardizing structure (team-owned prompts, skills, and global rules)](./standarizing-structure/)

## Standardizing structure (what it is)

The goal of the `standarizing-structure/` proposal is **not** to have one person “manage the AI” for the whole project. Instead, it proposes a structure that a **team of humans** can maintain together, where each discipline contributes the prompts, skills, and rules they know best:

- **Product / Product Owners**: user needs, feature specs, acceptance criteria, definition of done, domain language.
- **Dev / Engineering**: architecture, coding conventions, stack choices, clean code practices, patterns, workflows.
- **Infra / Security**: deployment workflows, security boundaries, secrets handling, compliance constraints.
- **QA**: test strategy, test levels, quality gates, bug triage, regression practices.

On top of role-specific contributions, the proposal includes **global, non-negotiable project rules** (constraints, conventions, security policies) so AI outputs stay consistent across contributors and over time.

If you want the details, start here:

- `proposals/standarizing-structure/ai/OWNERSHIP.md` (who owns what, and how agents should consume it)
- `proposals/standarizing-structure/ai/role-skills/README.md` (role-based skill library)

