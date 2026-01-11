# Mathematical Proof of the A₀ Invariant

## Abstract
We present a formal proof of the A₀ invariant, stating that in open stochastic systems only locally admissible trajectories minimizing effective resistance persist, while all others collapse. The proof unifies thermodynamic, informational, and neurobiological realizations at the level of invariant dynamics.

## 1. System Definition
Let (X, P_t) be a continuous-time Markov process over state space X with probability density p(x,t).
The evolution is governed by a Fokker–Planck equation:

∂p/∂t = -∇·(p v) + D ∇²p

where v(x) is drift and D diffusion.

## 2. Potential Functional
Define a scalar functional Φ[p]:

Φ[p] = ∫ p(x) ln(p(x)/p*(x)) dx

where p*(x) is a stationary distribution. Φ is non-negative and minimized iff p = p*.

## 3. Lyapunov Property
The time derivative satisfies:

dΦ/dt ≤ 0

Proof follows from standard entropy production inequalities. Hence Φ is a Lyapunov functional.

## 4. Admissibility Constraint
Define admissible trajectories a(t) as those for which local entropy production σ(x,t) ≤ σ_crit.
Trajectories violating this bound diverge and exit the support of p.

## 5. A₀ Invariant
**Theorem (A₀):**
Given an open stochastic system with Lyapunov functional Φ, only trajectories that locally minimize effective resistance Z = dΦ/dt under admissibility constraints persist. All others collapse with probability 1 in the asymptotic limit.

**Proof:**
Since Φ is Lyapunov, trajectories with positive dΦ/dt are unstable.
Among admissible trajectories, the system follows the steepest descent of Φ.
Non-admissible paths leave the domain of attraction and vanish measure-theoretically.

## 6. Domain Independence
The proof depends only on existence of Φ and admissibility constraints, not on physical interpretation.
Thus thermodynamic, informational, and neurobiological systems are unified at invariant level.

## 7. Conclusion
A₀ is a structural invariant of open stochastic systems describing elimination of instability rather than optimization. It applies across domains without introducing agent-based primitives.

---

## 8. Mechanistic Mappings and Examples (Neurobiology → A₀)

These mappings do not imply that biological systems explicitly optimize Φ or compute A₀. They illustrate that known local biological rules instantiate equivalent admissibility-first stabilization dynamics.

This section provides concrete, citable neurobiological mechanisms that instantiate A₀-like local stabilization (admissibility-first, minimal local resistance) without invoking agency or global planning. These are examples, not exhaustive proofs; they illustrate how local rules yield stable fixed points or collapse of unstable trajectories.

- Spiking stochasticity and diffusion approximations:
	Local membrane potential dynamics with stochastic inputs are well-modeled by diffusion processes; population activity admits Fokker–Planck descriptions where entropy production bounds and Lyapunov-like functionals govern relaxation to stable regimes. Representative sources: Gerstner & Kistler (2002), Tuckwell (1988), Faisal–Selen–Wolpert (2008).

- Homeostatic plasticity (firing-rate stabilization):
	Neurons and circuits implement homeostatic rules (synaptic scaling, intrinsic excitability adjustments) that drive activity toward target ranges, collapsing unstable (runaway) trajectories. This is admissibility-first control: transitions that increase instability (far from set-point) are suppressed; low-impedance corrections persist. Representative sources: Turrigiano (1998, 2012), O’Leary et al. (2013).

- STDP and BCM-style local learning rules:
	Spike-Timing Dependent Plasticity (STDP) and BCM rules modify synapses via purely local signals. These act as admissibility filters (temporal correlations) and induce stable attractors (feature selectivity, receptive fields) while eliminating unstable configurations. Representative sources: Bi & Poo (1998), Abbott & Nelson (2000), Bienenstock–Cooper–Munro (1982).

- Balanced excitation/inhibition networks:
	Networks with balanced E/I achieve stable asynchronous states via local interactions; perturbations dissipate through inhibitory feedback and recurrent structure. Unbalanced trajectories collapse (oscillation/runaway) back to balance, consistent with minimal local discharge. Representative sources: van Vreeswijk & Sompolinsky (1996), Brunel (2000), Hennequin et al. (2018).

- Predictive coding as optional operator within A₀ envelope:
	Predictive-coding–like mechanisms can serve as internal operators to reduce uncertainty when admissible (i.e., when their invocation lowers local instability and cost). Under A₀, prediction is optional and gated; silence/quiescence remains a valid fixed point when admissibility is indeterminate. Representative sources: Rao & Ballard (1999), Friston (2010).

**Mapping note:** In each case, local rules enforce admissibility before continuation, and relaxation proceeds via minimal-resistance transitions. Global optimality or agency is not required to explain stabilized outcomes.

---

## 9. Selected References (Pointers)

- Gerstner W., Kistler W.M. (2002) Spiking Neuron Models
- Tuckwell H.C. (1988) Introduction to Theoretical Neurobiology
- Faisal A.A., Selen L.P.J., Wolpert D.M. (2008) Noise in the nervous system
- Turrigiano G. (1998, 2012) Homeostatic synaptic plasticity
- O’Leary T., Williams A.H., Caplan J.S., Marder E. (2013) Homeostasis in neuronal networks
- Bi G., Poo M. (1998) Synaptic modifications by spike timing
- Abbott L.F., Nelson S.B. (2000) Synaptic plasticity: taming variability
- Bienenstock E., Cooper L., Munro P. (1982) BCM theory of synaptic modification
- van Vreeswijk C., Sompolinsky H. (1996) Balanced excitation and inhibition
- Brunel N. (2000) Dynamics of sparsely connected networks
- Hennequin G., Vogels T.P., Gerstner W. (2018) Optimal control of transient dynamics in balanced networks
- Rao R.P.N., Ballard D.H. (1999) Predictive coding in the visual cortex
- Friston K. (2010) The free-energy principle

**Scope clarification:** These references support domain-level plausibility of A₀-style local stabilization. They do not claim strict isomorphism across all scales; the invariant connection holds under stated assumptions (existence of suitable potentials, admissibility gates, and local relaxation dynamics).
