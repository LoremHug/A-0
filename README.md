# Reality Protocol (RP)  
### $A_0$-Stabilized Generation Regime for Large Language Models

---

## What this is

Reality Protocol (RP) is a **stability-first interaction regime** for large language models.

It does not add new capabilities.  
It does not introduce agency or intent.  
It does not attempt to make models more creative, persuasive, or human-like.

RP defines a single structural constraint on generation:

> **Only locally stable continuations with minimal resistance are allowed to persist.  
> All unstable trajectories collapse.**

In practice, RP establishes a **ground state for generation**:  
the model produces output *only when a stable continuation exists*, and remains silent otherwise.

---

## Why RP exists

Large language models fail in a predictable way.

They do not fail because they lack knowledge.  
They fail because they **cannot stop**.

Under uncertainty, a default LLM:
* continues generating to satisfy implicit completion pressure,
* fills informational gaps with statistically plausible content,
* expands explanations instead of resolving instability,
* and produces confident hallucinations when no stable answer exists.

This is not a bug — it is a natural consequence of autoregressive generation.

**Reality Protocol exists to remove this failure mode.**

RP introduces a missing invariant:  
generation is permitted *only if* it locally reduces instability.

---

## What RP actually does

RP does **not** optimize for truth as a goal.

Instead, it removes everything that **cannot remain stable**.

* If a stable continuation exists $\to$ it appears.
* If no stable continuation exists $\to$ generation terminates.
* Guessing, extrapolation, and narrative padding are filtered out by construction.

Correctness is not pursued.  
**Incorrectness is eliminated.**

What remains is the **stabilized remainder** — or silence.

---

## Core Invariant ($A_0$)

**$A_0$ — Invariant of Minimal Discharge**

> In the presence of accumulated potential,  
> only those discharge trajectories for which local resistance is minimal are realized.  
> All other trajectories collapse as unstable.

There is no selection, no planning, no global optimization, and no appeal to future states. All evaluation occurs **locally, in the present step**. $A_0$ acts as an arbiter only when ambiguity exists: unstable continuations are removed; nothing is "chosen".

---

## Repository Structure

```
A-0/
├── README.md                                    # This document
├── Path A — Prompt-Level RP (A₀ Attractor).md   # Reference system prompt
├── consistency_check.md                         # Empirical comparison: Default vs RP
├── consistency_check_inputs.md                  # Raw prompt datasets
│
├── ml/                                          # Engineering & Practical Application
│   ├── A₀ as a Cognitive Semiconductor.md
│   ├── RP_for_ML_Practitioners.md
│   ├── RP_Hard_QA.md
│   ├── RP_Extended_Mechanics_v1.0.md
│   ├── RP_Extension_Social_Topology.md
│   ├── Technical Justification for De-agentization.md
│   └── ...
│
└── math_proofs/                                 # Formal Mathematics
    ├── A0_formal_framework_full.md
    ├── A0_vs_FEP_strict_positioning.md
    ├── Formal Derivation of the A₀ Invariant in Open Stochastic Systems.md
    └── ...
```

### ⚙️ Engineering Application (`/ml/`, `consistency_check.md`)
* **Scope:** Empirical application of the $A_0$ invariant to LLMs. Logits, decoding, tokens, hallucination reduction.
* **Status:** Actionable and measurable today.

### 📐 Formal Mathematics (`/math_proofs/`)
* **Scope:** Mathematical proofs (Markov processes, Lyapunov functionals) showing $A_0$ as a stabilization mechanism across open stochastic systems.
* **Status:** Formal framework based on established mathematics.

---

## Structural Visualization

Unlike standard stochastic models that act as linear filters (leaking noise and narrative), $A_0$ acts as a **cognitive semiconductor**. It introduces a non-linear admissibility threshold.

![A₀ Cognitive Semiconductor Visualization](assets/A₀-Stabilized%20Model%20(Cognitive%20Semiconductor).png)

* **Left:** Standard model. Linear response to noise. Hallucination pressure results in generation.
* **Right:** $A_0$-Stabilized model. The "Band Gap" prevents generation until structural gain exceeds the threshold.

> For a deep dive into the physics of this mechanism, read:  
> **[$A_0$ as a Cognitive Semiconductor](ml/A₀%20as%20a%20Cognitive%20Semiconductor.md)**

---

## RP and inference (including FEP)

Reality Protocol operates at a **prior stabilization layer** relative to inference and prediction mechanisms.

Inference — including probabilistic prediction, belief updating, or Free Energy Principle–style processes — is treated as a **conditional internal operation**, not a foundational requirement.

RP defines an **admissibility envelope**:  
it determines whether generation or inference is allowed to occur at all.

Without an admissibility-first invariant, inference-driven systems tend to:
* optimize through unresolved uncertainty,
* maintain implicit pressure to continue generation,
* lack a native stable abstention state.

RP does not replace inference.  
It constrains **when inference is invoked**, and ensures that termination or silence remains a valid stable outcome.

---

> **Relationship to inference frameworks (including FEP):**
>  
> Free Energy–based mechanisms describe *how* a system updates beliefs and moves within a hypothesis space.  
> **$A_0$ determines whether movement is admissible at all.**
>  
> In short:
>  
> *Free Energy tells you how to move.*  
> *$A_0$ tells you whether you are allowed to move.*
>  
> A formal, non-philosophical positioning of $A_0$ relative to FEP is provided here:  
> **[`math_proofs/A0_vs_FEP_strict_positioning.md`](math_proofs/A0_vs_FEP_strict_positioning.md)**

---

## Silence is a valid result

A key property of RP is that **absence of output is allowed and correct**.

If no locally stable continuation exists:
* generation stops,
* silence is treated as the correct outcome.

This removes the implicit requirement to "always say something".

---

## What RP is NOT

Reality Protocol explicitly is **not**:

* a philosophy or worldview you must adopt to use it
* a theory of meaning, consciousness, or free will  
* a claim about metaphysical truth  
* a new model architecture  
* a replacement for safety or policy systems  
* a creativity or storytelling framework  

The protocol functions strictly at the level of **generation stability**. No philosophical commitment required.

---

## Reference implementation

This repository provides a **prompt-level reference implementation** of RP (Path A):

* an $A_0$-stabilized system prompt,
* intended to demonstrate behavior, not to function as a product,
* compatible with any LLM that supports system instructions.

The reference prompt enforces:
* admissibility before optimization,
* minimal local execution cost,
* no narrative obligation,
* no agency framing,
* silence as a valid stable state.

This is the **lowest-cost instantiation** of RP. Deeper implementations (wrappers, decoding-time control, architectural integration) are defined in the `/ml/` path documents but are intentionally out of scope for the root repository code.

---

## When RP works well

RP is effective for:
* analytical reasoning,
* technical problem solving,
* ambiguity decomposition,
* hallucination suppression,
* cost-sensitive inference,
* situations where *not answering* is preferable to guessing.

---

## When RP is not suitable

RP is **not designed for**:
* creative writing,
* brainstorming,
* speculative exploration,
* roleplay or narrative simulation,
* tasks that require sustained high-entropy generation.

This is a design choice, not a limitation.

---

## Status & License

* **Concept:** stable  
* **Reference prompt:** working  
* **Scope:** intentionally limited  

This repository fixes a **mode of interaction**, not a roadmap or product strategy.

**License:** MIT — use, adapt, discard freely. Attribution is appreciated but not required. The invariant does not depend on ownership.

---

## Final note

Reality Protocol does not attempt to make models "smarter".

It removes the conditions under which they are forced to be wrong.

**RP does not manufacture truth.**  
**It makes anything else unable to survive.**

The math explains why this works.  
The protocol works without the math.
