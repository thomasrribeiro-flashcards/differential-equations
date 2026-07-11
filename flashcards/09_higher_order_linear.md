+++
order = 9
subject = "mathematics"
tags = ["math", "differential-equations", "ode", "higher-order", "characteristic-polynomial", "wronskian"]
+++

# Differential Equations — Higher-Order Linear Equations

## 9.1 Generalization to $n$-th Order

Q: Why does extending linear ODE theory from second order to $n$-th order introduce no fundamentally new ideas?
A: The structural results (superposition, existence/uniqueness, general solution = homogeneous solution plus particular solution, linear independence via Wronskian) are consequences of linearity, not the specific order. Raising the order only changes the *size* of the fundamental set and the *degree* of the characteristic polynomial; the logic is identical.

C: An $n$-th order linear ODE has the general form $a_n(x) y^{(n)} + a_{n-1}(x) y^{(n-1)} + \cdots + a_1(x) y' + a_0(x) y = [g(x)]$, where $y^{(k)}$ denotes the $k$-th derivative of $y$ and $g(x)$ is the forcing term.

C: A linear $n$-th order ODE is called [homogeneous] when its right-hand side $g(x)$ is identically zero.

Q: What does it mean for an $n$-th order linear ODE to be in standard form?
A: Divide through by $a_n(x)$ so the leading coefficient is $1$: $y^{(n)} + p_{n-1}(x) y^{(n-1)} + \cdots + p_0(x) y = f(x)$. Standard form is required for the existence/uniqueness theorem and for the variation-of-parameters formulas.

## 9.2 General Solution Structure

Q: Why does the general solution of a nonhomogeneous $n$-th order linear ODE decompose as $y = y_c + y_p$?
A: Linearity implies that differences of solutions of the nonhomogeneous equation solve the homogeneous equation. So any solution can be written as one fixed particular solution $y_p$ plus *some* homogeneous solution $y_c$; the $n$-parameter family $y_c$ exhausts all homogeneous solutions.

C: The general solution of a nonhomogeneous $n$-th order linear ODE is $y = c_1 y_1 + c_2 y_2 + \cdots + c_n y_n + [y_p]$, where $\{y_1, \ldots, y_n\}$ is a fundamental set of solutions to the associated homogeneous equation and $y_p$ is any particular solution of the nonhomogeneous equation.

C: In the decomposition $y = y_c + y_p$, the piece $y_c = c_1 y_1 + \cdots + c_n y_n$ is called the [complementary solution] and solves the associated homogeneous equation.

## 9.3 Fundamental Set for $n$-th Order

Q: What is a fundamental set of solutions for an $n$-th order homogeneous linear ODE?
A: A collection of exactly $n$ solutions $\{y_1, \ldots, y_n\}$ that are linearly independent on the interval of interest. Such a set spans the solution space, so every homogeneous solution is a linear combination of its members.

Q: Why does a fundamental set for an $n$-th order equation need exactly $n$ functions — not more, not fewer?
A: The homogeneous solution space is an $n$-dimensional vector space (one dimension per initial condition needed). Fewer than $n$ independent solutions cannot span it; more than $n$ must be linearly dependent.

C: Functions $y_1, \ldots, y_n$ are [linearly independent] on an interval $I$ if the only constants $c_1, \ldots, c_n$ satisfying $c_1 y_1(x) + \cdots + c_n y_n(x) = 0$ for all $x \in I$ are $c_1 = c_2 = \cdots = c_n = 0$.

## 9.4 Wronskian for $n$ Functions

C: The Wronskian of $n$ functions $y_1, \ldots, y_n$ is the [$n \times n$ determinant] whose rows are the functions and their first $n-1$ derivatives.

C: Explicitly, $W(y_1, \ldots, y_n)(x) = \det\begin{pmatrix} y_1 & y_2 & \cdots & y_n \\ y_1' & y_2' & \cdots & y_n' \\ \vdots & \vdots & \ddots & \vdots \\ y_1^{(n-1)} & y_2^{(n-1)} & \cdots & [y_n^{(n-1)}] \end{pmatrix}$, where $y_j^{(k)}$ denotes the $k$-th derivative of $y_j$.

Q: How is the Wronskian used to verify a fundamental set?
A: If $y_1, \ldots, y_n$ are solutions of an $n$-th order linear homogeneous ODE on an interval $I$ and $W(y_1, \ldots, y_n)(x_0) \neq 0$ at some $x_0 \in I$, then the solutions are linearly independent on $I$ and thus form a fundamental set.

Q: Why does a nonzero Wronskian at a single point suffice to prove independence of solutions to a linear ODE?
A: Abel's theorem says the Wronskian of solutions is either identically zero on $I$ or never zero on $I$. So one nonzero value rules out the identically-zero case and guarantees independence throughout.

## 9.5 Existence and Uniqueness for $n$-th Order IVPs

C: An IVP for an $n$-th order linear ODE requires [$n$ initial conditions] of the form $y(x_0), y'(x_0), \ldots, y^{(n-1)}(x_0)$.

Q: State the existence/uniqueness theorem for an $n$-th order linear IVP.
A: If the coefficients $p_0(x), \ldots, p_{n-1}(x)$ and the forcing $f(x)$ are continuous on an open interval $I$ containing $x_0$, then for any prescribed values of $y(x_0), y'(x_0), \ldots, y^{(n-1)}(x_0)$ the IVP has a unique solution on all of $I$.

## 9.6 Why $n$ Initial Conditions

Q: Why does an $n$-th order linear IVP require exactly $n$ initial conditions — no more, no fewer?
A: The general solution contains $n$ arbitrary constants $c_1, \ldots, c_n$. Each initial condition imposes one scalar equation on these constants; $n$ conditions give a square linear system that pins down all constants uniquely (the Wronskian being nonzero guarantees the system is invertible).

C: The general solution of an $n$-th order linear ODE contains exactly [$n$ arbitrary constants], one for each dimension of the homogeneous solution space.

## 9.7 Constant-Coefficient Case

Q: Why does trying $y = e^{rx}$ in a constant-coefficient linear ODE reduce the problem to an algebraic one?
A: Every derivative of $e^{rx}$ is just a power of $r$ times $e^{rx}$. Substituting into $a_n y^{(n)} + \cdots + a_0 y = 0$ factors out $e^{rx}$, leaving the polynomial equation $a_n r^n + \cdots + a_1 r + a_0 = 0$, whose roots determine the solutions.

C: For the constant-coefficient homogeneous ODE $a_n y^{(n)} + \cdots + a_1 y' + a_0 y = 0$, the [characteristic polynomial] is $P(r) = a_n r^n + a_{n-1} r^{n-1} + \cdots + a_1 r + a_0$, obtained by replacing $y^{(k)}$ with $r^k$.

C: A constant-coefficient $n$-th order homogeneous linear ODE has a characteristic polynomial of degree exactly [$n$], which (counting multiplicity, over $\mathbb{C}$) contributes exactly $n$ roots and hence $n$ linearly independent solutions.

## 9.8 Distinct Real Roots

C: If the characteristic polynomial of a constant-coefficient linear ODE has $n$ distinct real roots $r_1, \ldots, r_n$, the general solution is $y = [c_1 e^{r_1 x} + c_2 e^{r_2 x} + \cdots + c_n e^{r_n x}]$, where $c_1, \ldots, c_n$ are arbitrary constants.

Q: Why are the exponentials $e^{r_1 x}, \ldots, e^{r_n x}$ linearly independent when the $r_i$ are distinct?
A: Their Wronskian is a Vandermonde-type determinant, $W = e^{(r_1 + \cdots + r_n)x} \prod_{i<j} (r_j - r_i)$, which is nonzero exactly when all the $r_i$ are distinct. So distinct roots guarantee independence.

## 9.9 Repeated Real Roots

Q: Why do repeated characteristic roots require the extra factors $x, x^2, \ldots$ beyond the bare exponential?
A: A repeated root $r$ produces only *one* independent exponential $e^{rx}$. To fill the $m$-dimensional solution piece associated with a root of multiplicity $m$, we need additional independent solutions; multiplying by $x$, $x^2$, etc., produces them, and direct substitution confirms each solves the ODE.

C: A real root $r$ of multiplicity $m$ of the characteristic polynomial contributes the $m$ independent solutions $[e^{rx}, xe^{rx}, x^2 e^{rx}, \ldots, x^{m-1} e^{rx}]$ to the general solution, where $m$ is the multiplicity of $r$.

C: The general solution piece from a real root $r$ of multiplicity $3$ is $(c_1 + c_2 x + [c_3 x^2]) e^{rx}$, where $c_1, c_2, c_3$ are arbitrary constants.

## 9.10 Complex Conjugate Roots

Q: Why do complex conjugate roots $\alpha \pm i\beta$ produce real solutions $e^{\alpha x}\cos\beta x$ and $e^{\alpha x}\sin\beta x$?
A: Euler's formula gives $e^{(\alpha \pm i\beta)x} = e^{\alpha x}(\cos\beta x \pm i\sin\beta x)$. Taking real and imaginary linear combinations of these complex solutions yields the two real, linearly independent solutions; since the ODE has real coefficients, real solutions suffice.

C: A simple complex conjugate pair of roots $\alpha \pm i\beta$ contributes the two real solutions $[e^{\alpha x}\cos(\beta x)]$ and $e^{\alpha x}\sin(\beta x)$, where $\alpha$ is the real part and $\beta$ is the imaginary part of the roots.

C: If the complex conjugate pair $\alpha \pm i\beta$ is a root of multiplicity $m$, it contributes $2m$ independent real solutions: $e^{\alpha x}\cos\beta x, xe^{\alpha x}\cos\beta x, \ldots, [x^{m-1} e^{\alpha x}\cos\beta x]$ and the same list with $\sin\beta x$ in place of $\cos\beta x$.

Q: How many real solutions does a complex conjugate pair of characteristic roots with multiplicity $m$ contribute, and why?
A: It contributes $2m$ real solutions. The pair represents $2m$ complex roots counted with multiplicity; linearity plus the repeated-root rule means we multiply each of the two base solutions $e^{\alpha x}\cos\beta x$ and $e^{\alpha x}\sin\beta x$ by $1, x, \ldots, x^{m-1}$.

## 9.11 Combining Cases

Q: How do you build the general solution when the characteristic polynomial has a mixture of simple, repeated, and complex roots?
A: Factor the characteristic polynomial completely. For each root (real or complex, with its multiplicity), write down the corresponding piece of the solution using the rules of sections 9.8–9.10, then sum all pieces. Each root contributes independently to the total fundamental set.

P: Given a third-order constant-coefficient homogeneous linear ODE whose characteristic polynomial factors as $(r - 2)^2 (r + 3) = 0$, write down the general solution.

S:
**IDENTIFY**: Constant-coefficient homogeneous linear ODE of order $3$. Characteristic roots: $r = 2$ (multiplicity $2$) and $r = -3$ (multiplicity $1$).

**PLAN**:
- Repeated real root $r = 2$ of multiplicity $2$ contributes $e^{2x}$ and $xe^{2x}$.
- Simple real root $r = -3$ contributes $e^{-3x}$.
- Sum with arbitrary constants.

**EXECUTE**:
$$y(x) = c_1 e^{2x} + c_2 x e^{2x} + c_3 e^{-3x},$$
where $c_1, c_2, c_3$ are arbitrary real constants.

**EVALUATE**: Three independent solutions, three arbitrary constants — matches the order $3$. The Wronskian at any point is nonzero (distinct behavior: pure $e^{2x}$, $xe^{2x}$ grows polynomially, and $e^{-3x}$ decays), confirming a fundamental set.

## 9.12 Undetermined Coefficients at Higher Order

Q: How does the method of undetermined coefficients change when moving from second-order to $n$-th order constant-coefficient equations?
A: Hardly at all — the guess table (polynomial, exponential, sine/cosine, and their products) and the modification rule are identical. The only difference is that the "modification multiplicity" is now the multiplicity of the forcing's exponent as a root of the *higher*-degree characteristic polynomial.

C: In undetermined coefficients for an $n$-th order constant-coefficient ODE, if the trial form $y_p$ corresponds to a characteristic root of multiplicity $k$, multiply the trial form by [$x^k$] to avoid duplicating a homogeneous solution.

Q: For the ODE $y^{(4)} - y = e^x$, how is the trial form for $y_p$ modified, and why?
A: Base trial is $A e^x$. The characteristic polynomial $r^4 - 1 = (r-1)(r+1)(r^2+1)$ has $r = 1$ as a simple root, so multiplicity $k = 1$. We multiply by $x^1$, giving $y_p = A x e^x$. Without the $x$ factor, $A e^x$ would solve the homogeneous equation and contribute zero on the left-hand side.

P: Write down the correct trial form (with the modification factor) for a particular solution of $y''' + y' = x^2 + e^x \sin x$. Do not solve for the coefficients.

S:
**IDENTIFY**: Undetermined coefficients for a third-order constant-coefficient ODE with a forcing that is a sum: a polynomial $x^2$ plus $e^x \sin x$. Use superposition to handle each piece separately.

**PLAN**:
- Find characteristic roots to check which trial forms collide with homogeneous solutions.
- Characteristic polynomial: $r^3 + r = r(r^2 + 1) = 0$, so roots are $r = 0, \; \pm i$.
- For forcing $x^2$: base trial is a general degree-$2$ polynomial $A x^2 + B x + C$. But $r = 0$ is a simple root, so multiply by $x^1$.
- For forcing $e^x \sin x$: associated complex exponent is $1 + i$. Check if $1 + i$ is a characteristic root — it is not (roots are $0, \pm i$). So no modification.

**EXECUTE**:
Polynomial piece: $y_{p,1} = x(A x^2 + B x + C) = A x^3 + B x^2 + C x$.
Exponential-trig piece: $y_{p,2} = e^x (D \cos x + E \sin x)$.
Total trial: $$y_p = A x^3 + B x^2 + C x + e^x (D \cos x + E \sin x),$$ where $A, B, C, D, E$ are the undetermined coefficients.

**EVALUATE**: The polynomial trial was bumped by $x^1$ because $r = 0$ has multiplicity $1$ in the characteristic polynomial; the $e^x\sin x$ trial needed no bump because $1 \pm i$ are not roots. If we had not bumped the polynomial, the constant term of the trial would solve $y''' + y' = 0$ and contribute nothing to the right-hand side.

## 9.13 Variation of Parameters for $n$-th Order

Q: Why does variation of parameters extend to $n$-th order ODEs, even when undetermined coefficients does not apply?
A: Variation of parameters requires only a fundamental set $\{y_1, \ldots, y_n\}$ of the homogeneous equation and a continuous forcing $f(x)$ — it makes no assumption about the form of $f$. It therefore handles forcings like $\tan x$, $\ln x$, or $1/x$ that lie outside the undetermined-coefficients guess table.

C: The $n$-th order variation-of-parameters formula is $y_p = \sum_{k=1}^n y_k(x) \int \dfrac{W_k(x)\, f(x)}{[W(x)]}\, dx$, where $W(x)$ is the Wronskian of the fundamental set, $W_k$ is the determinant obtained from $W$ by replacing its $k$-th column with $(0, 0, \ldots, 0, 1)^T$, $y_k$ is the $k$-th fundamental solution, and $f(x)$ is the forcing term (ODE in standard form).

Q: In the $n$-th order variation-of-parameters formula, why is the forcing column in the auxiliary determinant $W_k$ taken to be $(0, \ldots, 0, 1)^T$ instead of $(0, \ldots, 0, f(x))^T$?
A: The ODE must first be put in standard form (leading coefficient $1$). After Cramer's rule is applied to the system for $u_1', \ldots, u_n'$ whose right-hand side is $(0, \ldots, 0, f(x))^T$, the $f(x)$ factors out, leaving the cleaner form $u_k' = W_k f / W$ with the column $(0,\ldots,0,1)^T$.

## 9.14 $n$-th Order Cauchy–Euler

C: An $n$-th order Cauchy–Euler equation has the form $a_n x^n y^{(n)} + a_{n-1} x^{n-1} y^{(n-1)} + \cdots + a_1 x y' + a_0 y = [0]$ (for the homogeneous case), where each term pairs a power $x^k$ with the $k$-th derivative.

Q: Why does $y = x^r$ still work as a trial solution for the $n$-th order Cauchy–Euler equation?
A: The $k$-th derivative of $x^r$ is $r(r-1)\cdots(r-k+1) x^{r-k}$, and the factor $x^k$ multiplying it restores the power to $x^r$. Every term becomes a polynomial in $r$ times $x^r$, so the equation reduces to an algebraic polynomial equation in $r$.

C: For the $n$-th order Cauchy–Euler equation, substituting $y = x^r$ produces a polynomial equation in $r$ called the [indicial polynomial], analogous to the characteristic polynomial of the constant-coefficient case.

Q: How are repeated and complex indicial roots handled in the $n$-th order Cauchy–Euler equation?
A: Exactly like the constant-coefficient case with the substitution $e^{rx} \mapsto x^r$ and $x \mapsto \ln x$. A real root $r$ of multiplicity $m$ gives $x^r, x^r \ln x, \ldots, x^r (\ln x)^{m-1}$; a complex pair $\alpha \pm i\beta$ gives $x^\alpha \cos(\beta \ln x)$ and $x^\alpha \sin(\beta \ln x)$, multiplied by powers of $\ln x$ if repeated.

## 9.15 Reduction of Order at Higher Order

Q: Why does reduction of order still work for $n$-th order linear ODEs when one solution $y_1$ is known?
A: Substituting $y = v(x) y_1(x)$ into the original $n$-th order equation produces an ODE for $v'$ of order $n - 1$ (the $v$ terms cancel because $y_1$ already solves the homogeneous equation). So knowing one solution always drops the order by exactly one.

C: Reduction of order applied to an $n$-th order linear ODE with one known solution $y_1$ reduces the problem to an ODE of order [$n - 1$] in the unknown $v'(x)$, where $y = v(x) y_1(x)$ is the ansatz.

## 9.16 Worked Example: Triple-Root Third-Order

P: Solve the third-order ODE $y''' - 3 y'' + 3 y' - y = 0$.

S:
**IDENTIFY**: Constant-coefficient, homogeneous, linear, third-order. Solve via the characteristic polynomial.

**PLAN**:
- Write the characteristic polynomial by substituting $y^{(k)} \to r^k$.
- Factor it and read off roots with multiplicities.
- Apply the repeated-root rule: multiplicity $m$ contributes $e^{rx}, xe^{rx}, \ldots, x^{m-1} e^{rx}$.

**EXECUTE**:
Characteristic polynomial: $r^3 - 3 r^2 + 3 r - 1 = 0$.
Recognize as the binomial expansion: $r^3 - 3r^2 + 3r - 1 = (r - 1)^3$.
So $r = 1$ is a root of multiplicity $3$.
General solution:
$$y(x) = c_1 e^{x} + c_2 x e^{x} + c_3 x^2 e^{x},$$
where $c_1, c_2, c_3$ are arbitrary real constants.

**EVALUATE**: Three independent solutions match order $3$. Checking independence: factoring out $e^x$ leaves $1, x, x^2$, whose Wronskian is a nonzero constant — so the three functions form a fundamental set. The answer is consistent with the pattern "multiplicity $m$ real root gives the first $m$ powers of $x$ times the exponential."
