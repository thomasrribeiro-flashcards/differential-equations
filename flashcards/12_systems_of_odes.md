+++
order = 12
tags = ["math", "differential-equations", "ode", "systems", "eigenvalue-method", "phase-portrait", "matrix-exponential"]
+++

# Differential Equations — Systems of Linear ODEs

## 12.1 Why Study Systems

Q: Why do we study systems of ODEs rather than just scalar ODEs?
A: Many natural phenomena involve several quantities that evolve together and influence one another — predator-prey populations, coupled mechanical oscillators, and circuits with multiple loops are all inherently multi-variable. A single scalar ODE cannot capture this coupling, so we need systems in which each equation describes one variable but references the others. Systems also provide a unified framework: any higher-order scalar ODE can be recast as a first-order system, making linear algebra available as a solution tool.

C: A system of ODEs is the natural model whenever two or more quantities evolve through [coupled dynamics].

Q: Give three physical situations that naturally give rise to a system of ODEs.
A: Predator-prey interactions (rabbit and fox populations influence each other's growth), coupled oscillators (two masses connected by springs exchange energy), and electrical circuits with multiple loops (currents in different loops satisfy coupled Kirchhoff equations).

C: Any $n$-th order scalar linear ODE can be rewritten as an equivalent [first-order system] in $n$ unknowns.

## 12.2 Converting Higher-Order ODEs to First-Order Systems

Q: Why is it useful to rewrite a higher-order scalar ODE as a first-order system?
A: First-order systems have a uniform matrix form $\vec{x}' = A\vec{x}$ that lets us apply linear algebra (eigenvalues, eigenvectors, matrix exponentials). This unifies the theory: every scalar higher-order problem becomes a special case of the vector first-order problem, and the same existence, uniqueness, and structure theorems apply.

C: To convert an $n$-th order ODE into a first-order system, define $x_1 = y$, $x_2 = y'$, $\ldots$, $x_n = [y^{(n-1)}]$, where $y$ is the original unknown function.

C: After the substitution $x_1 = y, x_2 = y', \ldots, x_n = y^{(n-1)}$, the relation $x_k' = x_{k+1}$ holds for $k = 1, \ldots, [n-1]$.

P: Convert the second-order ODE $y'' + 3y' + 2y = 0$ into a first-order system.

S:
**IDENTIFY**: Higher-order-to-system conversion of a linear ODE, where $y$ is the unknown scalar function of $t$.

**PLAN**:
- Introduce $x_1 = y$ and $x_2 = y'$ so the system has one component per derivative order.
- Write $x_1'$ and $x_2'$ each as a linear combination of $x_1, x_2$.

**EXECUTE**:
1. $x_1' = y' = x_2$.
2. From the ODE, $y'' = -3y' - 2y = -3x_2 - 2x_1$, so $x_2' = -2x_1 - 3x_2$.
3. In matrix form: $\vec{x}' = \begin{pmatrix}0 & 1\\ -2 & -3\end{pmatrix}\vec{x}$, where $\vec{x} = (x_1, x_2)^T$.

**EVALUATE**: The $2\times 2$ coefficient matrix has the characteristic form of a companion matrix, and its characteristic polynomial $\lambda^2 + 3\lambda + 2$ matches the original ODE, confirming the conversion is correct.

## 12.3 The Linear System $\vec{x}' = A\vec{x}$

C: The standard form of a homogeneous linear first-order system is $[\vec{x}' = A\vec{x}]$, where $\vec{x}(t) \in \mathbb{R}^n$ is the unknown vector function and $A$ is an $n\times n$ constant matrix.

C: In the system $\vec{x}' = A\vec{x}$, the matrix $A$ is called the [coefficient matrix], and its entries encode how each component of $\vec{x}$ contributes to the derivatives of every component.

Q: What makes the system $\vec{x}' = A\vec{x}$ "linear" and "homogeneous"?
A: Linear means each $x_i'$ is a linear combination of $x_1, \ldots, x_n$ with no products or nonlinear functions of the unknowns. Homogeneous means there is no forcing term — the right-hand side vanishes when $\vec{x} = \vec{0}$, so $\vec{x}(t) \equiv \vec{0}$ is always a solution.

## 12.4 Superposition for Systems

Q: Why does superposition hold for solutions of $\vec{x}' = A\vec{x}$?
A: The system is linear, so the map $L[\vec{x}] = \vec{x}' - A\vec{x}$ is a linear operator on vector-valued functions. If $L[\vec{x}_1] = 0$ and $L[\vec{x}_2] = 0$, then for any constants $c_1, c_2$ we have $L[c_1\vec{x}_1 + c_2\vec{x}_2] = c_1 L[\vec{x}_1] + c_2 L[\vec{x}_2] = 0$. Thus linear combinations of solutions are again solutions.

C: If $\vec{x}_1(t)$ and $\vec{x}_2(t)$ solve $\vec{x}' = A\vec{x}$, then any linear combination $c_1\vec{x}_1 + c_2\vec{x}_2$ is also a [solution].

C: The set of all solutions of the $n$-dimensional homogeneous system $\vec{x}' = A\vec{x}$ forms a vector space of dimension [$n$].

## 12.5 The Fundamental Matrix

Q: What is a fundamental matrix for the system $\vec{x}' = A\vec{x}$, and why is it useful?
A: A fundamental matrix $\Phi(t)$ is an $n\times n$ matrix whose columns are $n$ linearly independent solutions of the system. It is useful because every solution can be written as $\vec{x}(t) = \Phi(t)\vec{c}$ for some constant vector $\vec{c} \in \mathbb{R}^n$, so $\Phi(t)$ packages the general solution into a single object usable in formulas like variation of parameters.

C: A [fundamental matrix] $\Phi(t)$ is an $n\times n$ matrix whose columns are $n$ linearly independent solutions of $\vec{x}' = A\vec{x}$.

C: Given a fundamental matrix $\Phi(t)$, the general solution of $\vec{x}' = A\vec{x}$ is $\vec{x}(t) = [\Phi(t)\vec{c}]$, where $\vec{c} \in \mathbb{R}^n$ is an arbitrary constant vector.

Q: How can you check that a candidate matrix $\Phi(t)$ really is a fundamental matrix?
A: Two conditions must hold: first, $\Phi'(t) = A\Phi(t)$, meaning every column solves the system; second, $\det\Phi(t_0) \neq 0$ at some point $t_0$, which guarantees the columns are linearly independent (and therefore independent for all $t$ by Abel's theorem).

## 12.6 The Eigenvalue Method

Q: Before deriving it, predict: what simple form should we try for a solution to $\vec{x}' = A\vec{x}$ by analogy with the scalar equation $x' = ax$?
A: The scalar equation has solution $x(t) = e^{at}x_0$, so we guess $\vec{x}(t) = e^{\lambda t}\vec{v}$ for some scalar $\lambda$ and constant vector $\vec{v}$. Substituting should turn the differential equation into an algebraic condition on $\lambda$ and $\vec{v}$.

Q: Derive the eigenvalue condition by substituting $\vec{x}(t) = e^{\lambda t}\vec{v}$ into $\vec{x}' = A\vec{x}$.
A: Differentiating gives $\vec{x}'(t) = \lambda e^{\lambda t}\vec{v}$. The right-hand side is $A\vec{x} = e^{\lambda t}A\vec{v}$. Equating and dividing by $e^{\lambda t} \neq 0$ yields $\lambda\vec{v} = A\vec{v}$, which is precisely the eigenvalue-eigenvector equation. Thus $\lambda$ must be an eigenvalue of $A$ and $\vec{v}$ a corresponding eigenvector.

C: Trying $\vec{x}(t) = e^{\lambda t}\vec{v}$ in $\vec{x}' = A\vec{x}$ produces the algebraic condition $A\vec{v} = [\lambda\vec{v}]$, where $\lambda$ is a scalar eigenvalue and $\vec{v} \neq 0$ is the associated eigenvector.

C: Each eigenvalue $\lambda$ of $A$ with eigenvector $\vec{v}$ yields the solution $[\vec{x}(t) = e^{\lambda t}\vec{v}]$ of $\vec{x}' = A\vec{x}$.

## 12.7 General Solution — Distinct Real Eigenvalues

Q: If the $n\times n$ matrix $A$ has $n$ distinct real eigenvalues, why does the eigenvalue method produce the full general solution?
A: Distinct eigenvalues have linearly independent eigenvectors, so the $n$ solutions $e^{\lambda_i t}\vec{v}_i$ are linearly independent. Their linear span therefore has dimension $n$, matching the dimension of the solution space of the system, so every solution is a linear combination of them.

C: If $A$ has $n$ distinct real eigenvalues $\lambda_1, \ldots, \lambda_n$ with eigenvectors $\vec{v}_1, \ldots, \vec{v}_n$, then the general solution of $\vec{x}' = A\vec{x}$ is $[\vec{x}(t) = \sum_{i=1}^n c_i e^{\lambda_i t}\vec{v}_i]$, where $c_1, \ldots, c_n$ are arbitrary constants.

Q: After writing the general solution as $\vec{x}(t) = \sum c_i e^{\lambda_i t}\vec{v}_i$, how do you determine the $c_i$ from an initial condition $\vec{x}(0) = \vec{x}_0$?
A: Set $t = 0$ to get $\vec{x}_0 = \sum c_i\vec{v}_i$, which is a linear system for $c_1, \ldots, c_n$. Equivalently, if $P = [\vec{v}_1 | \cdots | \vec{v}_n]$ is the matrix of eigenvectors, then $\vec{c} = P^{-1}\vec{x}_0$.

## 12.8 Complex Eigenvalues

Q: Why do complex eigenvalues of a real matrix $A$ always come in conjugate pairs?
A: The characteristic polynomial $\det(A - \lambda I)$ has real coefficients, so its nonreal roots occur in complex-conjugate pairs. Moreover, if $\vec{v}$ is an eigenvector for $\lambda = \alpha + \beta i$, then $\overline{\vec{v}}$ is an eigenvector for $\bar{\lambda} = \alpha - \beta i$, so complex eigenvectors also come in conjugate pairs.

C: For a real matrix $A$ with complex eigenvalue $\lambda = \alpha + \beta i$ and eigenvector $\vec{v} = \vec{a} + i\vec{b}$, the conjugate $\bar{\lambda} = [\alpha - \beta i]$ is also an eigenvalue, with eigenvector $\overline{\vec{v}}$.

Q: How do you extract two real solutions from the complex solution $e^{(\alpha+\beta i)t}(\vec{a} + i\vec{b})$?
A: Expand using Euler's formula: $e^{(\alpha+\beta i)t}(\vec{a}+i\vec{b}) = e^{\alpha t}(\cos\beta t + i\sin\beta t)(\vec{a}+i\vec{b})$. The real and imaginary parts of this expression are each real solutions of $\vec{x}' = A\vec{x}$ and are linearly independent. Here $\alpha$ is the real part of the eigenvalue, $\beta$ the imaginary part, and $\vec{a}, \vec{b}$ are the real and imaginary parts of the eigenvector.

C: With $\lambda = \alpha + \beta i$ and eigenvector $\vec{v} = \vec{a} + i\vec{b}$, the first real solution is $[e^{\alpha t}(\vec{a}\cos\beta t - \vec{b}\sin\beta t)]$, where $\vec{a}, \vec{b}$ are the real and imaginary parts of $\vec{v}$.

C: With $\lambda = \alpha + \beta i$ and eigenvector $\vec{v} = \vec{a} + i\vec{b}$, the second real solution is $[e^{\alpha t}(\vec{a}\sin\beta t + \vec{b}\cos\beta t)]$.

Q: In a solution built from complex eigenvalues $\alpha \pm \beta i$, what do $\alpha$ and $\beta$ each control?
A: $\alpha$ controls the exponential growth ($\alpha > 0$) or decay ($\alpha < 0$) envelope of the trajectory, while $\beta$ controls the angular frequency of rotation in the phase plane. Together they produce spirals (if $\alpha \neq 0$) or closed ellipses (if $\alpha = 0$).

## 12.9 Repeated Eigenvalue with Full Eigenspace

Q: If $\lambda$ is a repeated eigenvalue of $A$ whose eigenspace has dimension equal to its algebraic multiplicity, how do you build the solutions?
A: In this "nondefective" case the eigenspace already supplies enough linearly independent eigenvectors $\vec{v}_1, \ldots, \vec{v}_k$. Each gives a solution $e^{\lambda t}\vec{v}_i$, and these are linearly independent. No generalized eigenvectors are needed, and the method is essentially the same as for distinct eigenvalues.

C: When a repeated eigenvalue has a full eigenspace (geometric multiplicity equal to algebraic multiplicity), the solutions are simply $e^{\lambda t}\vec{v}_i$, one for each [linearly independent eigenvector] $\vec{v}_i$.

## 12.10 Defective Case — Generalized Eigenvectors

Q: What does it mean for a repeated eigenvalue to be "defective," and why is it a problem?
A: An eigenvalue is defective when its geometric multiplicity (dimension of the eigenspace) is strictly less than its algebraic multiplicity (how many times it appears as a root of the characteristic polynomial). Then there are not enough eigenvectors to build $n$ independent solutions by the eigenvalue method alone, so we need a new construction — generalized eigenvectors.

C: A generalized eigenvector $\vec{w}$ associated with eigenvalue $\lambda$ and eigenvector $\vec{v}$ satisfies the equation $(A - \lambda I)\vec{w} = [\vec{v}]$.

Q: Why does the defective case produce a solution of the form $(t\vec{v} + \vec{w})e^{\lambda t}$?
A: Guess $\vec{x}(t) = (t\vec{v} + \vec{w})e^{\lambda t}$. Differentiating gives $\vec{x}' = \vec{v}e^{\lambda t} + \lambda(t\vec{v}+\vec{w})e^{\lambda t}$. Requiring $\vec{x}' = A\vec{x}$ leads to $(A-\lambda I)\vec{v} = 0$ (so $\vec{v}$ is an eigenvector) and $(A-\lambda I)\vec{w} = \vec{v}$ (so $\vec{w}$ is a generalized eigenvector). The factor of $t$ is exactly what compensates for the missing second eigenvector.

C: For a defective eigenvalue $\lambda$ of multiplicity 2 with eigenvector $\vec{v}$ and generalized eigenvector $\vec{w}$, the two independent solutions are $e^{\lambda t}\vec{v}$ and $[(t\vec{v} + \vec{w})e^{\lambda t}]$.

## 12.11 Phase Portraits

Q: What is a phase portrait of a 2D linear system, and what does it show?
A: A phase portrait is a sketch in the $x_1 x_2$-plane showing representative trajectories of $\vec{x}' = A\vec{x}$. Each trajectory is the curve traced by $\vec{x}(t)$ as $t$ varies, with arrows indicating the direction of increasing time. It shows qualitative long-term behavior — whether solutions spiral, decay to the origin, run off to infinity, or orbit periodically — without requiring an explicit formula.

C: At each point $\vec{x}$ in the phase plane, the tangent direction of the trajectory is given by the vector $[A\vec{x}]$, which equals $\vec{x}'(t)$.

Q: Why are eigenvectors special in a phase portrait?
A: Along an eigenvector direction, $A\vec{x} = \lambda\vec{x}$ is parallel to $\vec{x}$ itself, so trajectories starting on that line stay on that line. The eigenvectors form invariant "straight-line" trajectories through the origin, and they skeleton the rest of the portrait — neighboring trajectories bend toward or away from them depending on the sign of $\lambda$.

## 12.12 Classification of 2D Linear Systems

Q: Why does the eigenvalue structure of a $2\times 2$ matrix $A$ determine the qualitative shape of the phase portrait?
A: The general solution is a combination of exponentials in the eigenvalues times (generalized) eigenvectors, and exponentials' growth/decay and oscillation depend entirely on whether eigenvalues are real or complex and on the signs of their real parts. These features — sign, reality, and any imaginary component — are exactly the data needed to classify trajectories near the origin.

C: Two real eigenvalues with the same sign (both negative) give a [stable node], where every trajectory approaches the origin as $t \to \infty$.

C: Two real eigenvalues with the same sign (both positive) give an [unstable node], where every trajectory leaves the origin as $t \to \infty$.

C: Two real eigenvalues of opposite sign give a [saddle point], which is always unstable because trajectories in the positive-eigenvalue direction move away from the origin.

C: Complex eigenvalues $\alpha \pm \beta i$ with $\alpha < 0$ give a [stable spiral], where trajectories spiral inward to the origin.

C: Complex eigenvalues $\alpha \pm \beta i$ with $\alpha > 0$ give an [unstable spiral], where trajectories spiral outward from the origin.

C: Complex eigenvalues $\alpha \pm \beta i$ with $\alpha = 0$ give a [center], consisting of closed elliptical orbits around the origin.

Q: Why is a saddle always unstable, even when one eigenvalue is negative?
A: A saddle has eigenvalues of opposite sign. The negative-eigenvalue direction attracts trajectories, but the positive-eigenvalue direction repels them. Unless the initial condition lies exactly on the stable (negative-eigenvalue) eigenvector, the positive component grows exponentially and drives the trajectory to infinity. A single expanding direction is enough to destroy stability.

Q: What distinguishes a center from a spiral?
A: Both arise from complex eigenvalues $\alpha \pm \beta i$, but a center has $\alpha = 0$ while a spiral has $\alpha \neq 0$. With $\alpha = 0$ the exponential envelope $e^{\alpha t} = 1$ is constant, so trajectories form closed ellipses around the origin. With $\alpha \neq 0$ the envelope grows ($\alpha>0$) or decays ($\alpha<0$), producing outward or inward spirals.

## 12.13 Stability Summary

Q: What is the necessary and sufficient condition for the origin to be asymptotically stable for $\vec{x}' = A\vec{x}$?
A: Every eigenvalue of $A$ must have strictly negative real part. Each solution is a combination of $e^{\lambda_i t}$-type terms, and each such term decays to zero iff $\text{Re}(\lambda_i) < 0$. If even one eigenvalue has nonnegative real part, some solutions fail to decay, and asymptotic stability fails.

C: The origin is asymptotically stable for $\vec{x}' = A\vec{x}$ if and only if every eigenvalue of $A$ has [negative real part].

C: If any eigenvalue of $A$ has positive real part, the origin is [unstable], because the corresponding solution mode grows exponentially in time.

Q: If $A$ has a purely imaginary pair of eigenvalues and no other eigenvalues with nonzero real part, is the origin asymptotically stable?
A: No. Asymptotic stability requires every eigenvalue to have strictly negative real part, but purely imaginary eigenvalues have real part zero. Trajectories neither decay nor grow — they orbit as closed curves (a center). The origin is stable in the sense of Lyapunov (trajectories stay bounded) but not asymptotically stable.

## 12.14 The Matrix Exponential

Q: Why define a matrix exponential $e^{At}$ for a square matrix $A$?
A: We want a closed-form solution of $\vec{x}' = A\vec{x}$ that mirrors the scalar formula $x(t) = e^{at}x_0$. Defining $e^{At}$ so that $\frac{d}{dt}e^{At} = Ae^{At}$ and $e^{A\cdot 0} = I$ gives exactly this analogy: the unique solution of the initial value problem is $\vec{x}(t) = e^{At}\vec{x}_0$, where $\vec{x}_0 = \vec{x}(0)$.

C: The matrix exponential $e^{At}$ is defined by the series $\sum_{k=0}^{\infty}\frac{(At)^k}{k!}$, so that $e^{A\cdot 0} = [I]$, the identity matrix.

C: The matrix exponential satisfies the differential equation $\frac{d}{dt}e^{At} = [Ae^{At}]$, making it a fundamental matrix that equals $I$ at $t = 0$.

C: The unique solution of the initial value problem $\vec{x}' = A\vec{x}$, $\vec{x}(0) = \vec{x}_0$ is $[\vec{x}(t) = e^{At}\vec{x}_0]$, where $\vec{x}_0$ is the initial vector.

Q: How is $e^{At}$ related to an arbitrary fundamental matrix $\Phi(t)$?
A: Every fundamental matrix satisfies $\Phi'(t) = A\Phi(t)$, but $e^{At}$ is the specific fundamental matrix normalized by $e^{A\cdot 0} = I$. Given any fundamental matrix $\Phi(t)$, one can recover $e^{At} = \Phi(t)\Phi(0)^{-1}$. So the matrix exponential is the "canonical" fundamental matrix, with initial value the identity.

## 12.15 Computing $e^{At}$ via Diagonalization

Q: Why does diagonalization make $e^{At}$ easy to compute?
A: If $A = PDP^{-1}$ with $D$ diagonal, then $A^k = PD^kP^{-1}$, and substituting into the series for $e^{At}$ gives $e^{At} = Pe^{Dt}P^{-1}$. The matrix $e^{Dt}$ is diagonal with entries $e^{\lambda_i t}$, which requires no work to compute — so the hard part reduces to finding eigenvalues, eigenvectors, and a matrix inverse.

C: If $A = PDP^{-1}$ where $D$ is diagonal with eigenvalues on the diagonal and $P$ has the corresponding eigenvectors as columns, then $e^{At} = [Pe^{Dt}P^{-1}]$.

C: For a diagonal matrix $D = \text{diag}(\lambda_1, \ldots, \lambda_n)$, the exponential $e^{Dt}$ is the diagonal matrix with entries $[e^{\lambda_i t}]$ on the diagonal.

Q: What goes wrong with $e^{At} = Pe^{Dt}P^{-1}$ when $A$ is defective?
A: Defective matrices are not diagonalizable, so no factorization $A = PDP^{-1}$ with $D$ diagonal exists. The formula fails because $P$ does not have $n$ linearly independent eigenvector columns. Instead one uses the Jordan form $A = PJP^{-1}$ (with Jordan blocks) and computes $e^{Jt}$ block by block, or builds $e^{At}$ directly from generalized eigenvectors.

## 12.16 Nonhomogeneous Systems and Variation of Parameters

Q: What is the structure of the general solution to the nonhomogeneous system $\vec{x}' = A\vec{x} + \vec{g}(t)$?
A: It has the form $\vec{x}(t) = \vec{x}_h(t) + \vec{x}_p(t)$, where $\vec{x}_h$ is the general solution of the homogeneous system $\vec{x}' = A\vec{x}$ and $\vec{x}_p$ is any particular solution of the nonhomogeneous system. The homogeneous part captures the free dynamics, and $\vec{x}_p$ accounts for the forcing $\vec{g}(t)$, which is a given vector-valued function of $t$.

Q: Before deriving variation of parameters for systems, predict the form of the particular solution by analogy with the scalar case $x' = ax + g(t)$.
A: The scalar solution is $x(t) = e^{at}x_0 + \int_{t_0}^t e^{a(t-s)}g(s)\,ds$. By analogy we expect a matrix version: $\vec{x}(t) = e^{A(t-t_0)}\vec{x}_0 + \int_{t_0}^t e^{A(t-s)}\vec{g}(s)\,ds$, or equivalently in terms of a fundamental matrix $\Phi$, one involving $\Phi(t)\Phi^{-1}(s)$.

C: Using a fundamental matrix $\Phi(t)$ of $\vec{x}' = A\vec{x}$, the variation-of-parameters solution to $\vec{x}' = A\vec{x} + \vec{g}(t)$ with $\vec{x}(t_0) = \vec{x}_0$ is $\vec{x}(t) = [\Phi(t)\Phi^{-1}(t_0)\vec{x}_0 + \Phi(t)\int_{t_0}^t \Phi^{-1}(s)\vec{g}(s)\,ds]$, where $\vec{g}(t)$ is the forcing term.

Q: Why does the variation-of-parameters integrand involve $\Phi^{-1}(s)\vec{g}(s)$ rather than just $\vec{g}(s)$?
A: The trick is to seek $\vec{x}_p(t) = \Phi(t)\vec{u}(t)$ with $\vec{u}$ unknown. Substituting into the system, the homogeneous terms cancel and you get $\Phi(t)\vec{u}'(t) = \vec{g}(t)$, so $\vec{u}'(t) = \Phi^{-1}(t)\vec{g}(t)$. Integrating gives $\vec{u}(t) = \int \Phi^{-1}(s)\vec{g}(s)\,ds$, and multiplying back by $\Phi(t)$ produces the formula. The inverse $\Phi^{-1}$ appears because it undoes the fundamental matrix before integration.

## 12.17 Worked Problems

P: Solve the system $\vec{x}' = \begin{pmatrix}2 & 1\\ -1 & 2\end{pmatrix}\vec{x}$ with initial condition $\vec{x}(0) = (1, 0)^T$, and identify the type of phase portrait.

S:
**IDENTIFY**: Initial value problem for a $2\times 2$ linear system with constant coefficient matrix $A$; we expect complex eigenvalues from the structure of $A$ (nonzero off-diagonal with opposite signs and equal diagonal entries), which will give a spiral or center.

**PLAN**:
- Compute eigenvalues of $A$ from $\det(A - \lambda I) = 0$.
- Find a complex eigenvector $\vec{v} = \vec{a} + i\vec{b}$ for $\lambda = \alpha + \beta i$.
- Build the two real solutions $e^{\alpha t}(\vec{a}\cos\beta t - \vec{b}\sin\beta t)$ and $e^{\alpha t}(\vec{a}\sin\beta t + \vec{b}\cos\beta t)$.
- Apply $\vec{x}(0) = (1,0)^T$ to determine the coefficients.
- Classify the portrait from the sign of $\alpha$.

**EXECUTE**:
1. Characteristic polynomial: $\det\begin{pmatrix}2-\lambda & 1\\ -1 & 2-\lambda\end{pmatrix} = (2-\lambda)^2 + 1 = 0$, so $(2-\lambda)^2 = -1$ and $\lambda = 2 \pm i$. Thus $\alpha = 2$, $\beta = 1$.
2. Eigenvector for $\lambda = 2 + i$: $(A - (2+i)I)\vec{v} = \begin{pmatrix}-i & 1\\ -1 & -i\end{pmatrix}\vec{v} = 0$. Take $\vec{v} = (1, i)^T$, so $\vec{a} = (1,0)^T$ and $\vec{b} = (0,1)^T$.
3. Real solutions:
   - $\vec{x}_1(t) = e^{2t}(\vec{a}\cos t - \vec{b}\sin t) = e^{2t}(\cos t, -\sin t)^T$.
   - $\vec{x}_2(t) = e^{2t}(\vec{a}\sin t + \vec{b}\cos t) = e^{2t}(\sin t, \cos t)^T$.
4. General solution: $\vec{x}(t) = c_1 e^{2t}(\cos t, -\sin t)^T + c_2 e^{2t}(\sin t, \cos t)^T$.
5. Apply $\vec{x}(0) = (1, 0)^T$: $(c_1, -0 + c_2)^T \cdot 1 = (c_1, c_2)^T = (1, 0)^T$, so $c_1 = 1$, $c_2 = 0$.
6. Solution: $\vec{x}(t) = e^{2t}(\cos t, -\sin t)^T$.
7. Classification: complex eigenvalues $2 \pm i$ with $\alpha = 2 > 0$ give an **unstable spiral**.

**EVALUATE**: Check $\vec{x}(0) = (1, 0)^T$. Differentiate: $\vec{x}'(t) = e^{2t}(2\cos t - \sin t, -2\sin t - \cos t)^T$. Compute $A\vec{x}(t) = e^{2t}(2\cos t - \sin t, -\cos t - 2\sin t)^T$, which matches $\vec{x}'(t)$. The trajectory starts at $(1,0)$, rotates, and grows in magnitude like $e^{2t}$, consistent with an outward spiral.

P: Classify the system $\vec{x}' = \begin{pmatrix}-1 & 2\\ 0 & -3\end{pmatrix}\vec{x}$ and describe its phase portrait.

S:
**IDENTIFY**: Qualitative analysis of a $2\times 2$ linear system; the matrix is upper-triangular, so eigenvalues can be read off the diagonal, which will determine the classification.

**PLAN**:
- Read eigenvalues directly from the diagonal of the triangular matrix.
- Find eigenvectors for each eigenvalue.
- Apply the classification rules for real eigenvalues of the same sign.
- Sketch trajectories along eigenvector directions and between them.

**EXECUTE**:
1. Eigenvalues: diagonal entries of an upper-triangular matrix, so $\lambda_1 = -1$ and $\lambda_2 = -3$. Both are real, distinct, and negative.
2. Classification: real distinct eigenvalues of the same (negative) sign $\Rightarrow$ **stable node**. The origin is asymptotically stable.
3. Eigenvector for $\lambda_1 = -1$: $(A + I)\vec{v}_1 = \begin{pmatrix}0 & 2\\ 0 & -2\end{pmatrix}\vec{v}_1 = 0$ gives $\vec{v}_1 = (1, 0)^T$.
4. Eigenvector for $\lambda_2 = -3$: $(A + 3I)\vec{v}_2 = \begin{pmatrix}2 & 2\\ 0 & 0\end{pmatrix}\vec{v}_2 = 0$ gives $\vec{v}_2 = (1, -1)^T$.
5. Slow direction (smaller $|\lambda|$): $\vec{v}_1 = (1,0)^T$ decays like $e^{-t}$. Fast direction (larger $|\lambda|$): $\vec{v}_2 = (1,-1)^T$ decays like $e^{-3t}$.
6. Phase portrait: trajectories approach the origin, aligning tangent to the slow eigenvector $(1,0)^T$ as $t\to\infty$ (since the fast component decays more quickly), and emerging from the slow direction going backward in time.

**EVALUATE**: Both eigenvalues negative $\Rightarrow$ stable node, not a spiral (eigenvalues real) and not a saddle (same sign). Far from the origin, trajectories are dominated by the fast mode $e^{-3t}\vec{v}_2$; close to the origin, they are tangent to the slow mode $\vec{v}_1$. This matches the standard picture of a stable node with two distinct real rates.
