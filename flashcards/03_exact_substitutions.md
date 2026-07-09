+++
order = 3
subject = "Math"
tags = ["math", "differential-equations", "ode", "exact", "bernoulli", "homogeneous-substitution", "first-order"]
+++

# Differential Equations — Exact Equations and Substitutions

## 3.1 Exact Equations

Q: Why is it useful to recognize when a first-order ODE is "exact"?
A: An exact equation is secretly the total differential of some function $F(x,y)$, so $M\,dx + N\,dy = 0$ becomes $dF = 0$, and the implicit solution is simply $F(x,y) = C$. This converts a differential equation into a pure integration problem, bypassing the need for separation or integrating factors.

C: A first-order ODE written in differential form is $M(x,y)\,dx + N(x,y)\,dy = 0$, where $M$ is the coefficient of $dx$ and $N$ is the [coefficient of $dy$].

C: The equation $M(x,y)\,dx + N(x,y)\,dy = 0$ is called [exact] when there exists a function $F(x,y)$ whose total differential equals $M\,dx + N\,dy$.

C: If $M\,dx + N\,dy = 0$ is exact with potential function $F(x,y)$, then $F_x = M$ and $F_y = [N]$, where $F_x$ and $F_y$ denote partial derivatives of $F$ with respect to $x$ and $y$.

Q: Why does exactness immediately give the implicit solution $F(x,y) = C$?
A: If $F_x = M$ and $F_y = N$, then along any solution curve $dF = F_x\,dx + F_y\,dy = M\,dx + N\,dy = 0$. A function whose differential is zero is constant, so $F(x,y) = C$ along every solution curve, where $C$ is the constant of integration.

## 3.2 Test for Exactness

Q: Before trying to construct $F(x,y)$, how do you check whether $M\,dx + N\,dy = 0$ is actually exact?
A: Compute the mixed partials $\partial M/\partial y$ and $\partial N/\partial x$. If they are equal (and $M, N$ have continuous partials on a simply connected region), the equation is exact. Otherwise no potential function $F$ exists and a different method is needed.

C: The exactness test for $M\,dx + N\,dy = 0$ is the equality of mixed partials: $\dfrac{\partial M}{\partial y} = \dfrac{\partial N}{\partial [x]}$.

Q: Why does the exactness test involve equality of mixed partial derivatives?
A: If $F$ exists with $F_x = M$ and $F_y = N$, then $M_y = F_{xy}$ and $N_x = F_{yx}$. For a $C^2$ function, Clairaut's theorem guarantees $F_{xy} = F_{yx}$, so $M_y$ must equal $N_x$. This necessary condition is also sufficient on a simply connected domain.

Q: Before checking exactness, predict: for the ODE $(2xy)\,dx + (x^2 + 1)\,dy = 0$, will the exactness test succeed?
A: Yes. $\partial M/\partial y = 2x$ and $\partial N/\partial x = 2x$, so the test passes. Predicting first builds intuition that "symmetric-looking" coefficient pairs are often exact.

## 3.3 Constructing the Potential Function $F$

Q: Once the exactness test passes, how do you actually find $F(x,y)$?
A: Integrate $M(x,y)$ with respect to $x$ (treating $y$ as constant) to get $F(x,y) = \int M\,dx + h(y)$, where $h(y)$ is an unknown function of $y$ alone (the "constant of integration" in $x$). Then differentiate this expression with respect to $y$ and equate to $N(x,y)$ to solve for $h'(y)$, then integrate to get $h(y)$.

C: After integrating $M$ in $x$, the potential function takes the form $F(x,y) = \int M(x,y)\,dx + [h(y)]$, where $h(y)$ is an unknown function of $y$ only.

C: To determine $h(y)$ in $F(x,y) = \int M\,dx + h(y)$, compute $\partial F/\partial y$ and set it equal to $[N(x,y)]$, then solve for $h'(y)$.

Q: Why does $h$ depend only on $y$ and not on $x$?
A: The term represents the constant of integration when integrating with respect to $x$. Anything not involving $x$ is "constant" from the $x$-integration's perspective, but it may still depend on $y$. Once we enforce $F_y = N$, $h$ is pinned down up to an additive true constant (absorbed into $C$).

P: Solve the exact ODE $(2xy + 3)\,dx + (x^2 - 1)\,dy = 0$ by constructing $F(x,y)$.

S:
**IDENTIFY**: First-order ODE in differential form; candidate for exactness.

**PLAN**:
- Check exactness: compare $\partial M/\partial y$ with $\partial N/\partial x$.
- If exact, integrate $M$ in $x$ to get $F + h(y)$.
- Match $\partial F/\partial y = N$ to find $h'(y)$, integrate for $h$.
- Write solution as $F(x,y) = C$.

**EXECUTE**:
1. $M = 2xy + 3$, $N = x^2 - 1$. Then $M_y = 2x$ and $N_x = 2x$, so exact.
2. Integrate $M$ in $x$: $F(x,y) = \int (2xy + 3)\,dx = x^2 y + 3x + h(y)$.
3. Differentiate in $y$: $F_y = x^2 + h'(y)$. Set equal to $N$: $x^2 + h'(y) = x^2 - 1$, so $h'(y) = -1$, hence $h(y) = -y$.
4. Implicit solution: $x^2 y + 3x - y = C$.

**EVALUATE**:
- Check: $d(x^2 y + 3x - y) = (2xy + 3)\,dx + (x^2 - 1)\,dy$, matching the original.
- The solution is implicit in general; solving for $y$ gives $y = (C - 3x)/(x^2 - 1)$ where defined.

## 3.4 Integrating Factors for Non-Exact Equations

Q: What do you do when $M\,dx + N\,dy = 0$ fails the exactness test?
A: Multiply both sides by an integrating factor $\mu(x,y)$ chosen so that $(\mu M)\,dx + (\mu N)\,dy = 0$ is exact. In general finding $\mu(x,y)$ is as hard as the original ODE, but special cases — where $\mu$ depends on only $x$ or only $y$ — are tractable.

C: To rescue a non-exact equation $M\,dx + N\,dy = 0$, multiply through by an [integrating factor] $\mu(x,y)$ chosen to make the result exact.

Q: When does an integrating factor depending only on $x$ exist for $M\,dx + N\,dy = 0$?
A: It exists when $(M_y - N_x)/N$ is a function of $x$ alone. Calling that function $P(x)$, the integrating factor is $\mu(x) = e^{\int P(x)\,dx}$.

C: If $\dfrac{M_y - N_x}{N}$ is a function of $x$ alone, call it $P(x)$; then the integrating factor depending only on $x$ is $\mu(x) = [e^{\int P(x)\,dx}]$.

Q: When does an integrating factor depending only on $y$ exist?
A: When $(N_x - M_y)/M$ is a function of $y$ alone — call it $Q(y)$ — the integrating factor is $\mu(y) = e^{\int Q(y)\,dy}$. Note the sign flip in the numerator compared to the $x$-only case.

Q: How is the integrating factor for a first-order linear ODE a special case of integrating factors for exactness?
A: Writing $y' + P(x)y = Q(x)$ as $(P(x)y - Q(x))\,dx + dy = 0$, the exactness test fails because $M_y = P(x)$ but $N_x = 0$. The ratio $(M_y - N_x)/N = P(x)$ depends only on $x$, so $\mu(x) = e^{\int P\,dx}$ — exactly the linear-ODE integrating factor from chapter 2.

## 3.5 Homogeneous Equations and the $v = y/x$ Substitution

Q: What does "homogeneous" mean in the first-order substitution sense, and how is it different from "homogeneous linear"?
A: Here "homogeneous" means the ODE can be written as $dy/dx = f(y/x)$ — the right side depends only on the ratio $y/x$, not on $x$ and $y$ separately. This is unrelated to the "homogeneous linear" sense of $y' + P(x)y = 0$, which describes linear ODEs with zero forcing.

C: A first-order ODE is homogeneous (in the substitution sense) if it can be written as $dy/dx = f([y/x])$, depending only on the ratio $y/x$.

C: To solve a homogeneous ODE $dy/dx = f(y/x)$, substitute $v = [y/x]$, so $y = vx$ and $dy/dx = v + x\,dv/dx$.

Q: After substituting $v = y/x$, why does $dy/dx = v + x\,dv/dx$ rather than just $dv/dx$?
A: Because $y = vx$ is a product of two things that depend on $x$ ($v$ depends on $x$ through $y$, and $x$ is itself the independent variable). The product rule gives $dy/dx = v \cdot 1 + x \cdot dv/dx$.

## 3.6 Why the $v = y/x$ Substitution Works

Q: Why does $v = y/x$ always convert a homogeneous ODE into a separable one?
A: After substitution, $v + x\,dv/dx = f(v)$, so $x\,dv/dx = f(v) - v$. This is separable: $\dfrac{dv}{f(v) - v} = \dfrac{dx}{x}$. The dependence on $y$ has been absorbed into $v$, leaving a $v$-only right-hand side divided by an $x$-only factor.

C: After $v = y/x$ in a homogeneous ODE $dy/dx = f(y/x)$, the transformed equation $\dfrac{dv}{f(v) - v} = \dfrac{dx}{[x]}$ is separable.

Q: Once you solve the separated ODE for $v$ in terms of $x$, how do you recover $y$?
A: Back-substitute $v = y/x$, i.e., replace $v$ with $y/x$ in the implicit or explicit solution. The final answer is expressed in the original variables $x$ and $y$.

## 3.7 Bernoulli Equations

C: A Bernoulli equation has the form $y' + P(x)y = Q(x)y^n$ with $n \neq [0, 1]$, where $P(x)$ and $Q(x)$ are given functions of $x$.

Q: Why are $n = 0$ and $n = 1$ excluded from the Bernoulli definition?
A: If $n = 0$ the equation is $y' + P(x)y = Q(x)$, a first-order linear ODE solvable directly by the integrating factor. If $n = 1$ the right side becomes $Q(x)y$, combining with $P(x)y$ to give $y' + (P - Q)y = 0$, which is linear and separable. Both reduce to chapter-2 methods without needing a substitution.

Q: What makes a Bernoulli equation non-linear and hence resistant to the chapter-2 integrating factor?
A: The $y^n$ on the right (with $n \neq 0, 1$) creates a non-linear dependence on $y$. The linear integrating factor $\mu = e^{\int P\,dx}$ relies on the equation being linear in $y$ and $y'$, which fails here.

## 3.8 The Bernoulli Substitution $v = y^{1-n}$

C: To linearize the Bernoulli equation $y' + P(x)y = Q(x)y^n$, substitute $v = [y^{1-n}]$, where $n$ is the Bernoulli exponent.

C: After the Bernoulli substitution, the new ODE in $v$ is the linear equation $v' + (1-n)P(x)v = [(1-n)Q(x)]$.

Q: What relationship between $v'$ and $y'$ does the Bernoulli substitution $v = y^{1-n}$ produce?
A: Differentiating, $v' = (1-n)y^{-n}y'$, so $y' = \dfrac{y^n}{1-n}v'$. This lets us replace $y'$ in the original ODE with an expression in $v'$ and $y^n$, which then cancels the non-linear $y^n$ term on the right.

## 3.9 Why the Bernoulli Substitution Works

Q: Why does $v = y^{1-n}$ specifically turn the $y^n$ term linear in $v$?
A: Dividing the Bernoulli equation by $y^n$ gives $y^{-n}y' + P(x)y^{1-n} = Q(x)$. The coefficient of $P$ is now $y^{1-n} = v$, and $y^{-n}y' = \dfrac{1}{1-n}v'$. So both non-linear terms become linear in $v$: $\dfrac{1}{1-n}v' + P(x)v = Q(x)$.

Q: After solving the linear ODE for $v$, how do you recover $y$?
A: Back-substitute using $v = y^{1-n}$, so $y = v^{1/(1-n)}$. Sign choices may matter when $1-n$ is even; check the original ODE and initial condition to pick the correct branch.

## 3.10 Recognizing Which Substitution to Use

Q: Given a non-separable, non-linear first-order ODE, what decision procedure picks the right method?
A: Step 1: put it in differential form $M\,dx + N\,dy = 0$ and test exactness ($M_y = N_x$); if exact, build $F$. Step 2: if not exact, check whether $(M_y - N_x)/N$ is a function of $x$ alone (or $(N_x - M_y)/M$ is $y$-only) for an integrating factor. Step 3: if $dy/dx$ can be written as $f(y/x)$, use $v = y/x$. Step 4: if it fits $y' + P(x)y = Q(x)y^n$, use Bernoulli's $v = y^{1-n}$.

C: The substitution $v = y/x$ is the go-to choice when $dy/dx$ depends only on the ratio [y/x].

C: The substitution $v = y^{1-n}$ is the go-to choice for equations of the form $y' + P(x)y = [Q(x)y^n]$ with $n \neq 0, 1$.

Q: How do you distinguish at a glance between a homogeneous-type ODE and a Bernoulli equation?
A: A homogeneous-type ODE has the whole right side expressible as $f(y/x)$ — a single function of the ratio. A Bernoulli equation has a specific additive structure: a linear-in-$y$ part plus a $y^n$ forcing term, with coefficients depending only on $x$.

P: Solve the Bernoulli ODE $y' + y = x y^3$ using the standard substitution.

S:
**IDENTIFY**: Bernoulli equation with $P(x) = 1$, $Q(x) = x$, and Bernoulli exponent $n = 3$ (so $n \neq 0, 1$).

**PLAN**:
- Substitute $v = y^{1-n} = y^{-2}$ to linearize.
- Transform the ODE into $v' + (1-n)P(x)v = (1-n)Q(x)$, i.e., $v' - 2v = -2x$.
- Solve the resulting linear ODE using the integrating factor $\mu = e^{\int -2\,dx} = e^{-2x}$.
- Back-substitute to recover $y$ via $y = v^{-1/2}$.

**EXECUTE**:
1. Let $v = y^{-2}$. Then $v' = -2y^{-3}y'$, so $y^{-3}y' = -\tfrac{1}{2}v'$.
2. Divide the original by $y^3$: $y^{-3}y' + y^{-2} = x$, i.e., $-\tfrac{1}{2}v' + v = x$, so $v' - 2v = -2x$.
3. Integrating factor: $\mu = e^{-2x}$. Multiply through: $(e^{-2x}v)' = -2x e^{-2x}$.
4. Integrate: $e^{-2x}v = \int -2x e^{-2x}\,dx = x e^{-2x} + \tfrac{1}{2}e^{-2x} + C$ (by parts with $u = -2x$, $dv = e^{-2x}dx$).
5. Hence $v = x + \tfrac{1}{2} + C e^{2x}$.
6. Back-substitute: $y^{-2} = x + \tfrac{1}{2} + C e^{2x}$, so $y = \pm\left(x + \tfrac{1}{2} + C e^{2x}\right)^{-1/2}$.

**EVALUATE**:
- The sign of $y$ is fixed by an initial condition; without one, both branches are valid where the base is positive.
- The $y \equiv 0$ solution is lost by the substitution (since $v = y^{-2}$ requires $y \neq 0$); check separately — $y \equiv 0$ satisfies the original ODE trivially.
- Units/consistency: the linear transformed ODE produced an exponential term, which is expected since the transformed equation had constant coefficient $-2$.
