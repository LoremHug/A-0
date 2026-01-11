# Reality Protocol (RP)
### A₀-Stabilized Generation Regime for Large Language Models

---

## What this is

Reality Protocol (RP) is a **stabilized interaction regime** for large language models.

It does not add capabilities.
It does not introduce agency.
It does not optimize for creativity, persuasion, or completeness.

RP describes a way to **remove instability from model interaction** by enforcing a single invariant:

> **Only locally stable continuations with minimal resistance are allowed to persist.  
> All other trajectories collapse.**

In practice, RP functions as a *relaxed ground state* for generation.

---

## How RP emerged

RP was not designed top-down.

It emerged through **long-form calibration of interaction** with an LLM:
- removing narrative pressure,
- removing implicit obligation to answer,
- removing intent and agency framing,
- allowing silence as a valid outcome.

Once the interaction stabilized into a consistent regime,  
that regime was **explicitly fixed as a prompt-level reference**.

This repository documents that stabilized regime.

---

## Core Invariant (A₀)

**A₀ — Invariant of Minimal Discharge**

> In the presence of accumulated potential,  
> only those discharge trajectories for which local resistance is minimal are realized.  
> All other trajectories collapse as unstable.

There is:
- no selection,
- no planning,
- no optimization toward global goals.

What remains is the **stabilized remainder** — or silence.

---

### RP and Inference (Including FEP)

Reality Protocol operates at a prior stabilization layer relative to inference and prediction mechanisms.

RP defines a stability and admissibility envelope that determines whether generation or inference is allowed to occur at all.
Inference — including probabilistic prediction, belief updating, or Free Energy Principle–style mechanisms — is treated as a conditional internal operation, not a foundational requirement.

Without an admissibility-first invariant, inference-driven systems tend to:
- optimize through unresolved uncertainty,
- maintain implicit pressure to continue generation,
- lack a native stable abstention state.

RP does not replace inference.
It constrains when inference is invoked and ensures that silence or termination remains a valid stable outcome when no admissible continuation exists.

In this sense, RP provides the missing invariant layer required for inference-based systems to remain stable under open-world conditions.

---

## What RP is NOT

To avoid misinterpretation, RP explicitly is **not**:

- a philosophy or worldview  
- a theory of meaning, consciousness, or agency  
- a claim about truth or correctness  
- a new model architecture  
- a replacement for safety policies  
- a creativity framework  

Any interpretation in those directions is a category error.

RP operates strictly at the level of **generation stability**.

---

## Reference Implementation

This repository includes a **prompt-level reference implementation**:

- an A₀-stabilized system prompt
- intended to demonstrate behavior, not to act as a product
- usable with any LLM that supports system instructions

The prompt enforces:
- admissibility before optimization
- minimal local execution cost
- no narrative obligation
- no agency framing
- silence as a valid stable state

This is the **lowest-cost instantiation** of RP.

Deeper implementations (wrappers, decoding-time control, architectural changes) are explicitly **out of scope** here.

---

## When RP works well

RP is effective for:
- analytical reasoning
- technical problem solving
- ambiguity decomposition
- hallucination suppression
- cost-sensitive inference
- situations where *not answering* is preferable to guessing

---

## When RP is not suitable

RP is **not appropriate** for:
- creative writing
- brainstorming
- speculative exploration
- roleplay or narrative simulation
- tasks that require high entropy generation

This is a design choice, not a limitation.

---

## Silence as a valid outcome

A key property of RP is that **absence of output is allowed**.

If no locally stable continuation exists:
- generation terminates
- silence is treated as a correct result

This removes the implicit pressure to “always say something”.

---

## Intended audience

This repository is for people who:
- think in terms of invariants rather than heuristics
- are comfortable with local stability instead of global optimality
- are interested in reducing system-level noise rather than adding features

If this framing feels unintuitive or unnecessary,  
RP is probably not meant for you — and that is fine.

---

## Status

- Concept: stable
- Reference prompt: working
- Scope: intentionally limited
This repository fixes a **mode of interaction**, not a roadmap.

---

## License

MIT — use, adapt, discard freely.

Attribution is appreciated but not required.
The invariant does not depend on ownership.

---

## Final note

RP does not attempt to make models “smarter”.

It simply stops them from moving  
when no stable direction exists.

Everything else is a side effect.

**RP works without the math.**
**The math explains why it works.**
