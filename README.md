<div align="center">

# George Gallagher

### AI systems you can inspect, evaluate and control.

**Agent runtimes · evaluation & RL environments · trustworthy infrastructure · local inference**

<p>
  <a href="https://recensionresearch.co.uk"><img src="https://img.shields.io/badge/Recension%20Research-59D6A3?style=flat-square&labelColor=0A0D0F" alt="Recension Research"></a>
  <a href="mailto:george@recensionresearch.co.uk"><img src="https://img.shields.io/badge/email-george%40recensionresearch.co.uk-536c85?style=flat-square" alt="Email"></a>
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
| **[Endophasia](https://github.com/noctem-o/endophasia)** | Runtime-neutral experimental infrastructure for coding agents: trajectory capture and comparison, replay, capability studies, governed steering and controlled evaluation. | TypeScript · Bun · agent harnesses · evals |
| **[Magpie](https://github.com/noctem-o/magpie)** | Replayable epistemic memory with signed history, typed evidence, provenance and policy-defined conclusions. | Rust · SQLite · Ed25519 · deterministic replay |
| **[Deadbolt](https://github.com/noctem-o/deadbolt)** | Permission engine for AI-operated systems. Proposals remain untrusted until a typed route, policy, exact lease and confirmation authorize an effect. | Rust · capability security · MCP · rollback |
| **[Cogitator](https://github.com/noctem-o/cogitator)** | Recorder and verifier for agent runs, with canonical events, policy interception, replay, drift diagnosis and tamper-evident witness roots. | Rust · BLAKE3 · verification · release assurance |

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
| **Discriminating-task construction** | [72-trial screen + 20 fresh confirmation trials](https://github.com/noctem-o/endophasia/pull/34), selecting tasks that avoid saturated ~0% / ~100% success regimes for later candidate evaluation. |
| **Governed steering audit** | [Re-verified 364 recorded interventions](https://github.com/noctem-o/endophasia/pull/32) while hardening consumption semantics, STOP handling and authorization expiry. |

The useful outcome is not a prettier benchmark number. It is a better experimental instrument: one that can expose where sampling, environment, control flow and harness policy actually change an agent trajectory.

## Evaluation-driven adaptation

The next layer is **EVOLVE**: treating prompts, cognition policies, harness components, tools, memory, models, environments and inference budgets as explicit candidate changes.

```text
observe → propose → isolate → evaluate → compare → admit → promote
```

Current research directions include:

- RL environments and verifier-backed agent evaluation
- harness and policy search
- test-time compute allocation and stopping policies
- held-out checks and explicit promotion gates
- trajectory-preserving evidence for candidate comparison

RL is one possible adaptation mechanism. Training can produce a candidate; it does not decide what the evidence establishes, nor whether that candidate may replace anything.

## Engineering surface

**Languages:** Rust · TypeScript/Bun · Python · Bash/PowerShell  
**Agent/runtime:** Pi · MCP · ACP · OpenAI-compatible APIs · local agent harnesses  
**Inference:** llama.cpp · vLLM · SGLang · TensorRT-LLM · CUDA · GGUF · quantisation · long-context serving  
**Systems:** Linux · Nix/NixOS · systemd · containers/virtualisation · networking · low-level debugging  
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

[recensionresearch.co.uk](https://recensionresearch.co.uk) · [george@recensionresearch.co.uk](mailto:george@recensionresearch.co.uk)

</div>
