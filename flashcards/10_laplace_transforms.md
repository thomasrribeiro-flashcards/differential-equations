+++
order = 10
subject = "mathematics"
tags = ["math", "differential-equations", "ode", "laplace-transform", "convolution", "heaviside", "dirac-delta"]
+++

# Differential Equations — The Laplace Transform

## 10.1 Definition of the Laplace Transform

Q: Before seeing the formula, predict: what kind of operation might turn a differential equation into an algebraic one?
A: An integral transform that exchanges the derivative operator for multiplication by a variable. If differentiation in $t$ becomes multiplication in a new variable $s$, then an ODE (which involves $dy/dt$) becomes a polynomial equation in $s$ that can be solved by algebra.

C: The Laplace transform of $f(t)$ is defined by $\mathcal{L}\{f(t)\} = F(s) = \int_0^\infty [e^{-st}] f(t)\,dt$, where $t \ge 0$ is the time variable and $s$ is the transform variable.

C: In the definition $F(s) = \int_0^\infty e^{-st}f(t)\,dt$, the lower limit of integration is $[0]$, which is why the Laplace transform is well-suited to initial-value problems.

Q: Why is the Laplace transform an improper integral, and what does that require?
A: The upper limit is $\infty$, so $F(s) = \lim_{b\to\infty}\int_0^b e^{-st}f(t)\,dt$. For this limit to exist the integrand must decay fast enough as $t\to\infty$, which is ensured by choosing $s$ large enough. This is why $F(s)$ is only defined on a half-plane $s > c$ rather than for all $s$.

Q: Why does the Laplace transform take a function of $t$ and produce a function of $s$?
A: The variable $t$ is integrated out (it is a dummy variable in the definite integral), so the result depends only on the parameter $s$ appearing in the kernel $e^{-st}$. We write $\mathcal{L}\{f(t)\} = F(s)$ to emphasize this change of domain.

## 10.2 Why the Laplace Transform Helps with ODEs

Q: Why does the Laplace transform simplify linear ODEs with constant coefficients?
A: It converts differentiation in $t$ into multiplication by $s$ (plus initial-condition terms), so a linear ODE becomes a linear algebraic equation in $F(s)$. We then solve algebraically for $F(s)$ and invert the transform to recover $y(t)$. It also handles initial conditions automatically, eliminating the need to separately determine constants.

C: The Laplace transform is especially powerful because it converts [differentiation] in $t$ into multiplication by $s$, turning an ODE into an algebraic equation.

Q: What three-step strategy underlies every Laplace-transform solution of an ODE?
A: (1) Transform both sides of the ODE, using the derivative rules to incorporate initial conditions. (2) Solve the resulting algebraic equation for $F(s) = \mathcal{L}\{y(t)\}$. (3) Invert $F(s)$ to recover $y(t)$, usually via partial fractions and a table of known transforms.

## 10.3 Linearity of the Laplace Transform

C: The Laplace transform is [linear]: $\mathcal{L}\{af(t) + bg(t)\} = aF(s) + bG(s)$ for constants $a,b$, where $F = \mathcal{L}\{f\}$ and $G = \mathcal{L}\{g\}$.

Q: Why is linearity of $\mathcal{L}$ essentially automatic from its definition?
A: Because $\mathcal{L}$ is defined by an integral, and integration is a linear operation. Constants pull out of integrals and sums of integrands split into sums of integrals, so $\mathcal{L}$ inherits linearity directly.

## 10.4 Core Transform Table

C: $\mathcal{L}\{1\} = [1/s]$ for $s > 0$, obtained by integrating $\int_0^\infty e^{-st}\,dt$.

C: $\mathcal{L}\{t^n\} = [n!/s^{n+1}]$ for $s > 0$ and non-negative integer $n$.

C: $\mathcal{L}\{e^{at}\} = [1/(s-a)]$ for $s > a$, where $a$ is a real constant.

C: $\mathcal{L}\{\sin bt\} = [b/(s^2+b^2)]$ for $s > 0$, where $b$ is the angular frequency.

C: $\mathcal{L}\{\cos bt\} = [s/(s^2+b^2)]$ for $s > 0$, where $b$ is the angular frequency.

C: $\mathcal{L}\{\sinh at\} = [a/(s^2-a^2)]$ for $s > |a|$, where $a$ is a real constant.

C: $\mathcal{L}\{\cosh at\} = [s/(s^2-a^2)]$ for $s > |a|$, where $a$ is a real constant.

Q: Why does $\mathcal{L}\{e^{at}\} = 1/(s-a)$ only converge for $s > a$?
A: The integrand is $e^{-(s-a)t}$, which decays at infinity iff $s - a > 0$. For $s \le a$ the integral diverges, so the transform is defined only on the half-plane $s > a$.

Q: Why do the transforms of $\sin bt$ and $\cos bt$ share the denominator $s^2 + b^2$?
A: Both can be written using Euler's formula $e^{ibt} = \cos bt + i\sin bt$, whose Laplace transform is $1/(s - ib)$. Rationalizing the denominator gives $(s + ib)/(s^2 + b^2)$; the real part yields $\cos$ and the imaginary part yields $\sin$, so they share the denominator $s^2 + b^2$.

## 10.5 Conditions for Existence

C: A function $f$ is of [exponential order] $c$ if there exist constants $M, c$ such that $|f(t)| \le M e^{ct}$ for all $t \ge 0$.

C: A function is [piecewise continuous] on $\lbrack 0,\infty)$ if on every finite subinterval it has at most finitely many jump discontinuities and is continuous elsewhere.

Q: Why do piecewise continuity and exponential order guarantee that $F(s)$ exists?
A: Piecewise continuity ensures the integrand is integrable over any finite interval. Exponential order bounds $|f(t)| \le Me^{ct}$, so $|e^{-st}f(t)| \le Me^{-(s-c)t}$, which is integrable on $[0,\infty)$ whenever $s > c$. Together they make the improper integral converge for all sufficiently large $s$.

Q: Why do we usually not worry about existence when applying the Laplace transform to ODEs in practice?
A: The forcing functions we meet in applied ODEs (polynomials, exponentials, sines, cosines, step functions, and their products) are all piecewise continuous and of exponential order. The existence theorem guarantees their transforms exist on some half-plane $s > c$, so we can apply the method freely.

## 10.6 Transform of Derivatives

C: $\mathcal{L}\{f'(t)\} = [sF(s) - f(0)]$, where $F(s) = \mathcal{L}\{f(t)\}$ and $f(0)$ is the initial value of $f$.

C: $\mathcal{L}\{f''(t)\} = [s^2 F(s) - s f(0) - f'(0)]$, where $f(0)$ and $f'(0)$ are the initial position and initial velocity.

C: In general, $\mathcal{L}\{f^{(n)}(t)\} = s^n F(s) - s^{n-1}f(0) - s^{n-2}f'(0) - \cdots - [f^{(n-1)}(0)]$, where $f^{(k)}(0)$ is the $k$-th derivative of $f$ at $t = 0$.

Q: Where does the $-f(0)$ term in $\mathcal{L}\{f'\}$ come from?
A: Integration by parts on $\int_0^\infty e^{-st}f'(t)\,dt$ gives $[e^{-st}f(t)]_0^\infty + s\int_0^\infty e^{-st}f(t)\,dt$. The boundary term at $\infty$ vanishes (assuming $f$ has exponential order and $s$ is large), and the boundary term at $0$ contributes $-f(0)$, leaving $sF(s) - f(0)$.

Q: Why does the derivative rule automatically build initial conditions into the algebra?
A: Each derivative brings a power of $s$ plus terms involving $f(0), f'(0), \ldots$. When we transform an ODE, these initial-condition terms appear as constants on the algebraic side. Solving for $F(s)$ produces a formula already specialized to the given initial data — no undetermined constants remain.

## 10.7 First Shift Theorem (s-Shift)

C: First shift theorem: $\mathcal{L}\{e^{at}f(t)\} = [F(s-a)]$, where $F(s) = \mathcal{L}\{f(t)\}$ and $a$ is a constant.

Q: Why does multiplying $f(t)$ by $e^{at}$ translate $F(s)$ by $a$?
A: The definition gives $\mathcal{L}\{e^{at}f(t)\} = \int_0^\infty e^{-st}e^{at}f(t)\,dt = \int_0^\infty e^{-(s-a)t}f(t)\,dt$, which is exactly $F$ evaluated at $s - a$. An exponential factor in $t$-space becomes a rigid shift in $s$-space.

Q: Which common transform pairs come directly from applying the first shift theorem to $\sin bt$ and $\cos bt$?
A: Multiplying by $e^{at}$ shifts $s \mapsto s - a$: $\mathcal{L}\{e^{at}\sin bt\} = b/((s-a)^2 + b^2)$ and $\mathcal{L}\{e^{at}\cos bt\} = (s-a)/((s-a)^2 + b^2)$. These are exactly the transforms associated with damped oscillations.

## 10.8 Heaviside (Unit Step) Function and Second Shift

C: The [Heaviside step function] $u_c(t)$ equals $0$ for $t < c$ and $1$ for $t \ge c$, where $c \ge 0$ is the switch-on time.

C: $\mathcal{L}\{u_c(t)\} = [e^{-cs}/s]$ for $s > 0$, where $c$ is the switch-on time.

Q: Why does the Heaviside function matter in ODE modeling?
A: It models forcing terms that switch on or off at specific times — a voltage applied at $t = c$, a force applied suddenly, or a source turned off. Without $u_c$, we would need piecewise-defined ODEs; with $u_c$, we can write a single formula and apply the Laplace transform directly.

C: Second shift theorem (t-shift): $\mathcal{L}\{u_c(t) f(t-c)\} = [e^{-cs} F(s)]$, where $F(s) = \mathcal{L}\{f(t)\}$ and $c \ge 0$ is the delay.

Q: Why does the second shift theorem require the $u_c(t)$ factor instead of just $f(t-c)$?
A: The Laplace integral runs from $t = 0$, and $f(t-c)$ alone would include values of $f$ at negative arguments, which are usually undefined. Multiplying by $u_c(t)$ zeroes out the shifted function before $t = c$, so the transform cleanly becomes $e^{-cs}F(s)$.

Q: Contrast the first and second shift theorems: what does each shift, and in which domain?
A: The first shift theorem ($\mathcal{L}\{e^{at}f(t)\} = F(s-a)$) shifts in the $s$-domain — multiplying by $e^{at}$ in $t$ translates $F$. The second shift theorem ($\mathcal{L}\{u_c(t)f(t-c)\} = e^{-cs}F(s)$) shifts in the $t$-domain — a delayed version of $f$ picks up a factor $e^{-cs}$ in $s$.

## 10.9 Dirac Delta Function

C: The [Dirac delta] $\delta(t-c)$ is the formal limit of tall, narrow pulses of unit area centered at $t = c$, modeling an instantaneous impulse.

C: $\mathcal{L}\{\delta(t-c)\} = [e^{-cs}]$ for $c \ge 0$.

Q: Why does modeling an impulse with $\delta(t-c)$ lead to $\mathcal{L}\{\delta(t-c)\} = e^{-cs}$ rather than a rational function?
A: $\delta(t-c)$ has the sifting property $\int_0^\infty g(t)\delta(t-c)\,dt = g(c)$. Applying this with $g(t) = e^{-st}$ gives $e^{-sc}$. The result is not rational because $\delta$ is not an ordinary function — its transform encodes only the location of the impulse, not any continuous decay.

Q: What physical situation is modeled by $m y'' + ky = \delta(t-c)$?
A: A mass-spring system at rest struck by an instantaneous impulse at time $t = c$ (like a hammer blow). Before $t = c$ nothing drives the system; at $t = c$ the impulse imparts a sudden unit change in momentum, and the system then oscillates freely.

## 10.10 Transform of $t^n f(t)$ and $f(t)/t$

C: $\mathcal{L}\{t f(t)\} = [-F'(s)]$, where $F(s) = \mathcal{L}\{f(t)\}$ and $F'$ denotes differentiation with respect to $s$.

C: More generally, $\mathcal{L}\{t^n f(t)\} = [(-1)^n F^{(n)}(s)]$, where $F^{(n)}$ is the $n$-th derivative of $F$ with respect to $s$.

Q: Why does multiplying $f(t)$ by $t$ correspond to differentiating $F(s)$ in $s$?
A: Differentiating $F(s) = \int_0^\infty e^{-st}f(t)\,dt$ under the integral with respect to $s$ brings down a factor of $-t$: $F'(s) = -\int_0^\infty t e^{-st}f(t)\,dt = -\mathcal{L}\{tf(t)\}$. Repeating gives $(-1)^n F^{(n)}(s) = \mathcal{L}\{t^n f(t)\}$.

C: Under appropriate convergence, $\mathcal{L}\{f(t)/t\} = [\int_s^\infty F(\sigma)\,d\sigma]$, where $F(\sigma) = \mathcal{L}\{f(t)\}$ evaluated at $\sigma$.

Q: When is the formula $\mathcal{L}\{f(t)/t\} = \int_s^\infty F(\sigma)\,d\sigma$ valid?
A: It requires that $f(t)/t$ actually have a Laplace transform — in particular that $\lim_{t\to 0^+} f(t)/t$ exist (or the singularity be mild enough that the integral converges). A typical working example is $\mathcal{L}\{\sin(t)/t\} = \arctan(1/s)$.

## 10.11 Inverse Laplace Transform

C: The inverse Laplace transform is written $\mathcal{L}^{-1}\{F(s)\} = [f(t)]$ and is also linear: $\mathcal{L}^{-1}\{aF + bG\} = af + bg$.

Q: Why is the inverse Laplace transform essentially unique in practice?
A: Lerch's theorem says that if two piecewise-continuous functions of exponential order have the same Laplace transform, they are equal at every point of continuity. For the functions we encounter in ODEs, this uniqueness lets us read off $f(t)$ from $F(s)$ using a table without ambiguity.

Q: What is the standard strategy for computing an inverse Laplace transform by hand?
A: (1) Simplify $F(s)$ using partial fractions to break it into pieces that match entries in the transform table. (2) Apply linearity to invert each piece separately. (3) Use shift theorems or $t^n$/$f/t$ rules to handle pieces that differ from a table entry by a shift or algebraic factor.

## 10.12 Partial Fractions for Inversion

Q: Why are partial fractions the natural tool for inverting rational $F(s)$?
A: The transform table consists of simple rational building blocks: $1/(s-a)$, $1/(s-a)^n$, $b/((s-a)^2+b^2)$, etc. Partial fractions decompose a general rational $F(s)$ into exactly these building blocks, so linearity of $\mathcal{L}^{-1}$ reduces the problem to reading off each piece from the table.

C: After partial fractions, the inverse transform of $[A/(s-a)]$ is $Ae^{at}$, where $A$ is the residue coefficient and $a$ is the pole.

Q: How do repeated linear factors $(s-a)^n$ appear in partial fractions and what is their inverse?
A: A factor $(s-a)^n$ in the denominator contributes terms $A_1/(s-a) + A_2/(s-a)^2 + \cdots + A_n/(s-a)^n$. Using $\mathcal{L}\{t^{k-1}e^{at}/(k-1)!\} = 1/(s-a)^k$, each piece inverts to a polynomial-times-exponential term.

## 10.13 Completing the Square in the Denominator

Q: Why is completing the square essential when inverting transforms with irreducible quadratic denominators?
A: Transforms of $e^{at}\sin bt$ and $e^{at}\cos bt$ have denominator $(s-a)^2 + b^2$. A raw quadratic $s^2 + ps + q$ must first be rewritten in this form by completing the square; only then can we apply the first shift theorem to match the table and recognize a damped oscillation.

C: To invert a term like $1/(s^2 + 4s + 13)$, we [complete the square] to get $1/((s+2)^2 + 9)$, matching $\mathcal{L}\{e^{-2t}\sin(3t)\}/3$.

Q: What does completing the square in the denominator tell you physically about the time-domain solution?
A: If $F(s)$ has denominator $(s-a)^2 + b^2$, the time-domain solution contains $e^{at}\cos bt$ and $e^{at}\sin bt$. The real part $a$ sets the exponential decay/growth rate and the imaginary part $b$ sets the oscillation frequency — exactly the damped-oscillator structure from earlier chapters.

## 10.14 Worked Example: Inverse via Completing the Square

P: Compute $\mathcal{L}^{-1}\left\{\dfrac{2s + 3}{s^2 + 4s + 13}\right\}$.

S:
**IDENTIFY**: Inverse Laplace transform of a rational function whose denominator is an irreducible quadratic (discriminant $16 - 52 < 0$). The target forms in the table are $\mathcal{L}\{e^{at}\cos bt\} = (s-a)/((s-a)^2+b^2)$ and $\mathcal{L}\{e^{at}\sin bt\} = b/((s-a)^2+b^2)$, where $a$ is the decay rate and $b$ is the angular frequency.

**PLAN**:
- Complete the square in the denominator to expose the shifted form $(s-a)^2 + b^2$.
- Rewrite the numerator as a linear combination of $(s-a)$ and a constant so each piece matches a table entry.
- Apply linearity and the first shift theorem.

**EXECUTE**:
1. Complete the square: $s^2 + 4s + 13 = (s+2)^2 + 9$, so $a = -2$ and $b = 3$.
2. Rewrite the numerator in terms of $(s+2)$: $2s + 3 = 2(s+2) - 1$.
3. Split the fraction:
$$\frac{2s+3}{(s+2)^2 + 9} = 2\cdot\frac{s+2}{(s+2)^2 + 9} - \frac{1}{3}\cdot\frac{3}{(s+2)^2 + 9}.$$
4. Invert each piece using the first shift theorem ($s \mapsto s - (-2)$, i.e., multiply by $e^{-2t}$):
$$\mathcal{L}^{-1}\left\{\frac{s+2}{(s+2)^2+9}\right\} = e^{-2t}\cos(3t), \qquad \mathcal{L}^{-1}\left\{\frac{3}{(s+2)^2+9}\right\} = e^{-2t}\sin(3t).$$
5. Combine: $f(t) = 2e^{-2t}\cos(3t) - \tfrac{1}{3}e^{-2t}\sin(3t)$.

**EVALUATE**:
- Check at $t = 0$: $f(0) = 2\cos 0 - \tfrac13\sin 0 = 2$, which matches $\lim_{s\to\infty} sF(s) = \lim_{s\to\infty}(2s^2 + 3s)/(s^2 + 4s + 13) = 2$ (initial-value theorem). ✓
- The solution is a damped oscillation with decay rate $2$ and frequency $3$, consistent with the complex roots $s = -2 \pm 3i$ of $s^2 + 4s + 13 = 0$. ✓

## 10.15 Convolution

C: The [convolution] of $f$ and $g$ is $(f*g)(t) = \int_0^t f(\tau) g(t-\tau)\,d\tau$, where $\tau$ is a dummy integration variable ranging over $\lbrack 0,t\rbrack $.

C: Convolution theorem: $\mathcal{L}\{(f*g)(t)\} = [F(s)\,G(s)]$, where $F = \mathcal{L}\{f\}$ and $G = \mathcal{L}\{g\}$.

Q: Why is the convolution theorem so valuable for ODEs?
A: When we solve an ODE via Laplace, the transform of the solution often comes out as a product $F(s)G(s)$ — for example, a transfer function times the transform of the forcing term. Rather than doing partial fractions on that product, we can invert each factor separately and express the answer as $(f*g)(t)$, which directly shows the "response $f$ convolved with the input $g$" structure.

Q: What is the physical interpretation of $(f*g)(t)$ when $g$ is a forcing term and $f$ is the impulse response?
A: The output at time $t$ is the accumulated effect of all past inputs $g(\tau)$, each weighted by how much of the impulse response $f(t-\tau)$ remains at time $t$. Convolution is a running "weighted memory" of the forcing history.

Q: Why is convolution commutative, i.e. $(f*g)(t) = (g*f)(t)$?
A: It follows from the substitution $\tau \mapsto t - \tau$ in the defining integral. Physically, treating either function as the input and the other as the impulse response gives the same output — the roles are mathematically symmetric.

## 10.16 Putting It Together

Q: Summarize the overall Laplace-transform method for solving a constant-coefficient linear ODE with initial conditions.
A: (1) Transform the ODE, using $\mathcal{L}\{y^{(n)}\} = s^n Y(s) - s^{n-1}y(0) - \cdots - y^{(n-1)}(0)$ to bake in the initial conditions. (2) Collect terms to solve algebraically for $Y(s)$. (3) Simplify $Y(s)$ using partial fractions and, as needed, complete the square to match table entries. (4) Apply $\mathcal{L}^{-1}$, using shift theorems and possibly convolution, to recover $y(t)$.

Q: Why is the Laplace method especially well-suited to problems with discontinuous or impulsive forcing?
A: Functions like $u_c(t)$ and $\delta(t-c)$ have simple transforms ($e^{-cs}/s$ and $e^{-cs}$), and the second shift theorem handles delays cleanly. Classical methods (undetermined coefficients, variation of parameters) have to split the problem at every discontinuity and patch solutions together; Laplace handles the whole problem in one algebraic stroke.
