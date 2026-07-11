+++
order = 13
subject = "mathematics"
tags = ["math", "differential-equations", "ode", "series-solutions", "frobenius", "ordinary-point", "regular-singular-point"]
+++

# Differential Equations — Series Solutions

## 13.1 Why Power Series Solutions

Q: Why do we need power series methods for ODEs when we already have techniques like integrating factors, characteristic equations, and Laplace transforms?
A: Earlier techniques assume constant coefficients or very specific nonconstant forms. Variable-coefficient second-order equations like Bessel's, Legendre's, and Hermite's equations generally have no closed-form solution in elementary functions. Power series methods work near well-behaved points for any analytic-coefficient ODE, making them the universal fallback.

Q: Why is power series expansion guaranteed to work somewhere, even when elementary solutions fail?
A: If the ODE's coefficients are analytic (have convergent Taylor series) at a point, then solutions are also analytic there. So a power series centered at that point must exist and converge on some interval, regardless of whether the resulting function has a familiar closed form.

C: Variable-coefficient equations such as Bessel, Legendre, and Hermite generally have [no closed-form solution in elementary functions], which motivates series methods.

## 13.2 Power Series Centered at $x_0$

C: A power series centered at $x_0$ has the form $y = \sum_{n=0}^\infty a_n (x - x_0)^n$, where $a_n$ are [constant coefficients] and $x_0$ is the center of expansion.

C: The [radius of convergence] $R$ of a power series is the largest number such that the series converges for all $x$ satisfying $|x - x_0| < R$.

Q: Why does every convergent power series define an infinitely differentiable function inside its radius of convergence?
A: Inside $|x - x_0| < R$, a power series can be differentiated term-by-term any number of times, and each resulting series has the same radius of convergence. So the function is smooth there, which is exactly what we need to substitute it into an ODE.

## 13.3 Ordinary Points

Q: Before defining "ordinary point" formally, predict: where should a second-order linear ODE $y'' + P(x)y' + Q(x)y = 0$ be "nicely behaved" enough for a power series solution?
A: Wherever the coefficient functions $P(x)$ and $Q(x)$ are themselves well-behaved analytic functions. Trouble arises only where the coefficients blow up or become non-smooth.

C: For the ODE $y'' + P(x) y' + Q(x) y = 0$, a point $x_0$ is called an [ordinary point] if both $P(x)$ and $Q(x)$ are analytic (have convergent Taylor series) at $x_0$.

Q: At an ordinary point $x_0$, what does the existence theorem for series solutions guarantee?
A: There exist two linearly independent power-series solutions centered at $x_0$. Both are analytic, and each series converges on at least the interval $|x - x_0| < R$, where $R$ is the distance from $x_0$ to the nearest singular point of the ODE.

C: At an ordinary point, the radius of convergence of the series solution is at least the [distance to the nearest singular point] in the complex plane.

## 13.4 Singular Points

C: A point $x_0$ is called a [singular point] of $y'' + P(x) y' + Q(x) y = 0$ if $P(x)$ or $Q(x)$ fails to be analytic at $x_0$.

Q: Why do we care about singular points even when we're solving near an ordinary point?
A: The nearest singular point sets the radius of convergence of our series solution at an ordinary point. Knowing where singularities live tells us how far the series is guaranteed to be valid without any extra work.

## 13.5 Regular Singular Points

C: A singular point $x_0$ is called [regular] if both $(x - x_0) P(x)$ and $(x - x_0)^2 Q(x)$ are analytic at $x_0$.

Q: Why does multiplying by $(x - x_0)$ and $(x - x_0)^2$ "tame" a regular singular point?
A: These factors cancel mild poles: a simple pole in $P$ and at most a double pole in $Q$. If the singularity is that mild, a modified series $x^r \sum a_n x^n$ can still solve the equation, which is the basis of the Frobenius method.

## 13.6 Irregular Singular Points

C: A singular point is called [irregular] if it is singular but not regular, meaning $(x - x_0) P(x)$ or $(x - x_0)^2 Q(x)$ still fails to be analytic.

Q: Why are irregular singular points avoided in introductory series-solution methods?
A: At irregular singular points the Frobenius ansatz $x^r \sum a_n x^n$ generally fails: solutions may involve essential singularities, divergent asymptotic series, or require more sophisticated techniques beyond ordinary power series.

## 13.7 Method at an Ordinary Point

Q: What is the core procedural idea for solving an ODE at an ordinary point $x_0$?
A: Assume $y = \sum a_n (x - x_0)^n$, differentiate term-by-term to get $y'$ and $y''$, substitute into the ODE, collect terms by power of $(x - x_0)$, and force each coefficient to vanish. This produces a recurrence relation linking the $a_n$.

C: After substituting a power series into an ODE at an ordinary point, you [set each coefficient of $(x - x_0)^n$ to zero] to obtain the recurrence relation.

## 13.8 Recurrence Relations

C: A [recurrence relation] expresses a coefficient $a_{n+k}$ in terms of earlier coefficients $a_n, a_{n-1}, \ldots$, determining the series from a few free starting values.

Q: Why do recurrence relations from second-order ODEs typically leave exactly two coefficients arbitrary?
A: A second-order linear ODE has a two-dimensional solution space, so its general solution has two free constants. In the series picture, the recurrence lets you solve for all $a_n$ with $n \geq 2$ in terms of $a_0$ and $a_1$, which play the role of these two arbitrary constants.

C: In a typical second-order recurrence, the two arbitrary constants correspond to the free choices of [$a_0$ and $a_1$].

## 13.9 Two Linearly Independent Series

Q: How do you split a single power-series solution into two linearly independent solutions?
A: Set $a_0 = 1, a_1 = 0$ to generate one series $y_1(x)$; then set $a_0 = 0, a_1 = 1$ to generate a second series $y_2(x)$. These are linearly independent by construction, and the general solution is $y = c_1 y_1(x) + c_2 y_2(x)$.

C: The first independent series solution is typically obtained by choosing [$a_0 = 1, a_1 = 0$] and the second by $a_0 = 0, a_1 = 1$.

Q: Why are the two series from the $(a_0=1,a_1=0)$ and $(a_0=0,a_1=1)$ choices automatically linearly independent?
A: Evaluated at $x_0$, one gives $y_1(x_0) = 1, y_1'(x_0) = 0$ and the other gives $y_2(x_0) = 0, y_2'(x_0) = 1$. Their Wronskian at $x_0$ equals $1 \neq 0$, proving linear independence.

## 13.10 Worked Example — Airy Equation

C: The [Airy equation] is $y'' - x y = 0$, a simple-looking ODE whose solutions cannot be written in elementary functions.

Q: Why is the Airy equation a natural first example of the power series method?
A: $x = 0$ is an ordinary point (coefficients are polynomials, hence entire), so series solutions converge for all $x$. Yet the solutions $\mathrm{Ai}(x), \mathrm{Bi}(x)$ are not elementary, showing that power series produce genuinely new functions.

P: Find a power series solution of $y'' - x y = 0$ centered at $x_0 = 0$.

S:
**IDENTIFY**: Linear second-order ODE with analytic coefficients at $x_0 = 0$ (an ordinary point); use direct power series substitution.

**PLAN**:
- Assume $y = \sum_{n=0}^\infty a_n x^n$.
- Compute $y'' = \sum_{n=2}^\infty n(n-1) a_n x^{n-2}$.
- Substitute into $y'' - x y = 0$ and align powers of $x$.
- Equate coefficient of each $x^n$ to zero and solve for the recurrence.

**EXECUTE**:
1. $y'' = \sum_{n=2}^\infty n(n-1) a_n x^{n-2} = \sum_{m=0}^\infty (m+2)(m+1) a_{m+2} x^m$.
2. $x y = \sum_{n=0}^\infty a_n x^{n+1} = \sum_{m=1}^\infty a_{m-1} x^m$.
3. Substituting: the $x^0$ term gives $2 \cdot 1 \cdot a_2 = 0$, so $a_2 = 0$.
4. For $m \geq 1$: $(m+2)(m+1) a_{m+2} - a_{m-1} = 0$, giving the recurrence $a_{m+2} = \dfrac{a_{m-1}}{(m+1)(m+2)}$.
5. With $a_0 = 1, a_1 = 0$: $a_3 = \frac{1}{6}, a_6 = \frac{1}{180}, \ldots$; with $a_0 = 0, a_1 = 1$: $a_4 = \frac{1}{12}, a_7 = \frac{1}{504}, \ldots$.

**EVALUATE**: Two independent series emerge, both with infinite radius of convergence (polynomial coefficients have no singular points). These are the Airy functions $\mathrm{Ai}(x), \mathrm{Bi}(x)$ up to linear combinations.

## 13.11 Shifting the Summation Index

Q: Why do we so often need to shift the index in series manipulations?
A: After differentiating or multiplying by a power of $x$, different terms in an ODE produce series starting at different powers and with different index offsets. Shifting the index rewrites each series with the same generic power $x^m$, so we can combine them and read off the coefficient of each $x^m$.

Q: After the standard index shift $m = n - 1$, what does the series $\sum_{n=0}^\infty a_n x^{n-1}$ become?
A: $\sum_{m=-1}^\infty a_{m+1} x^m$.

Q: When shifting an index $n \to m$, how do the summation bounds change?
A: The new lower bound is whatever value of $m$ corresponds to the old lower bound of $n$; the upper bound $+\infty$ stays $+\infty$. E.g., if $m = n - 2$ and $n$ starts at $2$, then $m$ starts at $0$.

## 13.12 Frobenius Method at a Regular Singular Point

Q: Why does an ordinary power series $\sum a_n (x - x_0)^n$ fail at a regular singular point?
A: Such a series is automatically analytic at $x_0$, but solutions near a regular singular point often blow up or go to zero in a non-analytic way (like $\sqrt{x}$ or $\ln x$). A plain Taylor series cannot capture that behavior; we need an extra factor $x^r$ with possibly non-integer $r$.

C: The [Frobenius method] seeks solutions of the form $y = (x - x_0)^r \sum_{n=0}^\infty a_n (x - x_0)^n$ near a regular singular point, where $r$ is an exponent to be determined and $a_0 \neq 0$.

Q: In the Frobenius ansatz $y = x^r \sum a_n x^n$, why is $a_0$ required to be nonzero?
A: Otherwise the leading power of the series would be larger than $r$, and we could absorb the mismatch into a redefined $r$. Forcing $a_0 \neq 0$ makes $r$ the unique true leading exponent of the solution, which is what the indicial equation fixes.

## 13.13 The Indicial Equation

C: The [indicial equation] is a quadratic polynomial in $r$, obtained from the lowest-order terms after substituting the Frobenius series into the ODE and setting the coefficient of the lowest power of $x$ to zero.

Q: Why does the indicial equation come from only the lowest-order terms, ignoring higher ones?
A: When $y = x^r \sum a_n x^n$ is substituted, the lowest power of $x$ comes purely from the $a_0$ term. Forcing its coefficient to vanish (with $a_0 \neq 0$) gives one equation involving only $r$ — the indicial equation — independent of higher coefficients.

C: The roots $r_1$ and $r_2$ of the indicial equation are called [the exponents] of the singularity.

## 13.14 Three Cases for Frobenius Solutions

Q: What are the three cases in the Frobenius method, classified by how the indicial roots relate to each other?
A: (a) $r_1 - r_2$ is not an integer — two independent Frobenius series exist, one for each root. (b) $r_1 = r_2$ (repeated root) — only one Frobenius series; the second solution must include a $\ln x$ term. (c) $r_1 - r_2$ is a nonzero integer — the series for the smaller root may break down at the step where it would produce the larger-root terms, so the second solution may or may not need a $\ln x$ term.

C: If the Frobenius indicial roots differ by a non-integer, there exist [two independent Frobenius series solutions], one for each root.

C: If the Frobenius indicial roots are equal ($r_1 = r_2$), the second linearly independent solution necessarily contains a [$\ln x$ term].

Q: Why does a repeated indicial root force a logarithm into the second solution?
A: With only one root $r$, the Frobenius construction produces only one series. A second independent solution can be obtained by reduction of order or by differentiating with respect to $r$, and both approaches introduce a $\ln x$ factor, analogous to the repeated-root case for constant-coefficient ODEs.

## 13.15 Bessel's Equation

C: [Bessel's equation] of order $\nu$ is $x^2 y'' + x y' + (x^2 - \nu^2) y = 0$, where $\nu$ is a nonnegative real parameter and $x$ is the independent variable.

Q: Why is $x = 0$ a regular singular point of Bessel's equation?
A: Rewriting in standard form gives $P(x) = 1/x$ and $Q(x) = (x^2 - \nu^2)/x^2$. Then $xP(x) = 1$ and $x^2 Q(x) = x^2 - \nu^2$ are both analytic at $x = 0$, which is exactly the definition of a regular singular point.

C: The two standard solutions of Bessel's equation of order $\nu$ are denoted [$J_\nu(x)$ and $Y_\nu(x)$], called the Bessel functions of the first and second kind.

Q: Where do Bessel functions naturally arise in physics?
A: Whenever you solve the wave equation, heat equation, or Laplace equation in cylindrical coordinates and separate variables, the radial equation becomes Bessel's equation. So Bessel functions describe vibrations of drumheads, heat flow in cylinders, and many waveguide problems.

## 13.16 Legendre's Equation

C: [Legendre's equation] is $(1 - x^2) y'' - 2x y' + \nu(\nu + 1) y = 0$, where $\nu$ is a constant parameter and $x \in (-1, 1)$.

Q: Why are Legendre polynomials physically important?
A: They arise when solving Laplace's equation in spherical coordinates by separation of variables: the polar-angle equation is Legendre's equation. For integer $\nu$, one solution is a polynomial (the Legendre polynomial), giving the angular structure of gravitational, electrostatic, and quantum multipole expansions.

Q: Why does requiring a bounded solution on $[-1, 1]$ force $\nu$ to be a nonnegative integer in Legendre's equation?
A: The generic Frobenius series around $x = \pm 1$ (both regular singular points) diverges there. The series terminates into a polynomial — which is bounded — precisely when $\nu$ is a nonnegative integer, selecting the discrete Legendre polynomials $P_n(x)$.

## 13.17 Verification Example — Recovering $\cos x + \sin x$

P: Find a power series solution of $y'' + y = 0$ centered at $x_0 = 0$ and verify it reproduces $c_1 \cos x + c_2 \sin x$.

S:
**IDENTIFY**: Second-order linear ODE with constant coefficients, analytic everywhere; $x_0 = 0$ is an ordinary point. Apply direct power series substitution.

**PLAN**:
- Assume $y = \sum_{n=0}^\infty a_n x^n$.
- Differentiate twice; align powers using an index shift.
- Derive the recurrence and compute coefficients for the two independent choices $(a_0,a_1) = (1,0)$ and $(0,1)$.
- Compare the resulting series with the Taylor series of $\cos x$ and $\sin x$.

**EXECUTE**:
1. $y'' = \sum_{n=2}^\infty n(n-1) a_n x^{n-2} = \sum_{m=0}^\infty (m+2)(m+1) a_{m+2} x^m$.
2. Substituting into $y'' + y = 0$: $\sum_{m=0}^\infty \left[(m+2)(m+1) a_{m+2} + a_m\right] x^m = 0$.
3. Each coefficient vanishes: $a_{m+2} = -\dfrac{a_m}{(m+1)(m+2)}$.
4. Choice $a_0 = 1, a_1 = 0$: $a_2 = -\tfrac{1}{2!}, a_4 = \tfrac{1}{4!}, a_6 = -\tfrac{1}{6!}, \ldots$, giving $y_1 = \sum_{k=0}^\infty \dfrac{(-1)^k x^{2k}}{(2k)!} = \cos x$.
5. Choice $a_0 = 0, a_1 = 1$: $a_3 = -\tfrac{1}{3!}, a_5 = \tfrac{1}{5!}, \ldots$, giving $y_2 = \sum_{k=0}^\infty \dfrac{(-1)^k x^{2k+1}}{(2k+1)!} = \sin x$.

**EVALUATE**: The general solution $y = c_1 y_1 + c_2 y_2 = c_1 \cos x + c_2 \sin x$ matches the known constant-coefficient answer from the characteristic equation $r^2 + 1 = 0$, confirming the method.

## 13.18 Indicial Equation Example

P: Find the indicial equation and its roots for $2 x^2 y'' + x y' + (x^2 - 1) y = 0$ at $x_0 = 0$.

S:
**IDENTIFY**: Second-order linear ODE; check whether $x_0 = 0$ is a regular singular point, then apply the Frobenius method to extract the indicial equation.

**PLAN**:
- Write in standard form $y'' + P(x) y' + Q(x) y = 0$.
- Verify $xP(x)$ and $x^2 Q(x)$ are analytic at $0$.
- Substitute $y = x^r \sum_{n=0}^\infty a_n x^n$ with $a_0 \neq 0$.
- Extract the coefficient of the lowest power of $x$ and set it to zero.

**EXECUTE**:
1. Divide by $2x^2$: $y'' + \dfrac{1}{2x} y' + \dfrac{x^2 - 1}{2x^2} y = 0$. So $P(x) = \tfrac{1}{2x}$ and $Q(x) = \tfrac{x^2 - 1}{2 x^2}$.
2. $xP(x) = \tfrac{1}{2}$ and $x^2 Q(x) = \tfrac{x^2 - 1}{2}$ are both analytic at $0$, so $x_0 = 0$ is a regular singular point.
3. Substitute $y = \sum_{n=0}^\infty a_n x^{n+r}$: $y' = \sum (n+r) a_n x^{n+r-1}$, $y'' = \sum (n+r)(n+r-1) a_n x^{n+r-2}$.
4. Plug into the original equation and collect the lowest power ($x^r$ from $n = 0$): $2 r (r-1) a_0 + r a_0 - a_0 = 0$.
5. With $a_0 \neq 0$: indicial equation $2 r^2 - 2 r + r - 1 = 2 r^2 - r - 1 = 0$.
6. Roots: $r = \dfrac{1 \pm \sqrt{1 + 8}}{4} = \dfrac{1 \pm 3}{4}$, so $r_1 = 1$ and $r_2 = -\tfrac{1}{2}$.

**EVALUATE**: The roots differ by $r_1 - r_2 = \tfrac{3}{2}$, which is not an integer. By the three-case classification, two independent Frobenius series solutions exist, one behaving like $x$ near $0$ and the other like $x^{-1/2}$.
