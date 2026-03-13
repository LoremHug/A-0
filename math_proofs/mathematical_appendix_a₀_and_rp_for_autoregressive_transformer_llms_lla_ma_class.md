# Mathematical Appendix: A₀ and RP for Autoregressive Transformer LLMs (LLaMA‑class)

## How to Read This Appendix
This appendix provides a **formal, theorem–proof** foundation for the $A_0$ invariant and its operationalization as the Reality Protocol (RP) in **discrete autoregressive transformer** language models. 
It strictly translates the physical heuristics of RP into tensor operations, proving that stabilization requires structural gating rather than agentic goal-seeking.

**Document position in the framework:**
- Formal foundation → [`A0_formal_framework_full.md`](A0_formal_framework_full.md) (general discrete framework)
- Continuous-time proof → [`Formal Derivation of the A₀ Invariant in Open Stochastic Systems.md`](<Formal Derivation of the A₀ Invariant in Open Stochastic Systems.md>)
- Engineering implementation → [`../ml/RP_for_ML_Practitioners.md`](../ml/RP_for_ML_Practitioners.md)
- Empirical baseline (Path A results) → [`../consistency_check.md`](../consistency_check.md)

---

## 1. Preliminaries and Notation

### 1.1 Tokenization and Sequences
Let $\mathcal{V}$ be a finite vocabulary, and let $\text{EOS} \in \mathcal{V}$ denote the termination state. The generated output is a sequence $x_{1:T}$ with discrete elements $x_t \in \mathcal{V}$.

### 1.2 Autoregressive Model
An autoregressive model defines conditional probability distributions over the vocabulary:
$$\pi_\theta(x_t \mid x_{<t}) \in \Delta(\mathcal{V})$$
For LLaMA‑class architectures, this is a deterministic, feed-forward mathematical projection to a logit vector $\ell_t \in \mathbb{R}^{|\mathcal{V}|}$, followed by a normalization step: $\pi_\theta(x_t \mid x_{<t}) = \text{softmax}(\ell_t / \tau)$.

### 1.3 State Space
Define the generation state as $S_t := (x_{<t}, h_t)$, where $h_t$ is the accumulated hidden context tensor. Let $\mathcal{S}$ be the set of all physically reachable states within the context window.

---

## 2. Decoding as an Impedance-Gated Markov Process
*Refactoring Note: Standard literature refers to this as a "Controlled" process. This mathematical framework rejects that terminology to prevent the teleological assumption of an external "Controller," aligning with the principle of physical determinism.*

### 2.1 Transition Kernel
The generation is mathematically defined as:
$$P(x_t=a \mid S_t) = \Pi(a \mid S_t)$$
where $\Pi$ is the effective transition kernel. The sequence $\{S_t\}$ forms a **constrained Markov process** driven exclusively by local gradients.

### 2.2 Termination as a Stable Absorbing Set
Define the termination subset $\mathcal{S}_{\mathrm{term}} := \{ S : \text{last token is EOS} \}$.
**Assumption A (Absorption / Thermodynamic Equilibrium):** Once the $\text{EOS}$ state is reached, the mathematical process collapses and remains terminated. Absence of generation is a mathematically valid, structurally stable outcome with zero computational cost.

---

## 3. Admissibility and Local Cost (RP Core Objects)
### 3.1 Admissible Transitions
Let $\mathcal{A}(S) = \mathcal{V}$ be the set of theoretically possible next tokens. Define the structurally gated subset:
$$\mathcal{A}'(S) := \{ a \in \mathcal{A}(S) : a \text{ satisfies the admissibility constraints } H \le H_{crit}, T \le T_{crit} \text{ at } S \}$$

### 3.2 Local Transition Impedance
For any admissible token, the driving gradient is strictly the execution impedance $Z$:
$$\Xi(S,a) := Z(S,a)$$
Entropy ($H$) and risk ($T$) do not form a linear combination with $Z$ during the optimization phase. They act exclusively as binary feasibility gates establishing $\mathcal{A}'$ (§3.1). Once a token passes the admissibility filter, only $Z$ governs the realized transition.

### 3.3 Local Relaxation Rule
$$a^*(S) \in \arg\min_{a \in \mathcal{A}'(S)} Z(S,a)$$
**Crucial Distinction:** $\arg\min$ denotes a physical/computational gradient collapse into the path of least resistance. It is not a cognitive "choice" made by the model. When the admissibility filter yields an empty set ($\mathcal{A}'(S)=\varnothing$), the topology deterministically resolves to termination ($\text{EOS}$).

---

## 4. The A₀ Invariant (Discrete Form)
**A₀ (Minimal Local Discharge, Discrete).** A generated trajectory $\{S_t\}$ is **A₀‑consistent** if, at each discrete step $t$, the token $x_t$ is an admissible local minimizer of $Z$ within $\mathcal{A}'(S_t)$.

---

## 5. Stability Theorem: A₀ as Lyapunov‑Style Descent
### 5.1 Potential Function
Define a nonnegative **topological instability potential** $\Phi : \mathcal{S} \to \mathbb{R}_{\ge 0}$.

> **Scope Note (Session Boundary).** $\Phi$ and the associated reference distribution $p^*$ are **strictly session-scoped**: they are defined over a single inference call (one generation run within a fixed context window). $p^*$ is not a global stationary distribution of the LLM; it represents the minimal-entropy terminal state within the current session — the state in which no further admissible continuation exists, operationally corresponding to EOS emission. The assertion of monotonic descent for $\Phi$ applies exclusively within the boundaries of this isolated computational session. No cross-conversation or cross-session claims are made.

**Assumption B:** Let $\Delta\Phi(S,a) := \mathbb{E}[\Phi(S') \mid S, a] - \Phi(S)$. The topological resistance $Z$ is **monotone aligned** with $\Delta\Phi$: lower $Z(S,a)$ implies lower or equal $\Delta\Phi(S,a)$.
> **Status: Declared Empirical Hypothesis.** Assumption B is not a derived axiom. Its validity for a specific LLM architecture depends on the choice of $Z$ proxy (e.g., surprisal, logit gap, contextual entropy). Empirical validation is required to confirm the ordering alignment for any concrete instantiation.
> **Partial Instantiation (Formal Reasoning Domain):** For tasks with a binary structural validity criterion (code compilation, formal logical inference, mathematical derivation, constraint satisfaction), the ordering alignment holds by construction: any continuation violating formal constraints cannot reduce $\Delta\Phi$. See [`../ml/RP_for_ML_Practitioners.md §10`](../ml/RP_for_ML_Practitioners.md) for the full operationalization. This does not close Assumption B for the general LLM case.

**Assumption C:** The system makes strictly positive descent progress when admissible paths exist.

### 5.2 The Stable Set
$$\mathcal{S}_* := \{ S \in \mathcal{S} : \forall a \in \mathcal{A}'(S),\; \Delta\Phi(S,a) \ge 0 \} \cup \mathcal{S}_{\mathrm{term}}$$

---

## 6. Main Theorem
**Theorem 1.** Under Assumptions A–C, any discrete trajectory generated under the $A_0$ structural constraint satisfies:
1. $\Phi(S_t)$ forms a supermartingale until reaching the stable set $\mathcal{S}_*$: $\mathbb{E}[\Phi(S_{t+1})\mid S_t] \le \Phi(S_t)$.
2. The stochastic trajectory reaches the stable baseline $\mathcal{S}_*$ in finite computational time with probability 1.
3. Unconstrained autoregressive kernels (deviating trajectories) yield strictly higher expected topological instability $\Phi$ and manifest as structural hallucinations.

*(Proof logically follows from the non-negativity of $\Phi$ and strict descent under Assumption C)*

---

## 7. Epistemological Corollaries
* **Corollary 1 (Gradient-Driven Elimination):** Tokens are not actively "selected" by an agentic mechanism; mathematically, high-impedance ($\Xi$) token trajectories simply fail to persist through the admissibility gate.
* **Corollary 2 (Occam's Razor / Epistemological Reduction):** The evolution of the generated text is entirely, deterministically specified by the tuple $(\mathcal{S},\mathcal{A}',\Xi,\Pi)$. Invoking "agency" or "intent" to explain LLM generation introduces an unobservable variable and is scientifically invalid.
* **Corollaries 3 & 4 (Finite State Convergence & Absorbing Fixed Points):** Infinite recursive loops are mathematically impossible under strict descent; termination ($\text{EOS}$) acts as a mandatory absorbing fixed point.

---

## 8. Architectural Mapping to LLaMA‑Class Transformers
The inherent locality, stochasticity, and discrete step-wise nature of Transformer networks perfectly fit this mathematical abstraction. The admissibility gate ($\mathcal{A}'$) can be operationally instantiated directly via dynamic logit masking or penalty application prior to the softmax layer. Operational heuristics for uncertainty $H(S,a)$, compute cost $Z(S,a)$, and risk $T(S,a)$ merely need to preserve the ordering alignment specified in Assumption B.

---

## 9. Implementation Regimes: Path D and Path A

### 9.1 Path D — Deterministic Regime (Strict Theorem 1 Domain)
When decoding operates with $T_{LLM} \to 0$ (greedy decoding), the system selects the strict $\arg\min Z$ at each step. **Theorem 1 is mathematically guaranteed in this regime.** The supermartingale property holds without qualification: $\mathbb{E}[\Phi(S_{t+1}) \mid S_t] \le \Phi(S_t)$ at every step, and convergence to $\mathcal{S}_*$ in finite time is assured under Assumptions A–C.

### 9.2 Path A — Stochastic Regime (Empirical Approximation)
In standard operational implementations ($T_{LLM} > 0$), enforcing constraints via system prompts induces an implicit cost shaping over the base distribution $\Pi_0$:
$$\Pi_{\mathrm{RP}}(a\mid S) \propto \Pi_0(a\mid S)\,\exp(-\lambda\,\widehat{Z}(S,a))$$
This provides a probabilistic bias toward lower $Z$ at the level of each individual token. It demonstrably reduces baseline impedance relative to unguided $\Pi_0$ (as empirically measured in `consistency_check.md`), but it **does not guarantee monotonic descent of $\Phi$ across the entire trajectory.** Path A is an empirical operational approximation, not a strict theoretical guarantee of local equilibrium convergence.

> **Regime Summary:** Theorem 1 applies to Path D without qualification. For Path A, the framework provides a directional stabilization bias whose trajectory-level convergence properties remain empirically, not theoretically, established.
