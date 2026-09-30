<div align="center">

# George Gallagher

**Local-first systems for inspectable and governable AI agents.**

I build experimental infrastructure for observing agent computation, preserving evidence, separating proposals from permission, and testing how agent systems can adapt without hiding what changed.

[Endophasia](https://github.com/noctem-o/endophasia) · [Magpie](https://github.com/noctem-o/magpie) · [Deadbolt](https://github.com/noctem-o/deadbolt) · [Cogitator](https://github.com/noctem-o/cogitator)

</div>

---

I am interested in systems where a user can inspect what the runtime observed, how a conclusion was produced, what changed between candidate versions, and who authorised an action.

My projects explore those questions through small, testable components with explicit boundaries between runtime state, evidence, and authority.

## Selected projects

| Project | Focus |
| :--- | :--- |
| **[Endophasia](https://github.com/noctem-o/endophasia)** | Instrumented cognition for coding agents. It observes and steers agent runtimes through explicit semantic contracts. Its developing EVOLVE mode is intended for controlled experiments over agent policies, environments, runtimes, and models. |
| **[Magpie](https://github.com/noctem-o/magpie)** | A replayable memory kernel for AI systems. Signed history, typed evidence, provenance, and policy-defined conclusions. |
| **[Deadbolt](https://github.com/noctem-o/deadbolt)** | A permission engine for AI-operated systems. Models can propose actions, while authority, review, execution, and receipts remain explicit. |
| **[Cogitator](https://github.com/noctem-o/cogitator)** | A Rust recorder and verifier for agent runs, with tamper-evident records and reproducible verification. |

## Current direction

Endophasia is becoming the integration point for the wider work.

```text
agent runtime
     |
     v
Endophasia
observe, steer, compare
     |
     +--> Magpie
     |    evidence, provenance, standing
     |
     +--> Deadbolt
          permission, effects, receipts

Cogitator
reproducible run verification
```

DEVELOP covers the current agent session. EVOLVE is being designed for repeated candidate experiments with pinned environments, evaluators, costs, held-out checks, and explicit promotion steps.

I am also exploring optional agent RL and recursive self-improvement research around that EVOLVE path. The useful parts, for me, are controlled candidate generation, evaluation, selection, rollback, and evidence retention. Projects such as [Reef](https://github.com/Human-Agent-Society/reef) and [RRSI](https://github.com/google-research/rrsi) are useful references because they make those stages inspectable rather than treating a higher benchmark score as sufficient reason to keep a change.

The same separation applies if model weights are trained later. Training can produce a candidate. It does not decide what the evidence establishes or whether that candidate may replace anything.

## Working principles

```text
observation  != inference
evidence     != standing
proposal     != permission
evaluation   != promotion
simulation   != real execution
```

These projects are experimental research software. I try to keep claims narrow, make failure states visible, test hostile cases, and document what each system does not establish.
