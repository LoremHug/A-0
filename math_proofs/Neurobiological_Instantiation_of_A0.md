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
Given an open stochastic system with Lyapunov functional Φ, only trajectories that locally minimize effective resistance Z = dΦ/dt under admissibility constraints persist. All others collapse with probability 1.

**Proof:**
Since Φ is Lyapunov, trajectories with positive dΦ/dt are unstable.
Among admissible trajectories, the system follows the steepest descent of Φ.
Non-admissible paths leave the domain of attraction and vanish measure-theoretically.

## 6. Domain Independence
The proof depends only on existence of Φ and admissibility constraints, not on physical interpretation.
Thus thermodynamic, informational, and neurobiological systems are unified at invariant level.

## 7. Conclusion
A₀ is a structural invariant of open stochastic systems describing elimination of instability rather than optimization. It applies across domains without introducing agent-based primitives.
