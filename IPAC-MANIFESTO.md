# IPAC — Integrated Personality as Code

## Definition

Integrated Personality as Code (IPAC) is a framework for encoding a person's knowledge, decision-making patterns, voice, and operational context into structured, version-controlled files that AI agents can load, execute, and evolve over time.

The aim is practical: take the working context an operator carries around in their head — what they know, how they decide, how they sound, what they care about — and make it portable, inspectable, and reproducible across sessions and models.

## The analogy

Infrastructure as Code (IaC) changed how we think about servers: from hand-configured one-offs to reproducible, version-controlled definitions. IPAC borrows that pattern for the human context an agent needs to operate on someone's behalf.

Instead of Terraform provisioning a server, IPAC provisions an AI agent with a person's:

- Identity and values
- Domain expertise and tacit knowledge
- Decision-making patterns
- Communication style and voice
- Relationships and social context
- Operational procedures and preferences

## The stack

| IaC concept | IPAC equivalent | File/system |
|---|---|---|
| Terraform state | Long-term memory | MEMORY.md + memory/ref-*.md |
| Config files | Identity & values | SOUL.md, IDENTITY.md |
| Environment variables | Credentials & endpoints | TOOLS.md |
| User data | Human context | USER.md |
| CI/CD pipeline | Behavioral learning | Instincts (pattern → rule YAML) |
| Container image | Physical presence | Voice clone + digital avatar |
| Helm values | Brand identity | Brand kit (colors, logos, tone) |
| Monitoring & alerts | Proactive checks | Heartbeat system + cron |
| Drift detection | Memory maintenance | Vectorization + daily logs |
| Runbooks | Operational skills | Skill files (SKILL.md) |
| Service mesh | Agent communication | Multi-agent orchestration |
| Backup/DR | Knowledge persistence | Git + vectorized embeddings |

## What's OpenClaw and what's IPAC

It's worth being explicit about the boundary between the runtime and the methodology, because they're often conflated.

**OpenClaw** is a third-party AI gateway runtime (open source, openclaw.ai). It defines the file conventions used here — SOUL.md, IDENTITY.md, USER.md, MEMORY.md, AGENTS.md, HEARTBEAT.md, TOOLS.md — and provides the memory backend (QMD), channel plugins, cron scheduling, and agent dispatch. We didn't build OpenClaw; we build on top of it.

**IPAC** is the framework layered on top:

- The IaC-to-personality analogy and naming
- A reference implementation (eight months of populating OpenClaw's files with real operational content)
- The instinct system (mistakes captured as YAML rules — CI/CD for behavior)
- A memory architecture (ref-*.md topic files, daily logs, naming conventions)
- Heartbeat checklist content (what the proactive task runner actually checks)
- A multi-agent team design with capability boundaries
- Session = Sprint, a way of applying sprint-style structure to agent sessions
- Memory canaries, a diagnostic primitive for session isolation
- Trust encoding, the alignment question underneath context encoding
- Operator Kit, a scaffolding tool

A short way to say it: OpenClaw gives you SOUL.md. IPAC is one set of opinions about what to put in it and why.

## The reference implementation

This was built over roughly eight months (August 2025 – March 2026) without yet having a name for the overall pattern. The table below tries to honestly separate what comes from upstream conventions from what's specific to this implementation, so anyone evaluating the framework can see where the seams are.

| Component | Source | What's in this implementation |
|---|---|---|
| SOUL.md, IDENTITY.md, USER.md | OpenClaw convention | The actual personality, values, and human context inside them |
| MEMORY.md, memory/ | OpenClaw convention | A curation methodology, ref-*.md naming, topic organization |
| AGENTS.md | OpenClaw convention | Behavioral rules, safety constraints, a proceed-gate pattern |
| HEARTBEAT.md | OpenClaw convention | A proactive monitoring checklist (inbox, calendar, memory hygiene) |
| instincts/*.yaml | This framework | Self-written behavioral rules generated from agent mistakes |
| Memory filename convention | This framework | ref-*.md naming and daily log format |
| Session = Sprint | This framework | Sprint-style structure applied to agent sessions |
| Memory canaries | This framework | A diagnostic primitive for testing session isolation |
| Voice clone | Third-party (ElevenLabs) | Voice training data and configuration |
| Digital avatar | Third-party (HeyGen) | Avatar configuration |
| Brand kit | This framework | Visual identity for agent presence |
| QMD vectors | OpenClaw memory backend | ~16,000 embedded chunks of curated content |

## The scaffolder: Operator Kit

Operator Kit is an IPAC provisioning tool — it generates the file structure, memory system, instinct framework, cron jobs, and multi-agent config. It's roughly what `terraform init` is to IaC. MIT licensed.

## Principles

- **Write it down.** If it isn't in a file, it doesn't survive a session restart (or a nap).
- **Version everything.** Git tracks how context evolves the same way it tracks code.
- **Fast feedback loops.** Treat behavioral rules like CI: catch regressions early and turn mistakes into automated guardrails.
- **Detect drift.** Schedule maintenance so stored context doesn't quietly diverge from reality.
- **Portability.** Any reasonably capable model should be able to load the files and produce comparable behavior.
- **Refine, don't accumulate.** Prune files; don't just append.

## Influences

- Infrastructure as Code (Terraform, Ansible, Pulumi) — treating systems as code
- Toyota Production System / Kaizen — continuous improvement through elimination
- Agile/Scrum — short cycles with explicit planning, daily check-ins, and retros

## Adjacent and parallel work

Several people are converging on similar patterns from different directions. Some adjacent work worth knowing about:

- Daniel Miessler's "Personal AI Infrastructure" (PAI) — agent infrastructure, with a different emphasis than personality/context encoding
- Academic work on AI personality expression — mostly psychometric, less operational
- Various commercial "AI personality" products — typically configuration UIs rather than file-first approaches

IPAC's specific angle is treating operator context as infrastructure: version-controlled, reproducible, evolvable, and model-agnostic. If you know of prior or parallel work that fits the same shape, please open an issue or PR in `ideas/` — the goal is to map the space, not stake a claim on it.
