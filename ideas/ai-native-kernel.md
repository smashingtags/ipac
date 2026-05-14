# AI-native kernel / OS concept

**Context:** Discord conversation, March 2026  
**Status:** Speculative — longer-horizon idea, captured here for discussion

## The concept

What if you baked AI directly into the operating system kernel, instead of running it as an application on top of one? The harness *is* the OS. Syscalls become inference calls. Self-healing happens at ring zero.

Not "AI app running on Linux" — AI as the kernel itself.

## Why it might matter

**Current shape:** App → OS → Kernel → Hardware. AI sits at the app layer and asks permission for everything through multiple abstraction layers.

**Proposed shape:** AI is the kernel. Direct hardware access, self-healing, intent-based syscalls where the OS infers what you need rather than executing literal instructions.

## The hard problem

AI hallucination at the kernel level is corrupted memory pages. A wrong inference at ring zero doesn't crash an app — it can corrupt the whole system.

That implies guardrails need to live in silicon, not in software. A software guardrail can't be trusted when the thing it's guarding against has root access to the hardware the guardrail runs on.

## One possible path

If someone wanted to prototype this, a plausible sequence:

1. RISC-V soft core on FPGA (~$50–200 dev board)
2. Custom AI acceleration instructions in the ISA
3. Prove the concept on FPGA
4. Tape out via a shuttle service (e.g. Efabless/ChipIgnite on Skywater 130nm PDK, roughly $10K)
5. Custom silicon with AI instructions native to the chip

Toolchain that fits this path: Verilator, Chisel/Amaranth HDL, Cocotb, OpenROAD, Skywater 130nm PDK.

## A shorter-term version

A much cheaper experiment is the "AI box" shape: off-the-shelf board (RPi5 / Jetson / Orange Pi 5) + custom Linux kernel + AI OS layer + local model + 3D-printed enclosure = a dedicated AI hardware device.

Not custom silicon, but custom OS on commodity hardware. Proves out the *interaction model* without the tape-out cost.

## Hardware worth looking at

- Sipeed NanoKVM (SG2002 RISC-V C906 1GHz, 256MB RAM, open source)
- Off-the-shelf FPGA dev boards as programmers
- A decent FDM 3D printer for enclosures

## Adjacent / prior work

- RISC-V AI extensions (various proposals)
- Google TPU (custom silicon for AI, but cloud-only)
- Apple Neural Engine (on-chip AI accelerator, not AI-native OS)
- Various "AI hardware" startups exploring dedicated devices

## Open questions

- What's the smallest interesting prototype? FPGA softcore? Modified Linux kernel?
- Where exactly does "intent-based syscall" stop being a syscall and start being a policy engine?
- What's the right place to draw the silicon-vs-software guardrail line?
- Is there a way to bound the blast radius of a wrong inference without giving up the upside?
