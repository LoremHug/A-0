# Mathematical Appendix: A₀ and RP for Autoregressive Transformer LLMs (LLaMA‑class)

## How to Read This Appendix
This appendix provides a **formal, theorem–proof** foundation for the $A_0$ invariant and its operationalization as the Reality Protocol (RP) in **discrete autoregressive transformer** language models. 
It strictly translates the physical heuristics of RP into tensor operations, proving that stabilization requires structural gating rather than agentic goal-seeking.

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
For any admissible token, define the computational resistance:
$$\Xi(S,a) := \alpha Z(S,a) + \beta H(S,a) + \gamma T(S,a)$$
with scalar weights $\alpha,\beta,\gamma \ge 0$.

### 3.3 Local Relaxation Rule
$$a^*(S) \in \arg\min_{a \in \mathcal{A}'(S)} \Xi(S,a)$$
**Crucial Distinction:** $\arg\min$ denotes a physical/computational gradient collapse into the path of least resistance. It is not a cognitive "choice" made by the model. When the admissibility filter yields an empty set ($\mathcal{A}'(S)=\varnothing$), the system forces a collapse to termination ($\text{EOS}$).

---

## 4. The A₀ Invariant (Discrete Form)
**A₀ (Minimal Local Discharge, Discrete).** A generated trajectory $\{S_t\}$ is **A₀‑consistent** if, at each discrete step $t$, the token $x_t$ is an admissible local minimizer of the execution impedance $\Xi$ at state $S_t$.

---

## 5. Stability Theorem: A₀ as Lyapunov‑Style Descent
### 5.1 Potential Function
Define a nonnegative **topological instability potential** $\Phi : \mathcal{S} \to \mathbb{R}_{\ge 0}$.
**Assumption B:** Let $\Delta\Phi(S,a) := \mathbb{E}[\Phi(S') \mid S, a] - \Phi(S)$. The execution impedance $\Xi$ is **monotone aligned** with $\Delta\Phi$.
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

## 9. Prompt‑Level Dynamics as a Topological Attractor
Implementing structural constraints via system prompts (rather than direct kernel logit-masking) induces an implicit cost shaping over the model's base distribution $\Pi_0$:
$$\Pi_{\mathrm{RP}}(a\mid S) \propto \Pi_0(a\mid S)\,\exp(-\lambda\,\widehat\Xi(S,a))$$
Theorem 1 applies conditionally in this regime: the semantic vector field of the prompt establishes a mathematically defined "basin of attraction," increasing the thermodynamic resistance of non-admissible tokens and forcing the stochastic process to converge upon structurally stable outcomes.
