<div align="center">

# George Gallagher

### AI systems you can inspect, evaluate, adapt and control.

**Agent runtimes · evaluation & adaptation · trustworthy infrastructure · local inference**

<p>
  <a href="https://recensionresearch.co.uk"><img src="https://img.shields.io/badge/Recension%20Research-59D6A3?style=flat-square&labelColor=0A0D0F" alt="Recension Research"></a>
  <img src="https://img.shields.io/badge/Greater%20Manchester-UK-637d69?style=flat-square" alt="Greater Manchester, UK">
</p>

**Founder + engineer at [Recension Research](https://recensionresearch.co.uk)**

[Endophasia](https://github.com/noctem-o/endophasia) · [Magpie](https://github.com/noctem-o/magpie) · [Deadbolt](https://github.com/noctem-o/deadbolt) · [Cogitator](https://github.com/noctem-o/cogitator)

</div>

---

I build experimental infrastructure for AI agents and AI-operated systems: ways to observe runtime behaviour, evaluate it reproducibly, preserve evidence, keep authority outside the model, and verify what happened afterwards.

The recurring question is simple:

> **How do increasingly capable agent systems remain inspectable, evidential and governable without pretending one mechanism solves everything?**

My work keeps five jobs separate:

```text
observe  →  evidence  →  policy  →  permission  →  verify
runtime     support      standing    authority      recompute
```

## Current work

| Project | What it does | Surface |
| :--- | :--- | :--- |
| **[Endophasia](https://github.com/noctem-o/endophasia)** | Runtime-neutral experimental substrate for coding agents: trajectory capture and comparison, replay, capability studies, governed steering, cross-runtime adapters and controlled evaluation. | TypeScript · Node.js · agent harnesses · evals |
| **[Magpie](https://github.com/noctem-o/magpie)** | Replayable epistemic memory with signed history, typed evidence, provenance, policy-defined standing and detached standing receipts. | Rust · SQLite · Ed25519 · portable verification |
| **[Deadbolt](https://github.com/noctem-o/deadbolt)** | Permission engine for AI-operated systems. Proposals remain untrusted until a typed route, policy, exact lease and confirmation authorize an effect. | Rust · capability security · MCP · rollback |
| **[Cogitator](https://github.com/noctem-o/cogitator)** | Tamper-evident recorder and verifier for agent runs, with canonical witness events, pre-dispatch policy interception, deterministic replay, drift detection and recomputable BLAKE3 witness roots. | Rust · BLAKE3 · verification · release assurance |

Each project stands alone. Together they explore a division of responsibility:

```text
agent runtime
     │
     ▼
Endophasia
observe · steer · compare
     │
     ├──── Magpie
     │     evidence · provenance · standing
     │
     └──── Deadbolt
           permission · effects · receipts

Cogitator
reproducible run verification
```

This is a **division of responsibility, not a dependency graph**. Observation is not authority, and a successful evaluation is not permission to replace a running system.

## Recent empirical work

Endophasia has moved from architecture into repeated live agent studies. The current research separates three different claims:

```text
exact replay               did the recorded session reproduce under recorded responses?
fixed-condition repeat     do repeated live runs under the same declared conditions agree?
perturbation invariance    does behaviour hold when an input that should not matter changes?
```

| Study | Evidence |
| :--- | :--- |
| **Pinned-environment repeatability** | [240 live trials](https://github.com/noctem-o/endophasia/pull/26) under a controlled Pi + local-model configuration, with every manipulation check passing. |
| **Path sensitivity** | [360 trials across 30 working-directory paths](https://github.com/noctem-o/endophasia/pull/31), exposing task-dependent behavioural sensitivity to a nominally irrelevant perturbation. |
| **Discriminating-task construction** | [72-trial screen + 60 fresh confirmation trials](https://github.com/noctem-o/endophasia/pull/34), selecting tasks that avoid saturated ~0% / ~100% success regimes for later candidate evaluation. |
| **Completion-cap / test-time compute** | [192-trial main study + 40-trial pilot](https://github.com/noctem-o/endophasia/pull/35): raising the completion cap improved pooled success on the two discriminating tasks from 10/24 to 19/23, while also exposing why evaluation workspaces need stronger isolation. |
| **Governed steering audit** | [Re-verified 364 recorded interventions](https://github.com/noctem-o/endophasia/pull/32) while hardening consumption semantics, STOP handling and authorization expiry. |

The useful outcome is not a prettier benchmark number. It is a better experimental instrument: one that can expose where sampling, environment, control flow and harness policy actually change an agent trajectory.

The runtime surface now extends beyond one harness: the merged [ACP v1 vertical slice](https://github.com/noctem-o/endophasia/pull/37) exercised a real OMP session through the standard protocol, while the separate [ACP v2 conformance study](https://github.com/noctem-o/endophasia/pull/47) pins a Draft v2 baseline, tests negotiation, replay and permission semantics against deterministic agents, and deliberately admits no v2 capability merely from protocol compatibility. That v2 study is complete and parked pending upstream stabilisation rather than chased as a moving draft.

## Operator Alpha and evaluation-driven adaptation

The immediate Endophasia milestone is **Operator Alpha**: make the existing instrument something a person can install and run through a distributable, versioned `endo` CLI before broadening the research surface.

Beyond that operator layer, **EVOLVE** treats prompts, cognition policies, harness components, tools, memory, models, environments and inference budgets as explicit candidate changes.

```text
observe → propose → isolate → evaluate → compare → admit → promote
```

Current research directions include:

- pluggable evaluation, environment, adaptation and optional training providers
- harness and policy search
- test-time compute allocation and stopping policies
- held-out checks and explicit promotion gates
- trajectory-preserving evidence for candidate comparison

RL is one possible adaptation mechanism. Training can produce a candidate; it does not decide what the evidence establishes, nor whether that candidate may replace anything.


## Longer-horizon alignment research

Beyond the current Endophasia build, I am starting to frame a separate line of research around whether alignment-relevant epistemic behaviour can be studied as a **developmental property** rather than only as a post-training correction.

The current design keeps the claim narrow: separate **epistemic-content effects** from **timing effects**, use synthetic microworlds with exact gold outcomes, keep Magpie as a shadow evidence / provenance / standing surface rather than a truth oracle, and treat null or reversed results as first-class outcomes.

A second question is measurement: whether developmental state can be described more precisely than training step alone. [*What Do Language Models Learn and When? The Implicit Curriculum Hypothesis*](https://arxiv.org/abs/2604.08510) and its open [ElementalTask](https://github.com/KaiserWhoLearns/ElementalTask) tooling provide useful emergence-order and trajectory baselines. I treat those as instrumentation, not as evidence that an early epistemic curriculum is causally better.

[Developmental epistemic training v0](https://github.com/noctem-o/endophasia/blob/main/research/developmental-epistemic-training-v0.md) is the substrate-side research contract and preregistration draft. [developmental-epistemics](https://github.com/noctem-o/developmental-epistemics) is the MIT-licensed, concept-only longer-horizon repository.

## Engineering surface

**Languages:** Rust · TypeScript/Node.js · Python · Bash/PowerShell  
**Agent/runtime:** Pi · MCP · ACP · OpenAI-compatible APIs · local agent harnesses  
**Inference:** llama.cpp · vLLM · SGLang · TensorRT-LLM · CUDA · GGUF · quantisation · long-context serving  
**Systems:** Linux · Arch · Nix · systemd · containers/virtualisation · networking · low-level debugging  
**Delivery:** GitHub Actions · reproducible environments · conformance testing · golden fixtures · cargo-dist · release verification

I use frontier and local models as a structured engineering workforce: architecture-first decomposition, bounded implementation briefs, maker/checker separation, adversarial review and human-controlled promotion.

## Working principles

```text
observation  != inference
evidence     != standing
proposal     != permission
evaluation   != promotion
simulation   != real execution
```

These projects are experimental research software. I try to keep claims narrow, make failure states visible, test hostile cases, and document what each system does **not** establish.

---

<div align="center">

**Make capability legible before making it larger.**

[recensionresearch.co.uk](https://recensionresearch.co.uk)

</div>
