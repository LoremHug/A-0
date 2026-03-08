# Formal Derivation of the A₀ Invariant in Open Stochastic Systems

## Abstract
We present a formal proof of the $A_0$ invariant, stating that in open stochastic systems only locally admissible trajectories minimizing effective resistance persist, while all others collapse. The proof unifies thermodynamic, informational, and neurobiological realizations at the level of invariant dynamics.

## 1. System Definition
Let $(X, P_t)$ be a continuous-time Markov process over state space $X$ with probability density $p(x,t)$.
The evolution is governed by a Fokker–Planck equation:

$$\frac{\partial p}{\partial t} = -\nabla \cdot (p v) + D \nabla^2 p$$

where $v(x)$ is drift and $D$ diffusion.



## 2. Potential Functional
Define a scalar functional $\Phi[p]$:

$$\Phi[p] = \int p(x) \ln\left(\frac{p(x)}{p^*(x)}\right) dx$$

where $p^*(x)$ is a stationary distribution. $\Phi$ is non-negative and minimized iff $p = p^*$.

## 3. Lyapunov Property
The time derivative satisfies:

$$\frac{d\Phi}{dt} \le 0$$

Proof follows from standard entropy production inequalities. Hence $\Phi$ is a Lyapunov functional.

## 4. Admissibility Constraint
Define admissible trajectories $a(t)$ as those for which local entropy production $\sigma(x,t) \le \sigma_{crit}$.
Trajectories violating this bound diverge and exit the support of $p$.

## 5. A₀ Invariant
**Theorem (A₀):**
Given an open stochastic system with Lyapunov functional $\Phi$, only trajectories that locally minimize effective resistance $Z = \frac{d\Phi}{dt}$ under admissibility constraints persist. All others collapse with probability 1 in the asymptotic limit.

**Proof:**
Since $\Phi$ is Lyapunov, trajectories with positive $\frac{d\Phi}{dt}$ are unstable. Among admissible trajectories, the system follows the steepest descent of $\Phi$. Non-admissible paths leave the domain of attraction and vanish measure-theoretically.

## 6. Domain Independence
The proof depends only on existence of $\Phi$ and admissibility constraints, not on physical interpretation. Thus thermodynamic, informational, and neurobiological systems are unified at invariant level.

## 7. Conclusion
$A_0$ is a structural invariant of open stochastic systems describing elimination of instability rather than optimization.

## 8. Mechanistic Mappings and Examples (Neurobiology → A₀)
These mappings illustrate that known local biological rules instantiate equivalent admissibility-first stabilization dynamics without invoking agency.

* **Spiking stochasticity and diffusion approximations:** Local membrane potential dynamics.
* **Homeostatic plasticity (firing-rate stabilization):** Neurons and circuits implement rules that drive activity toward target ranges, collapsing unstable (runaway) trajectories.
* **STDP and BCM-style local learning rules:** Spike-Timing Dependent Plasticity modifies synapses via purely local signals, acting as admissibility filters.
* **Balanced excitation/inhibition networks:** Perturbations dissipate through inhibitory feedback.
* **Predictive coding as optional operator:** Can serve to reduce uncertainty when admissible. Under $A_0$, prediction is optional and gated.

## 9. Selected References (Pointers)
*(See original file for references list)*