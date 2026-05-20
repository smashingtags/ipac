# IPAC: Integrated Personality as Code

IPAC is a framework for encoding a person's knowledge, decision-making patterns, voice, and operational context into structured, version-controlled files that AI agents can load and execute.

The goal is practical: make the operator's working context portable, inspectable, and reproducible across sessions and models — instead of trapped in one person's head or one chat history.

## Background

The name and structure came out of a long working session in March 2026 while building tooling around long-running AI agents. It's a label for a pattern several people are converging on independently; prior art and parallel approaches are welcome and tracked in `ideas/`.

## Read more

- **[IPAC-MANIFESTO.md](./IPAC-MANIFESTO.md)** — the full write-up
- **[spec/](./spec/)** — file format specifications
- **[examples/](./examples/)** — reference implementation templates
- **[ideas/](./ideas/)** — open questions and research notes
- **[Blog post](https://mjashley.com/writing/ipac-integrated-personality-as-code/)** — longer-form context

## The IaC analogy

Infrastructure as Code shifted server management from hand-configured one-offs to reproducible, version-controlled definitions. IPAC borrows that pattern for the human context an agent needs to operate on someone's behalf.

| IaC concept | IPAC equivalent | Implementation |
|---|---|---|
| Terraform state | Long-term memory | MEMORY.md + ref-*.md |
| Config files | Identity and values | SOUL.md, IDENTITY.md |
| Environment variables | Credentials/endpoints | TOOLS.md |
| User data | Human context | USER.md |
| CI/CD pipeline | Behavioral learning | instincts/*.yaml |
| Monitoring/alerts | Proactive checks | HEARTBEAT.md + cron |
| Drift detection | Memory maintenance | Vectorization + daily logs |
| Runbooks | Operational skills | Skill files |
| Backup/DR | Knowledge persistence | Git + embeddings |

## Principles

- **Write it down.** If it isn't in a file, it doesn't survive a session restart.
- **Version everything.** Git is fine for tracking how context evolves over time.
- **Fast feedback loops.** Treat behavioral rules like CI: catch regressions early.
- **Detect drift.** Schedule maintenance so stored context doesn't diverge from reality.
- **Portability.** Any reasonably capable model should be able to load the files and produce comparable behavior.
- **Refine, don't accumulate.** Prune files; don't just append.

## Tools we use

- **Operator Kit** — scaffolding for IPAC repos (think `terraform init`, but for operator context)
- **OpenClaw** — AI gateway runtime (third-party; we just use it)
- **QMD** — local vector search for memory retrieval

## Key concepts

- **Memory canaries** — diagnostic primitives for testing agent session isolation ([ideas/memory-canaries.md](./ideas/memory-canaries.md))
- **Trust encoding** — the harder problem sitting underneath context encoding ([ideas/trust-encoding.md](./ideas/trust-encoding.md))
- **Session = Sprint** — every agent session is a sprint with a 10-minute timebox ([ideas/session-equals-sprint.md](./ideas/session-equals-sprint.md))
- **Story points** — how estimation evolved from team planning poker to solo AI agent sessions ([ideas/story-points.md](./ideas/story-points.md))

## Status

Active research, not a finished spec. The reference implementation has been running for about 8 months. Critiques, prior art, and PRs welcome.

## License

CC BY-SA 4.0 — share and adapt with attribution.

Built at Imogen Labs. Questions: michael@mjashley.com
