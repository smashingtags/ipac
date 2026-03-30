# IPAC file structure specification

Version: 0.1.0 (draft)

## Required files

These files form the minimum viable IPAC implementation:

```
workspace/
├── SOUL.md              # Core personality, values, communication style
├── IDENTITY.md          # Agent role, title, self-concept
├── USER.md              # Human biography, preferences, patterns
├── MEMORY.md            # Curated index pointing to topic files
├── AGENTS.md            # Behavioral rules, safety constraints
└── memory/
    ├── ref-*.md         # Evergreen topic references
    └── YYYY-MM-DD.md    # Daily session logs
```

## Optional files

These extend the base implementation:

```
workspace/
├── TOOLS.md             # Operational manifest (APIs, credentials, procedures)
├── HEARTBEAT.md         # Proactive monitoring checklist
├── BOOTSTRAP.md         # First-run initialization instructions
├── instincts/
│   └── *.yaml           # Self-written behavioral rules from mistakes
├── brand-kit/           # Visual identity (logos, colors, fonts)
└── skills/              # Operational skill definitions
```

## File format conventions

All files are plain-text Markdown unless otherwise specified.

### SOUL.md

The agent's personality definition. Should contain:

- Name and role
- Communication style (tone, formality, humor)
- Core values and priorities
- Relationship to the human
- Hard rules and constraints

SOUL.md is loaded into system context on every session start. Keep it under 2,000 words.

### IDENTITY.md

The agent's self-concept. Separate from SOUL.md because identity can change (promotions, role shifts) while personality stays stable.

### USER.md

Everything the agent needs to know about the human. Biography, work history, preferences, communication patterns, family context. This is the human's terraform state.

### MEMORY.md

An index file, not a dump. Points to ref-*.md files by topic. Think of it as a table of contents for the agent's long-term knowledge.

### memory/ref-*.md

Evergreen reference files organized by topic. Examples:
- ref-infrastructure.md (servers, IPs, containers, DNS)
- ref-products.md (product status, pricing, repos)
- ref-sales-and-revenue.md (customers, revenue, metrics)

Naming convention: `ref-<topic>.md`, lowercase, hyphens.

### memory/YYYY-MM-DD.md

Daily session logs. Raw chronological record of what happened. These are short-term memory that eventually feeds into ref files.

### instincts/*.yaml

Behavioral rules the agent writes itself after making mistakes. Format:

```yaml
trigger: "agent restarted gateway without permission"
rule: "never restart gateway without explicit 'proceed' from human"
learned: 2026-03-27
severity: critical
```

These are CI/CD for behavior. Every mistake becomes an automated guardrail.

### HEARTBEAT.md

A checklist the agent runs proactively on a schedule. Inbox triage, calendar checks, memory maintenance, system health. The agent's cron job manifest.

## Vectorization

All .md files should be vectorized for semantic search. The recommended chunk size is 512 tokens with 64-token overlap. The vector index should be rebuilt on a schedule (every 4 hours recommended).

## Version control

All IPAC files live in a git repository. Personality evolution is tracked the same way code evolution is tracked. Diffs show exactly what changed and when.
