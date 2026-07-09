+++
order = 14
subject = "Mathematics"
tags = ["math", "differential-equations", "ode", "nonlinear", "stability", "linearization", "lyapunov", "phase-plane"]
+++

# Differential Equations — Nonlinear Systems and Stability

## 14.1 Why Nonlinear Systems Matter

Q: Why do nonlinear ODEs dominate real-world modeling, even though linear techniques are emphasized in introductory courses?
A: Most physical systems — pendulums with large swings, predator-prey populations, chemical reaction rates, neural dynamics — involve products, powers, or transcendental functions of the state variables. Linearity is a mathematical convenience, not a feature of nature. Exact closed-form solutions rarely exist for nonlinear ODEs, so we shift from solving to qualitative analysis: what do trajectories look like, where do they settle, and how do they respond to perturbations?

Q: Why can't we rely on the same toolkit (characteristic equations, superposition, variation of parameters) for nonlinear ODEs?
A: Those tools depend on the superposition principle, which only holds when the operator is linear. Nonlinear systems lose superposition, so sums of solutions are not solutions, and eigenvalue methods fail globally. We instead study local behavior via linearization and global behavior via qualitative methods like phase portraits and Lyapunov functions.

C: Because exact solutions are rare for nonlinear ODEs, we use [qualitative methods] (phase portraits, stability analysis, linearization) instead of explicit formulas.

## 14.2 Autonomous Systems

Q: Why does the absence of explicit $t$-dependence simplify the analysis of a system $\vec{x}' = \vec{f}(\vec{x}, t)$?
A: When $\vec{f}$ does not depend on $t$ explicitly, the future evolution from any state $\vec{x}$ is determined solely by $\vec{x}$ itself, not by when we start. Trajectories are therefore fixed curves in phase space, and the vector field $\vec{f}(\vec{x})$ alone encodes all dynamics. Time-translation symmetry means we can slide a solution along $t$ and get another solution.

C: An [autonomous] system is one of the form $\vec{x}' = \vec{f}(\vec{x})$, where the right-hand side has no explicit $t$ dependence.

C: In an autonomous system, the [vector field] $\vec{f}(\vec{x})$ assigns a velocity vector to every point in phase space, and trajectories follow this field.

Q: Why can two distinct trajectories of an autonomous system never cross in phase space?
A: Because the vector field $\vec{f}(\vec{x})$ assigns a unique velocity to each point, uniqueness of ODE solutions implies that through any point passes exactly one trajectory. If two crossed, the point of crossing would have two different future evolutions, violating uniqueness.

## 14.3 Equilibrium (Critical) Points

C: An [equilibrium point] (or critical point) of $\vec{x}' = \vec{f}(\vec{x})$ is a point $\vec{x}^*$ where $\vec{f}(\vec{x}^*) = \vec{0}$.

Q: Why is an equilibrium point also called a constant solution of the system?
A: If $\vec{f}(\vec{x}^*) = \vec{0}$, then starting at $\vec{x}^*$ gives $\vec{x}'(t) = \vec{0}$ for all $t$, so $\vec{x}(t) \equiv \vec{x}^*$ is a valid (constant) solution. The system simply does not move.

C: At an equilibrium point $\vec{x}^*$, the solution starting there is [constant]: $\vec{x}(t) = \vec{x}^*$ for all $t$.

## 14.4 Finding Equilibria

Q: How do you find the equilibria of an autonomous system $\vec{x}' = \vec{f}(\vec{x})$?
A: Set every component of $\vec{f}$ to zero simultaneously and solve the resulting algebraic system $\vec{f}(\vec{x}) = \vec{0}$. The solutions are typically isolated points (though continuous families can occur). This is an algebra problem, not a differential equations problem.

P: Find all equilibria of the system $x' = x - xy$, $y' = -y + xy$, where $x$ and $y$ are population densities.

S:
**IDENTIFY**: Finding equilibria of a 2D autonomous system (Lotka-Volterra form).

**PLAN**:
- Set both components to zero: $x - xy = 0$ and $-y + xy = 0$.
- Factor and solve the resulting algebraic system.

**EXECUTE**:
1. From $x(1 - y) = 0$: either $x = 0$ or $y = 1$.
2. From $y(x - 1) = 0$: either $y = 0$ or $x = 1$.
3. Case $x = 0$ combined with $y(x-1)=0$ gives $y = 0$. Equilibrium: $(0, 0)$.
4. Case $y = 1$ combined with $y(x-1)=0$ gives $x = 1$. Equilibrium: $(1, 1)$.

**EVALUATE**:
- Two equilibria: the trivial extinction state $(0, 0)$ and the coexistence state $(1, 1)$.
- Verify: at $(1,1)$, $x' = 1 - 1 = 0$ and $y' = -1 + 1 = 0$. ✓

## 14.5 Stability — Qualitative Definitions

Q: Why do we need three separate notions of stability (stable, asymptotically stable, unstable) rather than just one?
A: They capture different behaviors of nearby trajectories. A solution may stay close but never return (stable but not asymptotic, like a center), may actively return to equilibrium (asymptotically stable, like a damped spring at rest), or may drift away (unstable). Distinguishing these matters because physical systems may tolerate bounded oscillation but not divergence.

C: An equilibrium $\vec{x}^*$ is [stable] if trajectories starting near $\vec{x}^*$ stay near $\vec{x}^*$ for all future time.

C: An equilibrium $\vec{x}^*$ is [asymptotically stable] if it is stable AND nearby trajectories actually converge to $\vec{x}^*$ as $t \to \infty$.

C: An equilibrium $\vec{x}^*$ is [unstable] if there exist arbitrarily close initial points whose trajectories eventually leave a fixed neighborhood of $\vec{x}^*$.

Q: What's the difference between stability and asymptotic stability?
A: Stability only requires trajectories to stay bounded near the equilibrium — they may orbit around it forever. Asymptotic stability additionally requires trajectories to actually approach the equilibrium. A pendulum at the bottom with damping is asymptotically stable; a frictionless pendulum at the bottom is only stable (it oscillates forever).

## 14.6 Linearization at an Equilibrium

Q: Why does Taylor expanding $\vec{f}$ around an equilibrium $\vec{x}^*$ give a useful approximation of the dynamics nearby?
A: Near $\vec{x}^*$, the nonlinear terms become second-order small in $\vec{x} - \vec{x}^*$, so the linear term — the Jacobian times the displacement — dominates. This replaces an intractable nonlinear system with a 2D (or $n$D) linear system whose behavior we can fully classify using eigenvalues. The approximation is local but powerful.

C: Near an equilibrium $\vec{x}^*$, the linearized system is $\vec{x}' \approx J(\vec{x}^*)(\vec{x} - \vec{x}^*)$, where $J(\vec{x}^*)$ is the [Jacobian matrix] evaluated at $\vec{x}^*$.

Q: Why does the constant term $\vec{f}(\vec{x}^*)$ not appear in the linearization?
A: Because $\vec{x}^*$ is an equilibrium, $\vec{f}(\vec{x}^*) = \vec{0}$, so the zeroth-order term in the Taylor expansion vanishes. The first surviving term is the Jacobian acting on the displacement $\vec{x} - \vec{x}^*$.

## 14.7 The Jacobian Matrix

C: The [Jacobian matrix] of $\vec{f}: \mathbb{R}^n \to \mathbb{R}^n$ has entries $J_{ij} = \partial f_i/\partial x_j$, where $f_i$ is the $i$-th component of $\vec{f}$ and $x_j$ is the $j$-th state variable.

Q: For a 2D system $x' = f(x,y)$, $y' = g(x,y)$, what does the Jacobian look like?
A: It's the $2\times 2$ matrix
$$J = \begin{pmatrix} \partial f/\partial x & \partial f/\partial y \\ \partial g/\partial x & \partial g/\partial y \end{pmatrix}$$
evaluated at the equilibrium of interest. Its eigenvalues determine the local dynamics.

P: Compute the Jacobian of $x' = x - xy$, $y' = -y + xy$ at the equilibrium $(1, 1)$.

S:
**IDENTIFY**: Compute partial derivatives and evaluate at a point.

**PLAN**:
- Take all four partial derivatives.
- Assemble into a $2 \times 2$ matrix.
- Substitute $(x, y) = (1, 1)$.

**EXECUTE**:
1. $\partial f/\partial x = 1 - y$; $\partial f/\partial y = -x$.
2. $\partial g/\partial x = y$; $\partial g/\partial y = -1 + x$.
3. $J(x,y) = \begin{pmatrix} 1-y & -x \\ y & x-1 \end{pmatrix}$.
4. At $(1,1)$: $J = \begin{pmatrix} 0 & -1 \\ 1 & 0 \end{pmatrix}$.

**EVALUATE**:
- $\det J = 1 > 0$, $\operatorname{tr} J = 0$: eigenvalues are $\pm i$.
- This suggests a center for the linearization; pure imaginary eigenvalues make the equilibrium non-hyperbolic, so linearization alone is inconclusive for the nonlinear system.

## 14.8 Hartman-Grobman Theorem (Informal)

Q: Why is the Hartman-Grobman theorem the foundation of linearization-based stability analysis?
A: It guarantees that when the Jacobian has no eigenvalues with zero real part (a "hyperbolic" equilibrium), the nonlinear system's phase portrait near $\vec{x}^*$ is topologically equivalent to its linearization's. That justifies using eigenvalues of $J$ to classify the nonlinear equilibrium's stability — the nonlinear terms cannot qualitatively change the picture locally.

C: An equilibrium is called [hyperbolic] if every eigenvalue of its Jacobian has nonzero real part.

C: Hartman-Grobman says that at a hyperbolic equilibrium, the nonlinear flow is [topologically equivalent] to the linearized flow in some neighborhood.

Q: When does the Hartman-Grobman theorem fail to apply, and what goes wrong?
A: It fails when the Jacobian has at least one eigenvalue with zero real part (a non-hyperbolic equilibrium), such as pure imaginary eigenvalues (potential center) or a zero eigenvalue. In those cases nonlinear terms become decisive: a linearized center can become a stable or unstable spiral, or exotic shapes like Bogdanov-Takens can appear.

## 14.9 Classifying Equilibria from Jacobian Eigenvalues

Q: Why can we reuse the 2D linear classification (node, saddle, spiral, center) for nonlinear systems?
A: Because by Hartman-Grobman, the hyperbolic cases (nodes, saddles, genuine spirals) carry over unchanged from the linearization to the nonlinear system. Only the center case — pure imaginary eigenvalues — is ambiguous, since zero real part makes it non-hyperbolic and nonlinear corrections can push it either way.

C: If both eigenvalues of $J(\vec{x}^*)$ have negative real parts, the equilibrium is an [asymptotically stable] node or spiral.

C: If both eigenvalues have positive real parts, the equilibrium is an [unstable] node or spiral.

C: If the eigenvalues are real with opposite signs, the equilibrium is a [saddle] (always unstable).

C: If the eigenvalues are pure imaginary ($\pm i\beta$), the linearization predicts a [center], but the nonlinear system may instead be a stable or unstable spiral.

Q: Why is the "center" case the one we must treat with special care in nonlinear analysis?
A: Because the eigenvalues have zero real part, the equilibrium is non-hyperbolic and Hartman-Grobman does not apply. Tiny nonlinear terms that would be ignored near a node or saddle can add or subtract energy each orbit, turning closed orbits into inward or outward spirals. A genuine nonlinear center requires additional structure, like a conserved quantity or reversibility.

## 14.10 Limit Cycles

C: A [limit cycle] is an isolated closed trajectory: a periodic orbit such that all nearby trajectories spiral toward it or away from it.

Q: Why can't a linear 2D system have a limit cycle?
A: In a linear system with a center, closed orbits come in a continuous family — every initial condition inside gives a closed orbit — so none is isolated. A true limit cycle is isolated, meaning neighboring trajectories are not periodic. This "isolated periodicity" is inherently nonlinear; only nonlinear terms can pump energy in on one side of the cycle and dissipate it on the other.

C: A limit cycle is [stable] if nearby trajectories spiral toward it, [unstable] if they spiral away.

Q: Why are limit cycles important for modeling real-world oscillators?
A: Physical oscillators (heartbeats, neural spikes, laser outputs, business cycles) have a preferred amplitude that the system returns to after perturbation — exactly the defining property of a stable limit cycle. Linear models cannot produce this: linear oscillators have amplitudes set by initial conditions, not by the equations themselves.

## 14.11 Van der Pol Oscillator

C: The [Van der Pol oscillator] is $x'' - \mu(1 - x^2)x' + x = 0$, where $x$ is the displacement and $\mu > 0$ is a nonlinearity parameter.

Q: Why does the Van der Pol oscillator possess a stable limit cycle for $\mu > 0$?
A: The damping coefficient $-\mu(1 - x^2)$ is negative (energy-injecting) for small $|x| < 1$ and positive (energy-dissipating) for large $|x| > 1$. Small oscillations grow; large oscillations decay. They meet at an isolated closed orbit — a stable limit cycle — whose amplitude is determined by the equation, not the initial condition.

Q: What is the physical origin of the Van der Pol equation?
A: Van der Pol introduced it in the 1920s to model triode-tube electronic oscillators whose damping changed sign with amplitude. It has since become the canonical example of self-sustained nonlinear oscillation and a test case for perturbation and numerical methods.

## 14.12 Predator-Prey (Lotka-Volterra)

C: The [Lotka-Volterra] predator-prey system is $dx/dt = ax - bxy$, $dy/dt = -cy + dxy$, where $x$ is prey population, $y$ is predator population, and $a, b, c, d > 0$ are rate constants.

Q: Why does $-bxy$ appear in the prey equation and $+dxy$ in the predator equation?
A: The term $xy$ represents encounter rate (mass-action): more prey and predators together means more encounters. Each encounter harms prey ($-bxy$) and benefits predators by providing food ($+dxy$). The coefficients $b$ and $d$ differ because prey loss and predator gain per encounter need not match.

Q: What are the equilibria of the standard Lotka-Volterra system $x' = ax - bxy$, $y' = -cy + dxy$?
A: Two equilibria: the extinction state $(0, 0)$ and the coexistence state $(c/d, a/b)$. The first represents both populations vanishing; the second is the population ratio at which prey birth exactly balances predation and predator death exactly balances predator reproduction.

Q: Why does linearization classify $(0,0)$ as a saddle in Lotka-Volterra?
A: At $(0,0)$ the Jacobian is $\operatorname{diag}(a, -c)$ with eigenvalues $a > 0$ (prey grows in absence of predators) and $-c < 0$ (predators starve in absence of prey). Opposite-sign real eigenvalues ⟹ saddle. Ecologically: if you lose all predators prey explodes; if you lose all prey predators crash.

Q: Why is the coexistence equilibrium in the standard Lotka-Volterra model a nonlinear center rather than a spiral?
A: The Jacobian at $(c/d, a/b)$ has pure imaginary eigenvalues, so linearization predicts a center but is ambiguous. The full system possesses a conserved quantity (a first integral), so every trajectory lies on a level set of that conserved quantity — closed orbits. The nonlinear system is therefore a genuine center, and predator and prey populations oscillate periodically.

## 14.13 Lyapunov Functions

C: A [Lyapunov function] for an equilibrium $\vec{x}^*$ is a continuously differentiable scalar function $V(\vec{x})$ that is positive definite near $\vec{x}^*$ (meaning $V(\vec{x}^*) = 0$ and $V(\vec{x}) > 0$ elsewhere) with $\dot V(\vec{x}) \le 0$ along trajectories.

Q: For the system $\vec{x}' = \vec{f}(\vec{x})$, what is the derivative of a scalar function $V$ along trajectories?
A: $\dot V = \nabla V \cdot \vec{f}(\vec{x})$, where $\nabla V$ is the gradient of $V$.

Q: Why does the existence of a Lyapunov function with $\dot V \le 0$ imply stability of the equilibrium?
A: The level sets $V = c$ are nested around $\vec{x}^*$ because $V$ is positive definite. Since $\dot V \le 0$, trajectories cannot cross outward through level sets — they are trapped inside whichever level set they start on. A trajectory starting inside a small level set stays inside a small neighborhood. That's the definition of stability.

Q: What strengthens stability to asymptotic stability in Lyapunov's method?
A: Requiring the strict inequality $\dot V(\vec{x}) < 0$ for $\vec{x} \ne \vec{x}^*$. Then $V$ strictly decreases along every non-equilibrium trajectory, but $V \ge 0$, so $V \to 0$, which forces $\vec{x} \to \vec{x}^*$. Strict decrease ⟹ convergence.

C: If $\dot V < 0$ for all $\vec{x} \ne \vec{x}^*$ (strict decrease), then $\vec{x}^*$ is [asymptotically stable].

## 14.14 Why Lyapunov Methods Matter

Q: Why is the Lyapunov method valuable even when linearization already works?
A: Linearization gives only local stability and fails at non-hyperbolic equilibria (centers, zero eigenvalues). A Lyapunov function proves stability without requiring eigenvalue computation or even solving the ODE, and it can establish global asymptotic stability by showing a basin of attraction — something eigenvalues alone cannot do.

Q: What is the main difficulty of the Lyapunov method in practice?
A: There is no algorithm for finding a Lyapunov function; it requires inspired guessing, often guided by physical energy, entropy, or Hamiltonian-like quantities. For mechanical systems, total energy (kinetic + potential) is frequently a Lyapunov function; for others, quadratic forms $V = \vec{x}^T P \vec{x}$ with $P$ positive definite are standard starting points.

## 14.15 Conservation Laws

C: A [conserved quantity] (first integral) for $\vec{x}' = \vec{f}(\vec{x})$ is a scalar function $E(\vec{x})$ satisfying $\dot E = \nabla E \cdot \vec{f} = 0$ along all trajectories.

Q: Why do level sets of a conserved quantity coincide with trajectories of the system?
A: If $\dot E = 0$, then $E$ is constant along every trajectory. Each trajectory is therefore confined to a single level set $E = c$. In 2D autonomous systems, this forces trajectories to be curves, often closed loops, and gives an explicit global picture of the phase portrait without solving the ODE.

Q: How is a conserved quantity related to a Lyapunov function?
A: A conserved quantity satisfies $\dot E = 0$ everywhere, which is weaker than $\dot V \le 0$ with equality only at $\vec{x}^*$. Conserved quantities prove stability (no escape from level sets) but not asymptotic stability, since trajectories do not approach $\vec{x}^*$ — they orbit. Energy in frictionless mechanics is the classic example.

C: For conservative mechanical systems, [total energy] $E = \frac{1}{2}m v^2 + U(x)$ is a conserved quantity, where $m$ is mass, $v$ is velocity, and $U(x)$ is potential energy.

## 14.16 Phase Plane Sketching

C: A [nullcline] is a curve where one component of the vector field vanishes: the $x$-nullcline is $f_1(x, y) = 0$ and the $y$-nullcline is $f_2(x, y) = 0$.

Q: Why are nullclines useful for sketching phase portraits?
A: Equilibria lie at intersections of nullclines. On the $x$-nullcline ($f_1 = 0$), trajectories move purely vertically; on the $y$-nullcline ($f_2 = 0$), they move purely horizontally. Nullclines therefore divide phase space into regions where the signs of $x'$ and $y'$ are constant, letting us sketch flow direction without computing trajectories.

Q: What is the recommended workflow for sketching a 2D nonlinear phase portrait?
A: First find equilibria by solving $\vec{f} = \vec{0}$. Second, compute the Jacobian at each equilibrium and classify it. Third, draw the nullclines $f_1 = 0$ and $f_2 = 0$ to partition the plane. Fourth, determine the sign of $x'$ and $y'$ in each region to find flow direction. Finally, connect local pictures near each equilibrium with the global flow to sketch trajectories.

C: Near an equilibrium, draw a local phase portrait matching its classification; far from equilibria, use [nullclines] and sign analysis to determine global flow direction.

## 14.17 Bifurcations (Brief)

C: A [bifurcation] is a qualitative change in the phase portrait (number or stability of equilibria, appearance of limit cycles) as a parameter varies continuously.

Q: Why do bifurcations matter in applied dynamics?
A: Real systems depend on parameters (temperature, input current, population growth rate), and qualitative changes — sudden appearance of oscillations, loss of stable equilibria, hysteresis — often signal catastrophic transitions: neuron firing onset, laser threshold, ecosystem collapse. Detecting parameter values where bifurcations occur predicts where behavior changes drastically.

C: A [saddle-node] bifurcation: two equilibria (one stable, one unstable) collide and annihilate as a parameter passes a critical value.

C: A [transcritical] bifurcation: two equilibria exchange stability as they cross each other when a parameter varies.

C: A [pitchfork] bifurcation: one equilibrium splits into three (or three merge into one), often associated with symmetry breaking.

C: A [Hopf] bifurcation: a stable equilibrium loses stability and a limit cycle is born (or dies) as a pair of complex eigenvalues crosses the imaginary axis.

Q: Why is the Hopf bifurcation the standard mechanism for the onset of oscillation in nonlinear systems?
A: It directly connects an equilibrium-dominated regime (complex eigenvalues with negative real part: stable spiral) to an oscillatory regime (limit cycle) as parameters vary. The moment eigenvalues cross into the right half plane, the equilibrium destabilizes and, generically, a nearby limit cycle appears. It explains laser thresholds, cardiac oscillations, and chemical clocks.

## 14.18 Worked Example — The Pendulum

P: The undamped pendulum satisfies $\theta'' + \sin\theta = 0$, where $\theta$ is the angular displacement from the downward vertical. Rewrite as a first-order system, find and classify all equilibria in the strip $-\pi < \theta \le \pi$.

S:
**IDENTIFY**: Convert a 2nd-order autonomous ODE to a 2D first-order system, find equilibria, linearize, classify via Jacobian eigenvalues. Watch for non-hyperbolic cases.

**PLAN**:
- Let $x_1 = \theta$ and $x_2 = \theta'$.
- Write $x_1' = x_2$, $x_2' = -\sin x_1$.
- Find equilibria by setting both right-hand sides to zero.
- Compute the Jacobian, evaluate at each equilibrium, and classify.

**EXECUTE**:
1. First-order system: $x_1' = x_2$, $x_2' = -\sin x_1$.
2. Equilibria: $x_2 = 0$ and $\sin x_1 = 0$, giving $x_1 = 0$ or $x_1 = \pi$ in the chosen strip. Equilibria: $(0, 0)$ (pendulum hanging down at rest) and $(\pi, 0)$ (pendulum balanced inverted).
3. Jacobian: $J(x_1, x_2) = \begin{pmatrix} 0 & 1 \\ -\cos x_1 & 0 \end{pmatrix}$.
4. At $(0, 0)$: $J = \begin{pmatrix} 0 & 1 \\ -1 & 0 \end{pmatrix}$. Eigenvalues: $\det(J - \lambda I) = \lambda^2 + 1 = 0 \Rightarrow \lambda = \pm i$. Linearization predicts a center.
5. At $(\pi, 0)$: $J = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}$. Eigenvalues: $\lambda^2 - 1 = 0 \Rightarrow \lambda = \pm 1$. Opposite-sign real eigenvalues ⟹ saddle.

**EVALUATE**:
- $(\pi, 0)$ is a saddle (hyperbolic): Hartman-Grobman applies, so the nonlinear equilibrium is also a saddle. Physically: the inverted pendulum is unstable, as expected.
- $(0, 0)$ has pure imaginary eigenvalues — non-hyperbolic — so linearization is inconclusive. However, the total energy $E(x_1, x_2) = \tfrac{1}{2}x_2^2 + (1 - \cos x_1)$ satisfies $\dot E = x_2 \cdot x_2' + \sin(x_1) \cdot x_1' = -x_2 \sin x_1 + x_2 \sin x_1 = 0$. Thus $E$ is conserved; near $(0,0)$ it is positive definite, so level sets are closed curves and $(0,0)$ is a genuine nonlinear center. The pendulum at rest is stable but not asymptotically stable (no damping).
- Consistent with physical intuition: the hanging pendulum oscillates forever (center); the inverted pendulum topples on the slightest push (saddle).
