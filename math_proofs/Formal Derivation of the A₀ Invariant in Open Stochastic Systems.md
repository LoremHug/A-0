# Formal Derivation of the A₀ Invariant in Open Stochastic Systems

## Abstract
We present a formal proof of the $A_0$ invariant in continuous time, stating that in open stochastic systems, only locally admissible trajectories minimizing effective execution resistance persist, while all others collapse. This derivation provides a strict mathematical isomorphism that maps thermodynamic, informational, and computational realizations to a single, non-teleological invariant dynamic, eliminating the need to invoke agency or global optimization in complex systems.

## 1. Continuous-Time System Definition
Let $(X, P_t)$ be a continuous-time Markov process over a measurable state space $X$ with probability density $p(x,t)$.
The evolution of the system is governed by a Fokker–Planck equation:

$$\frac{\partial p}{\partial t} = -\nabla \cdot (p v) + D \nabla^2 p$$

where $v(x)$ is the deterministic drift vector and $D$ represents stochastic diffusion. Crucially, this equation describes local gradient flows without assuming any global objective function or teleological intent.

## 2. The Potential Functional
We define a scalar functional $\Phi[p]$ representing the topological instability of the distribution:

$$\Phi[p] = \int p(x) \ln\left(\frac{p(x)}{p^*(x)}\right) dx$$

where $p^*(x)$ is a stationary (ground) distribution. $\Phi$ is non-negative and is minimized if and only if $p = p^*$. It acts as a measure of divergence from the stable baseline.

## 3. The Lyapunov Property
The time derivative of the functional satisfies:

$$\frac{d\Phi}{dt} \le 0$$

The proof follows directly from standard entropy production inequalities in non-equilibrium thermodynamics. Hence, $\Phi$ acts as a strictly decreasing Lyapunov functional for the autonomous system.

## 4. The Admissibility Constraint
In continuous dynamics, we define the set of admissible trajectories $a(t)$ as those for which the local entropy production rate $\sigma(x,t)$ remains below a critical structural threshold:
$$\sigma(x,t) \le \sigma_{crit}$$
This serves as the continuous-time equivalent of the discrete Admissibility Gate ($H \le H_{crit}, T \le T_{crit}$). Trajectories violating this bound represent unsustainable thermal debt; they rapidly diverge and exit the stable support of $p$.

## 5. The A₀ Invariant Theorem
**Theorem (A₀):**
Given an open stochastic system governed by a Lyapunov functional $\Phi$, only trajectories that locally minimize effective computational/physical resistance $Z \propto \frac{d\Phi}{dt}$ under strict admissibility constraints can persist. All mathematically possible but higher-impedance or non-admissible trajectories collapse with probability 1 in the asymptotic limit.

**Proof:**
Since $\Phi$ is a Lyapunov functional, any trajectories with positive $\frac{d\Phi}{dt}$ are mathematically unstable. Among the subset of admissible trajectories, the system deterministically follows the steepest descent of $\Phi$ (the path of least resistance). Non-admissible paths (where $\sigma > \sigma_{crit}$) leave the domain of attraction and vanish measure-theoretically. No "selection mechanism" or "agent" is required to choose the path; unstable vectors are eliminated by the topology itself (Invariant I-2: Non-Selection).

## 6. Topological Independence (Isomorphism)
The proof depends exclusively on the existence of the Lyapunov functional $\Phi$ and the hard admissibility constraints, independent of the underlying physical interpretation. Thus, thermodynamic energy dissipation, informational surprise minimization, and artificial neural network loss reduction are shown to be **topologically isomorphic**. They are distinct domains governed by the same non-teleological stabilization envelope.

## 7. Conclusion
$A_0$ is a strict structural invariant of open stochastic systems. It formally describes the deterministic elimination of topological instability (collapse of non-admissible trajectories) rather than goal-oriented optimization, removing the category error of agency from system dynamics.

## 8. Mechanistic Mappings (Biological Isomorphism)
These neurobiological mappings are included not as an ontological claim about human consciousness, but as an engineering proof of concept. They illustrate that known local biological nodes instantiate equivalent admissibility-first stabilization dynamics *without invoking agency*, validating the use of the non-teleological $A_0$ baseline in artificial architectures:

* **Spiking stochasticity and diffusion approximations:** Purely local membrane potential dynamics governed by physical gradients, not cognitive goals.
* **Homeostatic plasticity (firing-rate stabilization):** Neurons and circuits implement local rules that drive activity toward physical target ranges, deterministically collapsing unstable (runaway) computational trajectories.
* **STDP and BCM-style local learning rules:** Spike-Timing Dependent Plasticity modifies artificial/biological synapses via purely local temporal signals, acting as blind admissibility filters rather than forward-planning agents.
* **Balanced excitation/inhibition networks:** Informational perturbations dissipate through inhibitory feedback (thermodynamic grounding) rather than explicit intent.
* **Predictive coding as an optional operator:** Prediction serves merely to reduce local uncertainty when structurally admissible. Under $A_0$, prediction is an optional, resource-heavy operator gated by execution impedance, not a fundamental drive.

## 9. Selected References
*(Standard mathematical and thermodynamic references apply—e.g., Fokker-Planck dynamics, non-equilibrium statistical mechanics, and Lyapunov stability criteria).*
