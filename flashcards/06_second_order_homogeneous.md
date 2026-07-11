+++
order = 6
subject = "mathematics"
tags = ["math", "differential-equations", "ode", "second-order", "characteristic-equation", "homogeneous", "wronskian"]
+++

# Differential Equations — Second-Order Linear Homogeneous Equations

## 6.1 General Second-Order Linear ODE

Q: Why do we study second-order linear ODEs as a distinct class, rather than treating them as a special case of higher-order equations?
A: Second-order linear ODEs are the minimum order needed to model oscillation and most classical physical systems (springs, circuits, mechanics via Newton's second law). They are rich enough to exhibit the full structure of linear theory (fundamental sets, Wronskians, superposition) yet tractable enough to solve explicitly in many important cases. Higher-order linear theory is a direct generalization, so mastering order 2 gives nearly all the conceptual machinery.

C: A general second-order linear ODE has the form $a(x)y'' + b(x)y' + c(x)y = g(x)$, where $y = y(x)$ is the unknown function, $a, b, c$ are [coefficient functions] of $x$, and $g(x)$ is the forcing term.

C: A second-order linear ODE $a(x)y'' + b(x)y' + c(x)y = g(x)$ is called [homogeneous] when $g(x) = 0$ for all $x$ in the interval of interest.

Q: What distinguishes a linear ODE from a nonlinear one?
A: A linear ODE has the unknown $y$ and its derivatives appearing only to the first power and never multiplied together or composed with nonlinear functions. Thus $yy''$, $(y')^2$, and $\sin(y)$ are forbidden, but $x^2 y''$ and $e^x y'$ are allowed because the coefficients depend only on $x$.

## 6.2 Linearity Principle and Superposition

Q: Before seeing the proof, predict: if $y_1$ and $y_2$ both solve a homogeneous linear ODE, what do you expect about the function $3y_1 - 7y_2$?
A: It should also be a solution. Linear operations (scaling, adding) preserve membership in the solution set of a homogeneous linear equation — this is the defining property of linearity.

Q: State the superposition principle for second-order linear homogeneous ODEs.
A: If $y_1(x)$ and $y_2(x)$ are both solutions of $a(x)y'' + b(x)y' + c(x)y = 0$, then every linear combination $y = c_1 y_1 + c_2 y_2$ with constants $c_1, c_2 \in \mathbb{R}$ is also a solution. The solution set is a vector space.

Q: Why does the superposition principle hold for homogeneous linear ODEs?
A: Differentiation is a linear operation: $(c_1 y_1 + c_2 y_2)' = c_1 y_1' + c_2 y_2'$ and similarly for second derivatives. Substituting $c_1 y_1 + c_2 y_2$ into the left side of the ODE gives $c_1 \cdot (\text{LHS for } y_1) + c_2 \cdot (\text{LHS for } y_2) = c_1 \cdot 0 + c_2 \cdot 0 = 0$. The right-hand side being zero is essential — this fails for non-homogeneous equations.

C: The superposition principle fails when the equation is [non-homogeneous], because substituting $c_1 y_1 + c_2 y_2$ into $L\lbrack y\rbrack  = g(x)$ gives $c_1 g + c_2 g = (c_1 + c_2) g$, not $g$.

Q: Why does superposition fail for nonlinear ODEs, even homogeneous ones?
A: Nonlinear terms do not distribute over sums. For example, $(y_1 + y_2)^2 \neq y_1^2 + y_2^2$, so substituting a sum produces cross terms that the original solutions do not satisfy. Linearity is what makes the solution set closed under addition and scaling.

## 6.3 Linear Independence of Solutions

C: Two functions $y_1, y_2$ on an interval $I$ are [linearly independent] if the only constants $c_1, c_2$ satisfying $c_1 y_1(x) + c_2 y_2(x) = 0$ for all $x \in I$ are $c_1 = c_2 = 0$.

C: Two solutions $y_1, y_2$ of a second-order linear homogeneous ODE form a [fundamental set] on an interval $I$ if and only if they are linearly independent on $I$.

Q: Why do we need TWO linearly independent solutions to describe all solutions of a second-order linear homogeneous ODE?
A: The solution space is a vector space of dimension exactly 2 (provable from the existence-uniqueness theorem). A single solution $y_1$ only spans a 1-dimensional subspace via scalar multiples; we need a second direction, linearly independent of $y_1$, to span the full 2D space. With fewer than two independent solutions we cannot match arbitrary initial data.

Q: If $y_2 = k y_1$ for some constant $k$, why can't $\{y_1, y_2\}$ serve as a fundamental set?
A: The combination $c_1 y_1 + c_2 y_2 = (c_1 + k c_2) y_1$ is still just a scalar multiple of $y_1$, so it cannot represent solutions that move independently of $y_1$. We could never match initial conditions that require a shape not proportional to $y_1$.

## 6.4 The Wronskian

C: The [Wronskian] of two differentiable functions $y_1, y_2$ is defined as $W(y_1, y_2)(x) = y_1(x)\, y_2'(x) - y_2(x)\, y_1'(x)$.

Q: Why is the Wronskian useful for detecting linear independence of two solutions?
A: It encodes whether $y_1$ and $y_2$ are "going in the same direction" as functions. If one is a constant multiple of the other, then their values and derivatives are proportional, making the determinant vanish. A nonzero Wronskian certifies that the pair provides two genuinely independent directions in solution space.

C: For two solutions $y_1, y_2$ of a second-order linear homogeneous ODE with continuous coefficients, $y_1$ and $y_2$ are linearly independent on $I$ if and only if $W(y_1, y_2)(x_0) \neq 0$ at [some point $x_0 \in I$].

Q: For solutions of a second-order linear homogeneous ODE with continuous coefficients, why is it enough to check the Wronskian at a single point?
A: Abel's theorem shows the Wronskian of two solutions satisfies a first-order linear ODE, so it is either identically zero on the interval or never zero on the interval. Thus nonvanishing at one point implies nonvanishing everywhere, and we only need one "witness" point to certify linear independence.

Q: What is the matrix form of the Wronskian, and why is that view helpful?
A: $W(y_1, y_2) = \det \begin{pmatrix} y_1 & y_2 \\ y_1' & y_2' \end{pmatrix}$. Viewing it as a determinant makes the generalization to higher-order equations obvious — for order $n$, the Wronskian is the determinant of the $n \times n$ matrix of functions and their first $n-1$ derivatives.

## 6.5 General Solution of a Homogeneous Second-Order Linear ODE

C: If $\{y_1, y_2\}$ is a fundamental set of solutions of a second-order linear homogeneous ODE, the [general solution] is $y(x) = c_1 y_1(x) + c_2 y_2(x)$, where $c_1, c_2$ are arbitrary real constants.

Q: Why does $y = c_1 y_1 + c_2 y_2$ capture every solution of the homogeneous equation when $\{y_1, y_2\}$ is a fundamental set?
A: The solution space is 2-dimensional, and a linearly independent pair spans it. Any solution $y$ can therefore be written uniquely as a linear combination of $y_1$ and $y_2$ — the constants $c_1, c_2$ are determined by the initial conditions via a $2 \times 2$ system whose coefficient matrix has nonzero determinant (the Wronskian).

## 6.6 Existence and Uniqueness for Second-Order Linear IVPs

Q: State the existence-uniqueness theorem for the second-order linear initial value problem.
A: Consider $y'' + p(x)y' + q(x)y = g(x)$ with $y(x_0) = y_0$ and $y'(x_0) = y_0'$. If $p$, $q$, and $g$ are continuous on an open interval $I$ containing $x_0$, then there exists a unique solution defined on all of $I$. Unlike the nonlinear case, the solution is guaranteed on the full interval of continuity, not just locally.

Q: Why does the linear existence-uniqueness theorem give a solution on the entire interval of continuity, whereas the nonlinear version only guarantees a local solution?
A: Linear equations cannot "blow up" in finite time as long as their coefficients remain continuous — linearity bounds the growth rate of solutions in a way Grönwall-type arguments can control. Nonlinear equations can hit a vertical asymptote well before the coefficients misbehave, so only local existence is guaranteed there.

C: For the IVP $y'' + p(x)y' + q(x)y = g(x)$, $y(x_0)=y_0$, $y'(x_0)=y_0'$, if $p, q, g$ are continuous on an open interval $I \ni x_0$, the unique solution exists on [all of $I$].

## 6.7 Why Second-Order IVPs Need Two Initial Conditions

Q: Why does a second-order linear ODE require TWO initial conditions to pin down a unique solution?
A: The general solution contains two arbitrary constants $c_1, c_2$ (one from each "integration" intrinsic to a second-order equation). To solve for both constants we need two independent pieces of data. Specifying $y(x_0)$ and $y'(x_0)$ gives two equations in $c_1, c_2$, whose $2 \times 2$ system is solvable precisely because the Wronskian of the fundamental set is nonzero.

C: A second-order linear ODE's general solution has [two] arbitrary constants, so a well-posed IVP must supply two initial conditions, typically $y(x_0)$ and $y'(x_0)$.

Q: Geometrically, what do the two initial conditions $y(x_0) = y_0$ and $y'(x_0) = y_0'$ specify?
A: They specify a point $(x_0, y_0)$ that the solution curve must pass through and the slope $y_0'$ of the curve at that point. Together they fix both the position and direction of the solution at $x_0$, which is enough information to propagate a unique trajectory forward and backward in $x$.

## 6.8 Constant-Coefficient Homogeneous Equations

C: A [constant-coefficient] second-order linear homogeneous ODE has the form $ay'' + by' + cy = 0$, where $a, b, c \in \mathbb{R}$ are constants (with $a \neq 0$) and $y = y(x)$.

Q: Why do constant-coefficient linear ODEs admit exponential solutions?
A: For $ay'' + by' + cy = 0$ with constant coefficients, differentiating shifts by a factor but does not change functional form — exactly the property of $e^{rx}$, whose derivative is $r e^{rx}$. Substituting this ansatz reduces the differential equation to an algebraic equation in $r$, trading calculus for algebra.

## 6.9 The Characteristic Equation

Q: To solve $ay'' + by' + cy = 0$ with constant coefficients, predict what ansatz (guessed form) you would try, and why.
A: Try $y = e^{rx}$. Its derivatives are $re^{rx}$ and $r^2 e^{rx}$, so substitution factors out $e^{rx}$ and leaves a polynomial in $r$. This converts the ODE into an algebra problem.

C: Substituting $y = e^{rx}$ into $ay'' + by' + cy = 0$ yields the [characteristic equation] $ar^2 + br + c = 0$, whose roots determine the fundamental solutions.

Q: Derive the characteristic equation from $ay'' + by' + cy = 0$.
A: Let $y = e^{rx}$, so $y' = r e^{rx}$ and $y'' = r^2 e^{rx}$. Substituting gives $a r^2 e^{rx} + b r e^{rx} + c e^{rx} = 0$, or $(a r^2 + b r + c) e^{rx} = 0$. Because $e^{rx} \neq 0$, we need $a r^2 + b r + c = 0$, the characteristic (auxiliary) equation.

## 6.10 Case 1: Distinct Real Roots

C: If the characteristic equation $ar^2 + br + c = 0$ has two distinct real roots $r_1 \neq r_2$, the general solution of $ay'' + by' + cy = 0$ is $y(x) = [c_1 e^{r_1 x} + c_2 e^{r_2 x}]$, where $c_1, c_2$ are arbitrary constants.

Q: Why do $e^{r_1 x}$ and $e^{r_2 x}$ with $r_1 \neq r_2$ form a fundamental set?
A: Their Wronskian is $W = e^{r_1 x} \cdot r_2 e^{r_2 x} - e^{r_2 x} \cdot r_1 e^{r_1 x} = (r_2 - r_1) e^{(r_1 + r_2)x}$. Since $r_1 \neq r_2$, the factor $(r_2 - r_1) \neq 0$, and the exponential is never zero, so $W \neq 0$ everywhere. By the Wronskian criterion they are linearly independent.

## 6.11 Case 2: Repeated Real Root

C: If the characteristic equation has a repeated real root $r$, the general solution of $ay'' + by' + cy = 0$ is $y(x) = [c_1 e^{rx} + c_2 x e^{rx}]$.

Q: Why isn't $y = c_1 e^{rx} + c_2 e^{rx}$ the general solution when the characteristic equation has a repeated root $r$?
A: Because $c_1 e^{rx} + c_2 e^{rx} = (c_1 + c_2) e^{rx}$ collapses to a single arbitrary constant, spanning only a 1-dimensional subspace. We need a second, linearly independent solution to reach the full 2D solution space and match two initial conditions.

Q: Why does the extra factor of $x$ work in the repeated-root case — that is, why is $x e^{rx}$ a second solution?
A: When $r$ is a double root, $(D - r)^2[y] = 0$ where $D = d/dx$. Applying $(D - r)$ to $x e^{rx}$ gives $e^{rx}$, and applying it again gives $0$. So $x e^{rx}$ lies in the kernel of the operator. Equivalently, reduction of order with $y_2 = v(x) e^{rx}$ produces $v''(x) = 0$, forcing $v(x) = x$ (up to a constant absorbed by $c_2$).

Q: Why must the Wronskian criterion be checked in the repeated-root case?
A: To confirm that $e^{rx}$ and $x e^{rx}$ are linearly independent. Compute $W = e^{rx}(e^{rx} + r x e^{rx}) - x e^{rx}(r e^{rx}) = e^{2rx}$, which is nonzero everywhere. So they form a valid fundamental set.

## 6.12 Case 3: Complex Conjugate Roots

C: If the characteristic equation has complex conjugate roots $r = \alpha \pm \beta i$ with $\beta \neq 0$, the real-valued general solution is $y(x) = [e^{\alpha x}(c_1 \cos \beta x + c_2 \sin \beta x)]$, where $\alpha$ is the real part and $\beta$ is the (positive) imaginary part of the roots.

Q: Why do complex conjugate roots produce a real solution involving sines and cosines rather than complex exponentials?
A: Complex roots $\alpha \pm \beta i$ naively give $e^{(\alpha + \beta i)x}$ and $e^{(\alpha - \beta i)x}$ as fundamental solutions. Using Euler's formula $e^{i\theta} = \cos\theta + i\sin\theta$, these can be combined (as $\frac{1}{2}(\cdot + \cdot)$ and $\frac{1}{2i}(\cdot - \cdot)$) into the real-valued pair $e^{\alpha x} \cos \beta x$ and $e^{\alpha x} \sin \beta x$, which still span the same 2D solution space but give real solutions for real initial data.

Q: Derive the real-valued fundamental pair from complex conjugate characteristic roots $\alpha \pm \beta i$.
A: The complex solutions are $e^{(\alpha + \beta i)x} = e^{\alpha x}(\cos \beta x + i \sin \beta x)$ and $e^{(\alpha - \beta i)x} = e^{\alpha x}(\cos \beta x - i \sin \beta x)$. Taking their sum and difference (scaled by $1/2$ and $1/(2i)$) gives $e^{\alpha x} \cos \beta x$ and $e^{\alpha x} \sin \beta x$, respectively. Linear combinations of the complex pair equal linear combinations of the real pair, so we can use either as a fundamental set.

Q: In the complex-root solution $y = e^{\alpha x}(c_1 \cos \beta x + c_2 \sin \beta x)$, what physical roles do $\alpha$ and $\beta$ play?
A: $\alpha$ (the real part of the roots) controls the exponential envelope: $\alpha < 0$ gives decay, $\alpha = 0$ gives undamped oscillation, $\alpha > 0$ gives growth. $\beta$ (the imaginary part) is the angular frequency of oscillation, setting the period $2\pi / \beta$. This is the template for damped harmonic motion.

## 6.13 Discriminant Determines the Case

C: For $ay'' + by' + cy = 0$, the discriminant $\Delta = b^2 - 4ac$ determines the root structure: $\Delta > 0$ gives [two distinct real roots], $\Delta = 0$ gives a repeated real root, and $\Delta < 0$ gives complex conjugate roots.

Q: Why does the discriminant of the characteristic equation control which of the three solution cases applies?
A: The quadratic formula gives $r = \frac{-b \pm \sqrt{\Delta}}{2a}$, so the nature of $\sqrt{\Delta}$ determines the roots. A positive discriminant produces two distinct real square roots, zero produces a single repeated root, and negative produces an imaginary $\sqrt{\Delta}$, giving conjugate complex roots. Everything about the solution form flows from this one quantity.

## 6.14 Reduction of Order

Q: What problem does reduction of order solve?
A: Given one nonzero solution $y_1(x)$ of a second-order linear homogeneous ODE, it produces a second solution $y_2(x)$ linearly independent of $y_1$, so that $\{y_1, y_2\}$ forms a fundamental set. This is crucial when the equation has variable coefficients and we can guess or derive one solution but need the complete general solution.

C: In reduction of order, given one solution $y_1$ of a second-order linear homogeneous ODE, we seek a second solution of the form $y_2 = [v(x) y_1(x)]$ for some unknown function $v(x)$.

Q: Why does substituting $y_2 = v(x) y_1(x)$ into $y'' + p(x)y' + q(x)y = 0$ produce a first-order ODE in $v'$?
A: Substituting and using that $y_1$ satisfies the ODE causes the $v$-terms (those without derivatives) to cancel. What remains is a linear equation relating $v''$ and $v'$ only, with no $v$. Setting $w = v'$ converts this into a first-order linear equation in $w$, which can be solved by an integrating factor, and then $v = \int w\,dx$ recovers $y_2$.

Q: In the repeated-root case of $ay'' + by' + cy = 0$, how does reduction of order confirm that $y_2 = x e^{rx}$?
A: With $y_1 = e^{rx}$, set $y_2 = v(x) e^{rx}$. Substituting into $ay'' + by' + cy = 0$ and using $ar^2 + br + c = 0$ plus $2ar + b = 0$ (the double-root condition) collapses everything to $a v''(x) e^{rx} = 0$, so $v'' = 0$. Integrating gives $v(x) = C_1 + C_2 x$; dropping the $C_1$ term (absorbed into $y_1$) leaves $y_2 = x e^{rx}$.

## 6.15 Cauchy-Euler Equations

C: A [Cauchy-Euler] equation is a second-order linear ODE of the form $a x^2 y'' + b x y' + c y = 0$, where $a, b, c$ are constants and $x > 0$ (or $x < 0$).

Q: Why does the ansatz $y = x^r$ work for Cauchy-Euler equations?
A: In a Cauchy-Euler equation each term pairs a power of $x$ with the matching order of derivative: $x^2 y''$, $x y'$, $y$. Differentiating $x^r$ lowers the power by 1 each time but multiplies by $r$ (or $r(r-1)$), so every term in $a x^2 y'' + b x y' + c y$ becomes a constant multiple of $x^r$. Factoring $x^r$ leaves an algebraic equation in $r$ — the same strategy as $e^{rx}$ for constant coefficients, just with the appropriate "natural" ansatz for equidimensional operators.

C: Substituting $y = x^r$ into $a x^2 y'' + b x y' + c y = 0$ gives the [auxiliary (indicial) equation] $a r(r-1) + b r + c = 0$, whose roots determine the fundamental solutions.

Q: What are the three cases of solutions for a Cauchy-Euler equation, analogous to the constant-coefficient cases?
A: Let $r_1, r_2$ be roots of the auxiliary equation $a r(r-1) + b r + c = 0$. Distinct real roots: $y = c_1 x^{r_1} + c_2 x^{r_2}$. Repeated root $r$: $y = c_1 x^r + c_2 x^r \ln|x|$. Complex roots $\alpha \pm \beta i$: $y = x^\alpha (c_1 \cos(\beta \ln|x|) + c_2 \sin(\beta \ln|x|))$. Each mirrors the constant-coefficient trio under the change of variable $x = e^t$.

Q: Why do the Cauchy-Euler cases mirror the constant-coefficient cases so precisely?
A: The substitution $x = e^t$ (equivalently $t = \ln x$) transforms a Cauchy-Euler equation into a constant-coefficient linear ODE in $t$. Solutions $e^{rt}$, $t e^{rt}$, $e^{\alpha t}\cos \beta t$ in the new variable correspond to $x^r$, $x^r \ln x$, $x^\alpha \cos(\beta \ln x)$ in the original. The analogy is not coincidental; it is a change of variables.

## 6.16 IPEE Worked Examples

P: Solve the IVP $y'' - 4y' + 4y = 0$ with $y(0) = 1$ and $y'(0) = 3$, where $y = y(x)$.

S:
**IDENTIFY**: Constant-coefficient second-order linear homogeneous IVP. Compute the discriminant of the characteristic equation to decide which case applies.

**PLAN**:
- Write the characteristic equation $ar^2 + br + c = 0$ with $a=1$, $b=-4$, $c=4$.
- Find the roots and check $\Delta = b^2 - 4ac$ to classify the case.
- Write the general solution for the matching case.
- Apply $y(0)$ and $y'(0)$ to solve for $c_1, c_2$.

**EXECUTE**:
1. Characteristic equation: $r^2 - 4r + 4 = 0$. Discriminant $\Delta = (-4)^2 - 4(1)(4) = 0$, so we are in the repeated-root case.
2. Factor: $(r-2)^2 = 0$, so $r = 2$ (double).
3. General solution: $y(x) = c_1 e^{2x} + c_2 x e^{2x}$.
4. Derivative: $y'(x) = 2c_1 e^{2x} + c_2 e^{2x} + 2 c_2 x e^{2x} = (2c_1 + c_2) e^{2x} + 2 c_2 x e^{2x}$.
5. Apply $y(0) = 1$: $c_1 = 1$.
6. Apply $y'(0) = 3$: $2c_1 + c_2 = 3 \Rightarrow 2 + c_2 = 3 \Rightarrow c_2 = 1$.
7. Solution: $y(x) = e^{2x} + x e^{2x} = (1 + x) e^{2x}$.

**EVALUATE**:
- Check $y(0) = (1+0)e^0 = 1$ ✓.
- Check $y'(x) = e^{2x} + 2(1+x)e^{2x} = (3 + 2x) e^{2x}$, so $y'(0) = 3$ ✓.
- Check ODE: $y'' = 2 e^{2x} + 2(3 + 2x) e^{2x} = (8 + 4x) e^{2x}$. Then $y'' - 4y' + 4y = (8+4x - 12 - 8x + 4 + 4x) e^{2x} = 0$ ✓.
- The coefficients of the ODE are constants (continuous on all of $\mathbb{R}$), so this solution is valid for all $x \in \mathbb{R}$ by the linear existence-uniqueness theorem.

P: Solve the IVP $y'' + 4y' + 13y = 0$ with $y(0) = 2$ and $y'(0) = 0$, where $y = y(x)$.

S:
**IDENTIFY**: Constant-coefficient second-order linear homogeneous IVP. Compute the discriminant to determine the case.

**PLAN**:
- Form the characteristic equation with $a=1$, $b=4$, $c=13$.
- Compute $\Delta = b^2 - 4ac$ to classify the root type.
- Write the general solution for the matching case.
- Apply both initial conditions to solve for the constants.

**EXECUTE**:
1. Characteristic equation: $r^2 + 4r + 13 = 0$. Discriminant $\Delta = 16 - 52 = -36 < 0$, so complex conjugate roots.
2. Roots: $r = \frac{-4 \pm \sqrt{-36}}{2} = \frac{-4 \pm 6i}{2} = -2 \pm 3i$. So $\alpha = -2$, $\beta = 3$.
3. General solution: $y(x) = e^{-2x}(c_1 \cos 3x + c_2 \sin 3x)$.
4. Derivative (product rule): $y'(x) = -2 e^{-2x}(c_1 \cos 3x + c_2 \sin 3x) + e^{-2x}(-3 c_1 \sin 3x + 3 c_2 \cos 3x)$.
5. Apply $y(0) = 2$: $e^0(c_1 \cdot 1 + c_2 \cdot 0) = c_1 = 2$.
6. Apply $y'(0) = 0$: $-2(c_1) + 3 c_2 = 0 \Rightarrow -4 + 3 c_2 = 0 \Rightarrow c_2 = 4/3$.
7. Solution: $y(x) = e^{-2x}\left(2 \cos 3x + \tfrac{4}{3} \sin 3x\right)$.

**EVALUATE**:
- Check $y(0) = 1 \cdot (2 + 0) = 2$ ✓.
- At $x = 0$, $y'(0) = -2(2) + 3(4/3) = -4 + 4 = 0$ ✓.
- Qualitative check: $\alpha = -2 < 0$ means solutions decay exponentially while oscillating with angular frequency $\beta = 3$ (period $2\pi/3$) — consistent with a damped oscillator.
- Coefficients are constants (continuous on $\mathbb{R}$), so the solution is valid for all $x \in \mathbb{R}$.
