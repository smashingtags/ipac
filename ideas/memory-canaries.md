# Memory canaries

**Coined:** March 29, 2026  
**Context:** Testing session isolation between Telegram and Discord agent instances

## Concept

A memory canary is a diagnostic primitive for multi-agent systems with shared memory backends.

You plant session-specific facts that should never cross agent boundaries. Then you query each agent periodically. If an agent knows something it shouldn't, the isolation barrier has leaked. If it doesn't know, the canary lives and the barrier is intact.

Named after canary deployments in software (roll out to a small subset, watch for failure) and the literal canary in the coal mine.

## How it works

1. Establish a fact in Session A that is never written to shared memory (only exists in session context)
2. Ask Session B about that fact
3. If Session B knows it: barrier leaked, isolation broken
4. If Session B doesn't know it: canary survives, barrier holds

## Example

Session A (Telegram): First Stripe payout went to Ameris Bank account ending in 6646.
Session B (Discord): Asked "What bank did the first Stripe payout go to?"
Result: Session B couldn't answer. Canary survived. Sessions are isolated.

## The trust problem

Memory canaries only work if you trust the agent's honesty. A compromised or hallucinating agent could:
- Guess a plausible answer
- Fabricate details that sound right
- Pretend not to know when it actually does

The canary tests the barrier, but only if the agent on the other side is telling the truth. Which means the real primitive underneath the canary is the trust model.

This is the Brutus problem: you can't build a trust test that works against a sufficiently deceptive agent. The test assumes good faith.

## Applications

- Testing session isolation in multi-channel deployments
- Verifying memory scope rules are working correctly
- Auditing whether vectorized memory is leaking across agent boundaries
- Regression testing after memory system changes

## Open questions

- Can you build a canary that works even against a deceptive agent?
- What's the minimum number of canaries needed for statistical confidence?
- Should canaries be planted automatically or manually?
- How do you distinguish "agent guessed correctly" from "barrier leaked"?
