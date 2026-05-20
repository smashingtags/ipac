# Story Points: How They Evolved

**Author:** Michael Ashley
**Context:** 7+ years of Scrum (PSM, CSPO, SAFe), 12 teams at Neptune (Fortune 500), then solo with AI agents.

## How I used to do them (team setting)

Standard Fibonacci estimation with planning poker. The team sat in a room, discussed the work, played cards. Points measured relative complexity, not hours — that was the official line.

In practice, on every team I ever ran, points quietly mapped to hours. Everyone knew it. The PO knew it. The Scrum Master pretended otherwise during retrospectives. A 3-pointer was a day of work. A 5 was two days. An 8 was a week. A 13 meant the story needed to be broken down.

The value wasn't the precision of the estimate — it was the conversation. Planning poker forced the team to talk about what the work actually involved before anyone started coding. The engineer who played a 2 while everyone else played an 8 had to explain why. That conversation surfaced assumptions, dependencies, and risks that would have been invisible otherwise.

## How I did them solo (early days, August 2025)

When I started building HomelabARR solo after getting fired, I kept the process but dropped the pretense:

> **1 story point = 8 hours of head-down coding time.**

No relative sizing. No planning poker with myself. Just a direct mapping to effort. I documented it on day one in Confluence (page 1 of what became 238 pages).

| SP | Effort | Example |
|---|---|---|
| 1 | < 2 hours | Fix a typo, update a link |
| 2 | 2-4 hours | Add a component, fix a bug |
| 3 | 4-8 hours | New feature, refactor a section |
| 5 | 1-2 days | Multi-component feature, new page |
| 8 | 2-4 days | Major feature, architectural change |
| 13 | Break it down | Too big — split into smaller tasks |

This is still in the SDLC.md at `smashingtags/deploy-pipeline`. It works for solo human work because the only variable is my time and focus. There's no team calibration needed. A 3 is a day's work because I said so and I'm the only one doing it.

The sprint retros documented real velocity: Sprint 5 delivered 42 story points across 9 stories at 100% completion. That number meant something because the point definition was stable. I could look at a backlog and know roughly how many days it represented.

## How they work now (human + AI agents, May 2026)

The scale above still applies to human-led work — when I'm directing Claude Code through a multi-file change, the effort is still roughly measured in the hours I spend reviewing, testing, and iterating.

But for agent-dispatched work (tasks sent via Mission Control or Imogen), the model shifts:

**An agent session is a sprint.** A sprint is ~10 minutes. If a task can't be completed in one agent session, the task is too big. Don't extend the timeout — shrink the task.

That means:
- A **1-point** agent task is a single focused change: update a link, fix a type error, add an import.
- A **2-point** agent task is a component build or a bug fix that requires reading + modifying 1-2 files.
- A **3-point** agent task is the max for a single session: new page, refactor, multi-file change with verification.
- A **5-point** task gets decomposed into two or three 2-3 point agent sessions.
- An **8 or 13** never goes to a single agent. It gets broken into a series of sessions, each independently shippable.

The key shift: points no longer measure hours. They measure **sessions**. A 3-pointer is one agent session, not one day. The throughput is 100x faster, but the decomposition discipline is the same — arguably more important, because bad scope at 100x speed means you arrive at the wrong destination faster.

## What stayed the same

- Fibonacci scale (1, 2, 3, 5, 8, 13)
- 13 always means "break it down"
- The value is in the decomposition conversation, not the number
- Velocity tracking across sprints to spot trends
- Retrospectives after every sprint (even if the sprint is 10 minutes)

## What changed

- Points map to sessions, not hours
- A sprint is 10 minutes, not 2 weeks
- Scope creep is physically impossible (timebox kills it)
- No planning poker — I estimate alone and the estimate is a scope check, not a negotiation
- The PM role (decomposition) is more important than ever, not less

## The philosophy

The boring PM stuff — decomposition, acceptance criteria, definition of done — matters more with AI agents, not less. The model can execute at any speed you want. The question is whether you pointed it at the right thing. Story points are a forcing function for that conversation, even when the only person in the room is you.

See also: [[session-equals-sprint]]
