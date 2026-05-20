# Session = Sprint

**Context:** Evolved from managing 12 Scrum teams at Neptune (Fortune 500) to running AI agent sessions as sprints.
**First written:** March 24, 2026
**Blog post:** [mjashley.com/writing/session-equals-sprint](https://mjashley.com/writing/session-equals-sprint)

## The idea

Every AI agent session is a sprint. Not metaphorically. Literally. The Scrum framework maps directly:

| Scrum concept | Agent equivalent |
|---|---|
| Sprint | One agent session (about 10 minutes) |
| Sprint goal | Task title + acceptance criteria |
| Definition of done | Deployable artifact: a commit, a container, a merged PR |
| Sprint review | Checking the dev URL after the agent finishes |
| Sprint retro | Updating agent instructions when they underperform |
| Product backlog | Issue board / Mission Control |
| Sprint planning | PM decomposing big requests into atomic pieces |
| Velocity | Tasks completed per session |

## The 10-minute rule

If a task can't be completed in a single agent session, the task is too big. Don't extend the timeout. Shrink the task.

Bad decomposition:
- "Fix all broken app icons" (one task, 45+ minutes of work)

Good decomposition:
- Audit all 157 apps, list which ones have missing icons (delivers an audit file)
- Add icon mappings for apps A through M (delivers a commit)
- Add icon mappings for apps N through Z (delivers a commit)
- Fix the YAML template variable (delivers a commit)
- Final deploy to dev (delivers a running container)

Five tasks instead of one. Each one independently shippable. If task three fails, tasks one and two are still live.

## Why it works

**Zero ceremony.** Human sprints come loaded with process overhead. Agent sprints have none. Pick up, execute, ship, next.

**Tighter feedback loops.** You know in 10 minutes if the output is wrong. Not two weeks. If it's off, adjust and re-run. The iteration cycle is a hundred times faster.

**Scope creep is physically impossible.** An agent can't go down a rabbit hole for three days because it only has 10 minutes. The timebox kills scope creep dead. There's no "well, while I'm in here let me also refactor this." Either the task fits the window or it doesn't.

## Anti-patterns

**Extending timeouts instead of shrinking tasks.** When the agent times out, the gut reaction is to give it more time. That's like making a sprint three weeks instead of two because the team couldn't finish. The answer is always to scope down, not stretch the timebox.

**Bundling deliverables.** "Fix the icons AND the dark mode." That's two tasks. Every time I've combined them, one gets done well and the other gets done halfway. One task, one artifact. No exceptions.

**Letting agents plan their own work.** This applies to human teams and agent teams equally. An engineer, human or AI, will scope-creep if you let them. Decomposition is its own skill. It should be a separate role.

**Vague acceptance criteria.** "Make it look better" is not a task. "Replace the placeholder with the real app logo from the homelabarr-logos repository, rebuild the container, deploy to ce-dev on port 8085." That's a task. Be specific or get surprised.

## The bigger picture

The bottleneck isn't the model. It's the planning. The people who win with AI agents won't be the best engineers. They'll be the best project managers.

The models are good enough. They can write code, build UIs, draft content, run deployments. What's missing is the layer between "I want this" and "here's exactly what to build, in what order, with what acceptance criteria, and here's how I'll know it's done."

That layer is sprint planning. That's decomposition. That's all the boring PM stuff that engineers have always wanted to skip. And it turns out it matters more when your team never sleeps and works at 100x speed. Bad direction at 100x speed just means you arrive at the wrong destination faster.
