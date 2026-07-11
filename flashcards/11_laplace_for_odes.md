+++
order = 11
subject = "mathematics"
tags = ["math", "differential-equations", "ode", "laplace-transform", "partial-fractions", "convolution", "transfer-function"]
+++

# Differential Equations — Solving ODEs with the Laplace Transform

## 11.1 Why Laplace is Effective for IVPs

Q: Before reading further, predict: when you apply the Laplace transform to a linear ODE with constant coefficients, what happens to the derivatives?
A: They turn into multiplication by $s$ (plus a term involving the initial value). The differential equation becomes an algebraic equation in $Y(s) = \mathcal{L}\{y(t)\}$, which is much easier to solve.

Q: Why is the Laplace transform especially effective for initial value problems?
A: The transform of $y'(t)$ is $sY(s) - y(0)$, so initial conditions are built directly into the algebraic equation. Unlike undetermined coefficients, you never have to solve for arbitrary constants at the end — the particular solution that satisfies the ICs comes out automatically.

C: The Laplace transform converts a linear constant-coefficient ODE into an [algebraic] equation in $Y(s)$.

C: Using $\mathcal{L}\{y'\} = sY(s) - y(0)$, the initial condition $y(0)$ is automatically [baked into] the transformed equation.

Q: What advantage does Laplace have over undetermined coefficients for IVPs?
A: Laplace produces the specific solution matching the initial conditions directly, with no arbitrary constants to determine afterward. Undetermined coefficients first yields a general solution, then requires separate algebra to pin down the constants using the ICs.

## 11.2 The Three-Step Procedure

C: Step 1 of Laplace solution: apply $\mathcal{L}$ to [both sides] of the ODE.

C: Step 2 of Laplace solution: solve the resulting algebraic equation for [$Y(s)$].

C: Step 3 of Laplace solution: apply [$\mathcal{L}^{-1}$] to recover $y(t)$.

Q: In the Laplace procedure, after solving for $Y(s)$, why is the inverse transform usually the hardest step?
A: $Y(s)$ is typically a rational function (ratio of polynomials in $s$) that does not match any transform-table entry directly. Partial fraction decomposition is needed to break it into pieces whose inverse transforms are known.

## 11.3 Partial Fraction Decomposition

C: The standard tool for inverting a rational $Y(s) = N(s)/D(s)$ is [partial fraction decomposition].

Q: Why do we use partial fractions before applying $\mathcal{L}^{-1}$?
A: The Laplace table lists inverses of simple rational forms like $\frac{1}{s-a}$, $\frac{1}{(s-a)^2}$, and $\frac{b}{(s-a)^2+b^2}$. Partial fractions decompose a complicated $Y(s)$ into a sum of these simple pieces, each of which can be inverted term by term using linearity.

C: Partial fraction decomposition relies on the [linearity] of $\mathcal{L}^{-1}$: the inverse of a sum equals the sum of inverses.

## 11.4 Distinct Linear Factors

C: $\frac{1}{(s-a)(s-b)} = \frac{A}{s-a} + \frac{[B]}{s-b}$, where $a \ne b$.

Q: How do you find $A$ in $\frac{1}{(s-a)(s-b)} = \frac{A}{s-a} + \frac{B}{s-b}$?
A: Use the cover-up method: multiply both sides by $(s-a)$ and set $s = a$, giving $A = \frac{1}{a-b}$. The $(s-a)$ factor on the right cancels, and the $(s-b)$ term vanishes at $s = a$.

C: $\mathcal{L}^{-1}\left\{\frac{1}{s-a}\right\} = [e^{at}]$, where $a$ is a constant and $t \ge 0$.

## 11.5 Repeated Linear Factors

C: For a repeated root, $\frac{1}{(s-a)^2}$ decomposes using terms $\frac{A}{s-a} + \frac{B}{[(s-a)^2]}$.

Q: Why must repeated factors contribute one term for each power up to the multiplicity?
A: The numerator of each partial fraction must be a constant (lower degree than the denominator factor). A single $\frac{A}{(s-a)^2}$ cannot reproduce an arbitrary numerator of degree up to 1, so we need both $\frac{A}{s-a}$ and $\frac{B}{(s-a)^2}$ to span all possibilities.

C: $\mathcal{L}^{-1}\left\{\frac{1}{(s-a)^2}\right\} = [t e^{at}]$, where $a$ is a constant.

C: In general, $\mathcal{L}^{-1}\left\{\frac{n!}{(s-a)^{n+1}}\right\} = [t^n e^{at}]$.

## 11.6 Irreducible Quadratic Factors

Q: When does a quadratic factor $s^2 + \alpha s + \beta$ stay irreducible over the reals?
A: When its discriminant $\alpha^2 - 4\beta$ is negative, i.e., the quadratic has complex conjugate roots. Such a factor cannot be split into distinct real linear factors.

C: For an irreducible quadratic denominator, rewrite it as $(s-a)^2 + b^2$ by [completing the square].

C: $\mathcal{L}^{-1}\left\{\frac{b}{(s-a)^2+b^2}\right\} = [e^{at}\sin bt]$, where $a$ and $b$ are real constants.

C: $\mathcal{L}^{-1}\left\{\frac{s-a}{(s-a)^2+b^2}\right\} = [e^{at}\cos bt]$, where $a$ and $b$ are real constants.

Q: Why does completing the square work so neatly for Laplace inversion?
A: The shift theorem states $\mathcal{L}\{e^{at}f(t)\} = F(s-a)$, so shifts in $s$ correspond to multiplication by $e^{at}$ in $t$. Writing the quadratic as $(s-a)^2 + b^2$ makes the shift $a$ explicit, letting you read off an exponential times sine or cosine directly.

## 11.7 Discontinuous Forcing with Heaviside

Q: Why is the Heaviside function $u_c(t)$ the natural tool for piecewise forcing?
A: $u_c(t)$ switches from 0 to 1 at $t = c$, so multiplying any function by $u_c(t)$ activates it only for $t \ge c$. Any piecewise-defined forcing function can be rewritten as a sum of such shifted "switches," giving one clean algebraic expression instead of multiple cases.

C: A forcing that equals $g_1(t)$ for $0 \le t < c$ and $g_2(t)$ for $t \ge c$ can be written $f(t) = g_1(t) + u_c(t)\lbrack g_2(t) - g_1(t)\rbrack $, where $u_c(t)$ is the [Heaviside step] at $t = c$.

Q: Why does the piecewise rewrite use $g_2(t) - g_1(t)$ inside the Heaviside term?
A: At $t = c$ the Heaviside switches on. Adding $g_2 - g_1$ at that moment cancels the active $g_1$ contribution and installs $g_2$ instead, producing a clean jump from $g_1$ to $g_2$ without leaving residual pieces behind.

## 11.8 Laplace Handles Piecewise Forcing Naturally

C: The Laplace transform of a shifted-and-activated function is $\mathcal{L}\{u_c(t) f(t-c)\} = [e^{-cs} F(s)]$, where $F(s) = \mathcal{L}\{f(t)\}$.

Q: Why does each piecewise break-point produce a factor of $e^{-cs}$ in $Y(s)$?
A: Each shifted Heaviside $u_c(t) f(t-c)$ transforms to $e^{-cs}F(s)$ by the second shift theorem. So every activation of a new piece at $t = c$ contributes a distinct $e^{-cs}$ factor, encoding the time-delay algebraically in $s$-space.

Q: Why is Laplace preferable to undetermined coefficients when the forcing is piecewise?
A: Undetermined coefficients would require solving the ODE separately on each interval and then matching $y$ and $y'$ at the break-points — a tedious bookkeeping task. Laplace absorbs all the switching into $e^{-cs}$ factors and handles continuity automatically.

## 11.9 Impulsive Forcing

Q: What does the Dirac delta $\delta(t-c)$ model physically?
A: An idealized instantaneous impulse delivered at time $t = c$ — for example, a hammer strike or a sudden kick. It has zero duration but unit "area," so it transfers a finite amount of momentum/energy instantaneously.

C: $\mathcal{L}\{\delta(t-c)\} = [e^{-cs}]$, for $c \ge 0$.

Q: Why does an impulse $\delta(t-c)$ on the right of a second-order ODE cause a jump in $y'$ but not in $y$?
A: Integrating the ODE across the impulse, the $y''$ term contributes a jump in $y'$ equal to the impulse strength, while the lower-order $y'$ and $y$ terms stay continuous because the integral of a bounded function over zero duration is zero. Thus $y$ is continuous but has a corner at $t = c$.

## 11.10 Transfer Function

Q: Why do engineers care about the transfer function $H(s)$?
A: $H(s) = Y(s)/F(s)$ (with zero initial conditions) depends only on the system, not on the forcing. It encodes everything about how the system responds to any input, so one calculation of $H(s)$ lets you predict the output for any $F(s)$ by simple multiplication.

C: For a linear time-invariant system with zero initial conditions, $Y(s) = [H(s) F(s)]$, where $H(s)$ is the transfer function and $F(s) = \mathcal{L}\{f(t)\}$.

C: The transfer function is $H(s) = Y(s)/F(s)$, computed assuming [zero initial conditions].

Q: For the ODE $a y'' + b y' + c y = f(t)$ with zero ICs, what is the transfer function?
A: Applying $\mathcal{L}$ gives $(a s^2 + b s + c) Y(s) = F(s)$, so $H(s) = \frac{1}{a s^2 + b s + c}$. The denominator is the characteristic polynomial of the homogeneous ODE.

## 11.11 Convolution Gives the Solution

C: The impulse response $h(t)$ of an LTI system is defined as $h(t) = [\mathcal{L}^{-1}\{H(s)\}]$, where $H(s)$ is the transfer function.

C: By the convolution theorem, the zero-IC solution is $y(t) = [h(t) * f(t)]$, where $h$ is the impulse response and $f$ is the forcing.

Q: Why is $y(t) = h(t) * f(t)$ intuitive?
A: Any forcing $f$ can be viewed as a superposition of tiny impulses $f(\tau)\,d\tau$ at each time $\tau$. Each impulse produces a time-shifted impulse response $h(t-\tau)$, and linearity lets us sum them: $y(t) = \int_0^t h(t-\tau) f(\tau)\, d\tau$, which is exactly the convolution.

Q: What is the physical meaning of $h(t)$?
A: $h(t)$ is the system's response to a unit impulse $\delta(t)$ applied with zero initial conditions. It's the fundamental "signature" of the system; every other forced response can be built from it by convolution.

## 11.12 Zero-State and Zero-Input Response

C: The full solution splits as $y(t) = y_{\text{zi}}(t) + y_{\text{zs}}(t)$, where $y_{\text{zi}}$ is the [zero-input] response (from initial conditions, no forcing) and $y_{\text{zs}}$ is the zero-state response (from forcing, zero ICs).

Q: Why does linearity let us decompose the solution into zero-input and zero-state pieces?
A: A linear ODE's response to the sum of two inputs equals the sum of responses. Treating the initial conditions as one "input" and the forcing $f(t)$ as another, we can solve each separately with the other set to zero and add the results.

Q: What does each piece of the decomposition represent physically?
A: The zero-input response describes how the system evolves from its initial state if left alone. The zero-state response describes how the system responds to the external forcing if it started at rest. Real systems exhibit the superposition of both.

## 11.13 When Laplace Beats Undetermined Coefficients

Q: When is Laplace strictly preferable to undetermined coefficients?
A: For discontinuous forcing (step functions, piecewise inputs) and impulsive forcing ($\delta$-functions), Laplace handles the switching and impulses automatically through $e^{-cs}$ factors. Undetermined coefficients would require patching solutions across intervals and manually matching continuity.

Q: When is undetermined coefficients actually simpler than Laplace?
A: For smooth, standard forcing terms like polynomials, $e^{at}$, $\sin\omega t$, $\cos\omega t$, or products of these, undetermined coefficients is faster — no partial fractions or inverse transform bookkeeping needed.

## 11.14 Worked Problem: Resonant Forcing

P: Solve $y'' + 4y = \sin 2t$ with $y(0) = 0$, $y'(0) = 1$ using the Laplace transform.

S:
**IDENTIFY**: Second-order linear ODE with sinusoidal forcing at the natural frequency — classical resonance case. $Y(s)$ will have a repeated irreducible quadratic factor.

**PLAN**:
- Transform both sides using $\mathcal{L}\{y''\} = s^2 Y - s y(0) - y'(0)$ and $\mathcal{L}\{\sin 2t\} = \frac{2}{s^2+4}$.
- Solve algebraically for $Y(s)$.
- Decompose and invert, recognizing that the repeated $(s^2+4)^2$ factor signals resonance (a $t \cdot \sin/\cos$ term).

**EXECUTE**:
1. Transform: $s^2 Y - 1 + 4 Y = \frac{2}{s^2+4}$, so $(s^2+4) Y = 1 + \frac{2}{s^2+4}$.
2. Solve: $Y(s) = \frac{1}{s^2+4} + \frac{2}{(s^2+4)^2}$.
3. First term: $\mathcal{L}^{-1}\{\tfrac{1}{s^2+4}\} = \tfrac{1}{2}\sin 2t$.
4. Second term: using the standard result $\mathcal{L}^{-1}\left\{\frac{2b^3}{(s^2+b^2)^2}\right\} = \sin bt - bt\cos bt$, with $b = 2$ we get $\mathcal{L}^{-1}\left\{\frac{16}{(s^2+4)^2}\right\} = \sin 2t - 2t\cos 2t$. Scaling by $2/16 = 1/8$: $\mathcal{L}^{-1}\left\{\frac{2}{(s^2+4)^2}\right\} = \tfrac{1}{8}(\sin 2t - 2t\cos 2t)$.
5. Combine: $y(t) = \tfrac{1}{2}\sin 2t + \tfrac{1}{8}\sin 2t - \tfrac{1}{4} t\cos 2t = \tfrac{5}{8}\sin 2t - \tfrac{1}{4} t\cos 2t$.

**EVALUATE**:
- At $t = 0$: $y(0) = 0$. ✓
- $y'(t) = \tfrac{5}{4}\cos 2t - \tfrac{1}{4}\cos 2t + \tfrac{1}{2} t \sin 2t = \cos 2t + \tfrac{1}{2} t\sin 2t$, so $y'(0) = 1$. ✓
- The $t\cos 2t$ term grows unboundedly — the hallmark of resonance when forcing frequency matches the natural frequency $\omega_0 = 2$.

## 11.15 Worked Problem: Step Forcing

P: Solve $y'' + y = u_\pi(t)$ with $y(0) = 0$, $y'(0) = 0$ using the Laplace transform.

S:
**IDENTIFY**: Second-order linear ODE with a Heaviside step forcing turning on at $t = \pi$. Expect $e^{-\pi s}$ factors and a piecewise solution.

**PLAN**:
- Transform both sides: $\mathcal{L}\{u_\pi(t)\} = e^{-\pi s}/s$.
- Solve for $Y(s)$, factor out $e^{-\pi s}$, decompose the remaining rational function.
- Invert using the second shift theorem: $\mathcal{L}^{-1}\{e^{-cs} G(s)\} = u_c(t) g(t-c)$.

**EXECUTE**:
1. Transform: $(s^2+1) Y(s) = \frac{e^{-\pi s}}{s}$, so $Y(s) = e^{-\pi s}\cdot \frac{1}{s(s^2+1)}$.
2. Partial fractions: $\frac{1}{s(s^2+1)} = \frac{1}{s} - \frac{s}{s^2+1}$.
3. Inverse of the non-shifted part: $g(t) = \mathcal{L}^{-1}\left\{\tfrac{1}{s} - \tfrac{s}{s^2+1}\right\} = 1 - \cos t$.
4. Apply the second shift: $y(t) = u_\pi(t)\,[1 - \cos(t-\pi)] = u_\pi(t)\,[1 + \cos t]$ (using $\cos(t-\pi) = -\cos t$).

**EVALUATE**:
- For $0 \le t < \pi$: $y(t) = 0$, matching zero ICs and no forcing yet. ✓
- For $t \ge \pi$: $y(t) = 1 + \cos t$. At $t = \pi$: $y(\pi) = 0$ and $y'(\pi) = -\sin\pi = 0$, so $y$ and $y'$ remain continuous through the switch-on, as expected for step (non-impulsive) forcing.
- For $t > \pi$, $y$ oscillates around the new equilibrium $y = 1$, consistent with a sudden constant driving force on an undamped oscillator.

## 11.16 Worked Problem: Impulse Forcing

P: Solve $y'' + 2y' + y = \delta(t-1)$ with $y(0) = 0$, $y'(0) = 0$ using the Laplace transform.

S:
**IDENTIFY**: Second-order linear ODE with a Dirac-delta impulse at $t = 1$. Characteristic polynomial $s^2 + 2s + 1 = (s+1)^2$ gives a critically damped system.

**PLAN**:
- Transform both sides: $\mathcal{L}\{\delta(t-1)\} = e^{-s}$.
- Solve for $Y(s)$ and recognize $\frac{1}{(s+1)^2}$ as the transform of $t e^{-t}$.
- Apply the second shift theorem for the $e^{-s}$ factor.

**EXECUTE**:
1. Transform: $(s^2 + 2s + 1) Y(s) = e^{-s}$, so $Y(s) = \frac{e^{-s}}{(s+1)^2}$.
2. Unshifted inverse: $\mathcal{L}^{-1}\left\{\tfrac{1}{(s+1)^2}\right\} = t e^{-t}$.
3. Apply second shift with $c = 1$: $y(t) = u_1(t) \cdot (t-1) e^{-(t-1)}$.

**EVALUATE**:
- For $0 \le t < 1$: $y(t) = 0$. Both $y$ and $y'$ vanish, matching zero ICs and no forcing. ✓
- At $t = 1$: $y(1) = 0$ (continuous), but $y'(t) = u_1(t)\,e^{-(t-1)}[1 - (t-1)]$ jumps from 0 to 1 — exactly the unit jump in $y'$ expected from a unit impulse on a second-order system.
- For $t > 1$: the solution $(t-1)e^{-(t-1)}$ rises, peaks, then decays to zero, the classical critically damped impulse response. ✓
