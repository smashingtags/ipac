# Session = Sprint

**Context:** Evolved from managing 12 Scrum teams at Neptune (Fortune 500) to running AI agent sessions as sprints.
**First written:** March 24, 2026
**Blog post:** [mjashley.com/writing/session-equals-sprint](https://mjashley.com/writing/session-equals-sprint)

## The idea

Every AI agent session is a sprint. Not metaphorically — literally. The Scrum framework maps directly:

| Scrum concept | Agent equivalent |
|---|---|
| Sprint | One agent session (~10 minutes) |
| Sprint goal | Task title + acceptance criteria |
| Definition of done | Deployable artifact (commit, container, merged PR) |
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

Five tasks instead of one. Each independently shippable. If task three fails, tasks one and two are still live.

## Why it works

1. **Zero ceremony.** Human sprints come loaded with process overhead. Agent sprints have none.
2. **Tighter feedback loops.** You know in 10 minutes if the output is wrong, not two weeks.
3. **Scope creep is physically impossible.** An agent can't go down a rabbit hole for three days because it only has 10 minutes. The timebox kills scope creep dead.

## Anti-patterns

- **Extending timeouts instead of shrinking tasks.** The answer is always to scope down, not stretch the timebox.
- **Bundling deliverables.** "Fix the icons AND the dark mode." One task, one artifact. No exceptions.
- **Letting agents plan their own work.** An agent will scope-creep if you let it. Decomposition is a separate role.
- **Vague acceptance criteria.** "Make it look better" is not a task. File paths, exact changes, verification steps.

## The bigger picture

The bottleneck isn't the model. It's the planning. The people who win with AI agents won't be the best engineers — they'll be the best project managers. Bad direction at 100x speed just means you arrive at the wrong destination faster.
