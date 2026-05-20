# Story Points: How They Evolved

**Author:** Michael Ashley
**Context:** 7+ years of Scrum (PSM, CSPO, SAFe), 12 teams at Neptune (Fortune 500), then solo with AI agents.
**Source:** Confluence space DO, board 34 (`architecture-deep-dive.md`, Story Point Scale section)

## How I used to do them (team setting)

Standard Fibonacci estimation with planning poker. The team sat in a room, discussed the work, played cards. Points measured relative complexity. That was the official line.

In practice, on every team I ever ran, points quietly mapped to hours. Everyone knew it. The PO knew it. The Scrum Master pretended otherwise during retrospectives. A 3-pointer was a day of work. A 5 was two days. An 8 was a week. A 13 meant the story needed to be broken down.

The value was never the precision of the estimate. It was the conversation. Planning poker forced the team to talk about what the work actually involved before anyone started coding. The engineer who played a 2 while everyone else played an 8 had to explain why. That conversation surfaced assumptions, dependencies, and risks that would have stayed invisible otherwise.

## How I do them solo (the real scale)

When I started building solo, I dropped the pretense and made the mapping explicit. One story point equals eight hours of head-down time. Not relative sizing. Not planning poker with myself. Direct mapping to effort.

The scale is linear, not Fibonacci:

| Points | Hours | Typical Work |
|---|---|---|
| 0.25 | 2h | Minor config changes |
| 0.5 | 4h | Simple updates |
| 1.0 | 8h | Standard container setup |
| 2.0 | 16h | Complex integration |
| 3.0 | 24h | Multi-service feature |
| 5.0 | 40h | Major feature |
| 8.0 | 64h | Infrastructure change |

This is documented in the Confluence architecture deep-dive (space DO, board 34) and in SDLC.md at `smashingtags/deploy-pipeline`.

The sprint retros documented real velocity against this scale. Sprint 5 delivered 42 story points across 9 stories at 100% completion. That number meant something because the point definition was stable. 42 points was roughly 336 hours of equivalent work. I could look at a backlog and know how many days it represented.

## How they work now (human + AI agents, 2026)

The scale above still applies to human-led work. When I'm directing Claude Code through a multi-file change, the effort is still roughly measured in the hours I spend reviewing, testing, and iterating.

For agent-dispatched work, tasks sent via Mission Control or Imogen, the model shifts. An agent session is a sprint. A sprint is about 10 minutes. If a task can't be completed in one agent session, the task is too big.

The point scale maps to sessions, not hours:

- **0.25** is a trivial change. One file, one line.
- **0.5** is a single focused change. Update a link, fix a type error, add an import.
- **1.0** is a standard agent task. Component build, bug fix, touching one or two files.
- **2.0** is a substantial single session. New page, refactor, multi-file change with verification.
- **3.0** is the max for a single session. Decompose anything bigger.
- **5.0 and up** must be broken into multiple sessions. Each one independently shippable.

The throughput is 100x faster but the decomposition discipline is the same. Arguably more important, because bad scope at 100x speed just means you arrive at the wrong destination faster.

## What stayed the same

- The scale: 0.25, 0.5, 1, 2, 3, 5, 8
- An 8 always means "this is an infrastructure-level change"
- The real value is in the decomposition conversation, not the number itself
- Velocity tracking across sprints to spot trends
- Retrospectives after every sprint

## What changed

- Points map to sessions for agent work, or hours for human work, depending on who's doing it
- A sprint is 10 minutes for agents, not 2 weeks
- Scope creep is physically impossible with the agent timebox
- No planning poker. I estimate alone and the estimate is a scope check, not a negotiation.
- The PM role, especially decomposition, is more important than ever. Not less.

See also: [[session-equals-sprint]]
