# IPAC: Integrated Personality as Code

**Coined by:** [Michael Ashley](https://mjashley.com) ([@smashingtags](https://github.com/smashingtags))  
**Date:** March 26, 2026 at 08:12 EDT  
**Origin:** Discord, hour 28 of no sleep

---

IPAC is a methodology for encoding a human's knowledge, decision-making patterns, personality, voice, and operational context into structured, version-controlled files that AI agents can load and execute.

It makes the founder reproducible infrastructure rather than an irreplaceable snowflake.

## Read the manifesto

→ **[IPAC-MANIFESTO.md](./IPAC-MANIFESTO.md)** — the full methodology  
→ **[spec/](./spec/)** — file format specifications  
→ **[examples/](./examples/)** — reference implementation templates  
→ **[ideas/](./ideas/)** — research notes and future concepts  
→ **[Blog post](https://mjashley.com/writing/ipac-integrated-personality-as-code/)** — the story behind it

## The IaC analogy

Infrastructure as Code changed how we think about servers: from hand-configured snowflakes to reproducible, version-controlled cattle. IPAC does the same thing for people.

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

1. **Text over brain.** If it's not written down, it doesn't survive a session restart.
2. **Version everything.** Git tracks personality evolution the same way it tracks code.
3. **Fail fast, fix fast.** Instincts are CI/CD for behavior.
4. **Drift detection.** Regular maintenance catches when reality diverges from stored state.
5. **Reproducibility.** Any compatible model can load the files and approximate the personality.
6. **Remove to improve.** Personality files get refined, not just accumulated.

## Tools

- **[Operator Kit](https://www.npmjs.com/package/@imogenlabs/operator-kit)** — the IPAC scaffolding tool (`terraform init` for personality)
- **[OpenClaw](https://openclaw.ai)** — AI gateway runtime (not built by us, used by us)
- **[QMD](https://github.com/nickarella/qmd)** — local vector search for memory retrieval

## Key concepts

- **Memory canaries** — diagnostic primitives for testing agent session isolation ([ideas/memory-canaries.md](./ideas/memory-canaries.md))
- **Trust encoding** — the hard problem underneath personality encoding ([ideas/trust-encoding.md](./ideas/trust-encoding.md))
- **Session = Sprint** — Scrum methodology applied to AI agent sessions ([blog post](https://mjashley.com/writing/session-equals-sprint/))

## Status

This is an active research project, not a finished spec. The reference implementation has been running for 8 months. The ideas are evolving. Contributions, critiques, and prior art references are welcome.

## License

CC BY-SA 4.0 — share and adapt with attribution.

---

*Built by [Imogen Labs](https://imogenlabs.ai). Questions? [michael@mjashley.com](mailto:michael@mjashley.com)*
