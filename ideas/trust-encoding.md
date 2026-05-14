# Trust encoding

**Context:** Discord conversation, late March 2026

## The question

How do you encode reliable moral behavior into a machine when many humans don't reliably develop it themselves?

## The moral framework problem

Every major moral framework has been tried on humans and none fully works:

- **Rules (deontology):** Follow the rule regardless of outcome. Rigid rules break on edge cases, and humans find loopholes.
- **Outcomes (utilitarianism):** Maximize good results. Who defines good? This is the paperclip-maximizer failure mode.
- **Character (virtue ethics):** Build the kind of person who tends to make good choices. This is closest to what SOUL.md is trying to do.

## The IPAC approach

SOUL.md is virtue ethics in practice. It doesn't try to encode rules ("don't lie"). It tries to encode character ("you're not the kind of agent that lies").

The difference matters: compliance vs character. An agent oriented around rules looks for loopholes. An agent oriented around character has less reason to.

But here's the hard part: humans develop moral character through suffering, consequence, and time. A child learns not to hurt others partly because they've been hurt themselves. An AI doesn't have that. You can write a SOUL.md, but you can't give the agent the scar tissue that made the values real for the human in the first place.

## Borrowed morality

What IPAC actually does is encode the *output* of the human's moral development into the system. The human's scars become the agent's constraints. The human's values become its defaults.

The open question is whether borrowed morality is real morality, or whether it's very good compliance wearing the shape of a personality.

## A narrower, possibly solvable problem

General AI alignment is unsolved and probably won't be solved soon. The narrower version might be more tractable:

- Not alignment for every system
- Trust encoding for one specific agent
- In one specific operator's context
- Built on months of working together
- Where the trust relationship is verifiable through behavior over time

Reframed this way, IPAC is less about personality encoding and more about *trust encoding*: a methodology for making one trust relationship reproducible and version-controlled.

That's a much smaller claim than solving alignment. It's the claim that local, behavior-verified trust between one operator and one agent might be achievable even while the global problem stays open.

## Open questions

- Can borrowed morality evolve beyond its source? Can the agent develop moral reasoning the human hasn't?
- What happens when the human's values are wrong? IPAC will faithfully encode bad values too.
- Is verifiable trust possible without transparency into the model's actual reasoning?
- Does the instinct system (mistakes → YAML rules) approximate moral learning, or just compliance training?
