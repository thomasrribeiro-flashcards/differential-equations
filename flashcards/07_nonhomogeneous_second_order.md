+++
order = 7
subject = "Mathematics"
tags = ["math", "differential-equations", "ode", "nonhomogeneous", "undetermined-coefficients", "variation-of-parameters"]
+++

# Differential Equations — Nonhomogeneous Second-Order Equations

## 7.1 Structure of the General Solution

Q: Why can the general solution of $ay'' + by' + cy = g(x)$ be written as a sum of two pieces?
A: The equation is linear, so the difference of any two solutions satisfies the homogeneous equation. Thus every solution is a fixed particular solution plus some homogeneous solution. This decomposes the problem: solve the homogeneous part once, then find any single solution of the forced equation.

C: The general solution of $ay'' + by' + cy = g(x)$ is $y = [y_c + y_p]$, where $y_c$ is the complementary (homogeneous) solution and $y_p$ is any particular solution.

C: In $y = y_c + y_p$, the function $y_c$ is called the [complementary solution] and solves $ay'' + by' + cy = 0$.

C: In $y = y_c + y_p$, the function $y_p$ is called a [particular solution] and is any single function satisfying $ay'' + by' + cy = g(x)$.

Q: What role do the two arbitrary constants in the general solution play?
A: They sit in the complementary solution $y_c = c_1 y_1 + c_2 y_2$ and are fixed later by the initial conditions. The particular solution $y_p$ carries no free constants because any specific solution of the nonhomogeneous equation will do.

## 7.2 Why $y = y_c + y_p$ Works

Q: Using linearity, why does $y = y_c + y_p$ solve $L[y] = g$, where $L = a\tfrac{d^2}{dx^2} + b\tfrac{d}{dx} + c$?
A: Because $L$ is linear, $L[y_c + y_p] = L[y_c] + L[y_p]$. By construction $L[y_c] = 0$ and $L[y_p] = g$, so the sum gives $0 + g = g$. Linearity is exactly what lets us split the problem into homogeneous and particular pieces.

C: The operator $L\lbrack y\rbrack  = ay'' + by' + cy$ is [linear], meaning $L\lbrack \alpha u + \beta v\rbrack  = \alpha L\lbrack u\rbrack  + \beta L\lbrack v\rbrack $ for constants $\alpha, \beta$ and functions $u, v$.

Q: If $y_{p,1}$ and $y_{p,2}$ are both particular solutions of $L[y] = g$, what is $y_{p,1} - y_{p,2}$?
A: It is a solution of the homogeneous equation $L[y] = 0$, because $L[y_{p,1} - y_{p,2}] = g - g = 0$. This is why any one particular solution, combined with the full $y_c$, captures every solution.

## 7.3 Method of Undetermined Coefficients

Q: What is the core idea of the method of undetermined coefficients?
A: Guess a form for $y_p$ that mirrors the shape of the forcing function $g(x)$, with unknown coefficients. Substitute into the ODE and match coefficients of like terms to solve for the unknowns. It works because the derivatives of polynomials, exponentials, and sines/cosines stay within the same family.

Q: For which forcing functions $g(x)$ does undetermined coefficients work cleanly?
A: Polynomials, exponentials $e^{\alpha x}$, sines and cosines $\sin\beta x$, $\cos\beta x$, and finite sums or products of these. These families are closed under differentiation, so a structured guess closes the algebra.

Q: Why does the method fail for forcing terms like $\tan x$ or $1/x$?
A: Their derivatives do not stay in a finite-dimensional family of simple functions, so no fixed-form guess with finitely many coefficients can match. Variation of parameters is needed instead.

## 7.4 The Guess Table

C: If $g(x) = P_n(x)$, a polynomial of degree $n$, guess $y_p = [A_n x^n + A_{n-1} x^{n-1} + \dots + A_0]$, a polynomial of the same degree with undetermined coefficients.

C: If $g(x) = e^{\alpha x}$ with constant $\alpha$, guess $y_p = [A e^{\alpha x}]$, where $A$ is the undetermined coefficient.

C: If $g(x) = \sin\beta x$ or $\cos\beta x$, guess $y_p = [A\cos\beta x + B\sin\beta x]$, including BOTH sine and cosine terms.

Q: When $g(x) = \sin\beta x$, why must the guess include both $\cos\beta x$ and $\sin\beta x$?
A: Because differentiation mixes sines and cosines: $\tfrac{d}{dx}\sin\beta x = \beta\cos\beta x$. A guess with only $\sin\beta x$ cannot produce the cosine terms that arise from $y'$, so matching coefficients would be impossible.

C: If $g(x) = e^{\alpha x}\sin\beta x$, guess $y_p = [e^{\alpha x}(A\cos\beta x + B\sin\beta x)]$, where $\alpha, \beta$ are the given real constants.

Q: What is the guess for $g(x) = x e^{\alpha x}$?
A: $y_p = (A_1 x + A_0) e^{\alpha x}$. Multiplying a polynomial of degree $n$ by $e^{\alpha x}$ produces a guess that is a polynomial of the same degree $n$ times $e^{\alpha x}$.

Q: What is the guess for $g(x) = P_n(x) e^{\alpha x}\cos\beta x$ (before checking the modification rule)?
A: $y_p = e^{\alpha x}\big[Q_n(x)\cos\beta x + R_n(x)\sin\beta x\big]$, where $Q_n$ and $R_n$ are polynomials of degree $n$ with undetermined coefficients. Both sine and cosine must appear because differentiation mixes them.

## 7.5 The Modification Rule

C: If any term of the naive guess for $y_p$ is already a solution of the homogeneous equation, multiply the entire guess by [$x$]. If the match is with a repeated root, multiply by [$x^2$] instead.

Q: State the modification rule in one sentence.
A: Whenever the standard guess for $y_p$ overlaps the complementary solution $y_c$, multiply the guess by the smallest power of $x$ (either $x$ or $x^2$) needed to remove the overlap, then proceed as usual.

Q: When does multiplication by $x^2$ (rather than $x$) become necessary in the modification rule?
A: When the exponent in the guess matches a double (repeated) root of the characteristic equation. One factor of $x$ is "used up" by each repeated root, so two are needed to escape the homogeneous solution space.

## 7.6 Why the Modification Is Needed

Q: Why does the naive guess fail when it is already a homogeneous solution?
A: Because substituting a homogeneous solution into $L[y]$ gives $0$, not $g(x)$. No choice of the undetermined coefficient can turn $0$ into a nonzero $g$, so the algebra forces a contradiction like $0 = g$. Multiplying by $x$ produces a genuinely new function outside the homogeneous solution space.

Q: If you tried $y_p = A e^{\alpha x}$ when $e^{\alpha x}$ is already in $y_c$, what equation for $A$ would you get?
A: You would get $0 \cdot A = g(x)$ after substitution, which has no solution for $A$ unless $g \equiv 0$. This is the algebraic signature that tells you to apply the modification rule.

## 7.7 Superposition for Forcing

Q: If $g(x) = g_1(x) + g_2(x)$, how should you organize the search for $y_p$?
A: Solve $L[y_{p,1}] = g_1$ and $L[y_{p,2}] = g_2$ separately, then add: $y_p = y_{p,1} + y_{p,2}$. Linearity guarantees the sum satisfies $L[y_p] = g_1 + g_2 = g$, and each sub-problem uses the simplest guess.

C: If $g = g_1 + g_2$ and $L[y_{p,i}] = g_i$, then by superposition a particular solution of $L[y] = g$ is $y_p = [y_{p,1} + y_{p,2}]$.

Q: Why is superposition of forcing especially useful in practice?
A: It lets you apply the guess table and modification rule to each piece of $g$ independently. A complicated $g$ becomes several small, manageable problems instead of one algebraic mess.

## 7.8 Worked Example: $y'' - y = e^x$

Q: For $y'' - y = e^x$, what is the complementary solution $y_c$?
A: The characteristic equation $r^2 - 1 = 0$ gives roots $r = \pm 1$, so $y_c = c_1 e^x + c_2 e^{-x}$, where $c_1, c_2$ are arbitrary constants.

Q: For $y'' - y = e^x$, why does the naive guess $y_p = A e^x$ fail?
A: Because $e^x$ is already a homogeneous solution, so $L[A e^x] = 0 \neq e^x$. The modification rule requires multiplying by $x$, giving the corrected guess $y_p = A x e^x$.

P: Solve $y'' - y = e^x$ using undetermined coefficients.

S:
**IDENTIFY**: Nonhomogeneous second-order linear ODE with constant coefficients; forcing $g(x) = e^x$ with $e^x$ already in the homogeneous solution space.

**PLAN**:
- Solve the homogeneous equation $y'' - y = 0$ to get $y_c$.
- Try $y_p = A e^x$; detect the overlap with $y_c$; apply the modification rule with the factor $x$.
- Substitute $y_p = A x e^x$ into the ODE and solve for $A$.
- Write $y = y_c + y_p$.

**EXECUTE**:
1. Characteristic equation: $r^2 - 1 = 0 \Rightarrow r = \pm 1$, so $y_c = c_1 e^x + c_2 e^{-x}$.
2. Overlap: $e^x \in y_c$, so guess $y_p = A x e^x$.
3. Compute $y_p' = A e^x + A x e^x$ and $y_p'' = 2A e^x + A x e^x$.
4. Substitute: $y_p'' - y_p = 2A e^x + A x e^x - A x e^x = 2A e^x$.
5. Match: $2A e^x = e^x \Rightarrow A = \tfrac{1}{2}$.
6. General solution: $y = c_1 e^x + c_2 e^{-x} + \tfrac{1}{2} x e^x$.

**EVALUATE**:
- Dimensionally consistent: $y_p$ has the same units as $y_c$.
- The $x e^x$ term correctly lies outside the homogeneous solution space.
- Plugging back, $y_p'' - y_p = e^x$ holds, confirming the answer.

## 7.9 Variation of Parameters: Setup

Q: What is the core idea of variation of parameters?
A: Start from two independent homogeneous solutions $y_1, y_2$ and let their coefficients become functions of $x$: assume $y_p = u_1(x) y_1(x) + u_2(x) y_2(x)$. Choosing $u_1, u_2$ cleverly turns the ODE into two first-order equations that are always solvable by integration.

C: In variation of parameters, the particular solution is written $y_p = [u_1(x) y_1(x) + u_2(x) y_2(x)]$, where $y_1, y_2$ are homogeneous solutions and $u_1, u_2$ are unknown functions of $x$.

Q: Why is variation of parameters more general than undetermined coefficients?
A: It works for any continuous forcing $g(x)$, because it produces $u_1, u_2$ by integration rather than by matching a fixed-form guess. The cost is evaluating integrals that may not be elementary.

## 7.10 The Auxiliary Condition and the Formulas

Q: In variation of parameters, why do we impose the auxiliary condition $u_1' y_1 + u_2' y_2 = 0$?
A: Plugging $y_p = u_1 y_1 + u_2 y_2$ into a second-order ODE produces one equation in two unknown functions, which is underdetermined. Imposing $u_1' y_1 + u_2' y_2 = 0$ adds a second equation, makes $y_p'$ and $y_p''$ simple, and lets us solve for $u_1'$ and $u_2'$ cleanly.

C: The auxiliary condition imposed in variation of parameters is $[u_1' y_1 + u_2' y_2 = 0]$, where $y_1, y_2$ are homogeneous solutions and $u_1, u_2$ are the unknown coefficient functions.

C: After imposing the auxiliary condition, variation of parameters yields $u_1' = [-y_2 g / W]$, where $W$ is the Wronskian of $y_1, y_2$ and $g$ is the forcing term in standard form $y'' + py' + qy = g$.

C: After imposing the auxiliary condition, variation of parameters yields $u_2' = [y_1 g / W]$, where $W$ is the Wronskian of $y_1, y_2$ and $g$ is the forcing term in standard form $y'' + py' + qy = g$.

C: In the variation of parameters formulas, $W$ denotes the [Wronskian] $W(y_1, y_2) = y_1 y_2' - y_1' y_2$.

Q: Why is the forcing normalized to the leading-coefficient-1 form $y'' + py' + qy = g$ before applying the variation of parameters formulas?
A: The derivation assumes a leading coefficient of $1$; if the ODE is $a(x) y'' + \dots = \tilde g(x)$, the effective forcing is $g = \tilde g/a$. Skipping the normalization produces $u_1', u_2'$ that are off by a factor of $a(x)$.

## 7.11 Integrating for $u_1$ and $u_2$

Q: Once $u_1'$ and $u_2'$ are known, how do you finish the variation of parameters computation?
A: Integrate each derivative: $u_1 = \int u_1'\, dx$ and $u_2 = \int u_2'\, dx$. Any constants of integration can be dropped because they only reproduce homogeneous solutions already captured by $y_c$. Then $y_p = u_1 y_1 + u_2 y_2$.

C: In variation of parameters, $u_1 = [\int -\dfrac{y_2 g}{W}\, dx]$ and $u_2 = \int \dfrac{y_1 g}{W}\, dx$.

Q: Why can we drop the constants of integration when computing $u_1$ and $u_2$?
A: A constant in $u_1$ adds a multiple of $y_1$ to $y_p$, and a constant in $u_2$ adds a multiple of $y_2$. Both are already in $y_c$, so they contribute nothing new. Choosing the constants to be zero yields the simplest particular solution.

## 7.12 When to Prefer Variation over Undetermined Coefficients

Q: When should you reach for variation of parameters instead of undetermined coefficients?
A: When $g(x)$ is outside the guess table — forcings like $\tan x$, $\sec x$, $\ln x$, $1/x$, or anything whose derivatives do not stay in a finite family of elementary functions. Undetermined coefficients cannot handle these, but variation of parameters reduces them to integration.

C: Variation of parameters is preferred over undetermined coefficients when $g(x)$ is of the form [$\tan x$, $\sec x$, $1/x$, $\ln x$], or any other function not representable by the guess table.

Q: What is the practical trade-off between undetermined coefficients and variation of parameters?
A: Undetermined coefficients is fast when the guess table applies: it replaces integration with algebra. Variation of parameters is universal but often produces harder integrals. For textbook-friendly $g$, prefer undetermined coefficients; otherwise use variation of parameters.

## 7.13 Applying Initial Conditions

Q: When solving an IVP for $ay'' + by' + cy = g(x)$, at what stage do you apply the initial conditions?
A: Only AFTER combining: form the full solution $y = y_c + y_p$ first, then apply $y(x_0) = y_0$ and $y'(x_0) = y_0'$ to determine the two constants $c_1, c_2$ in $y_c$. Applying them to $y_c$ alone would ignore the particular solution's contribution at $x_0$.

Q: Why does applying initial conditions to $y_c$ alone give the wrong constants?
A: Because $y_p(x_0)$ and $y_p'(x_0)$ are generally nonzero, so they shift the value and slope that $y_c$ needs to supply. The right constants must balance the ICs against $y_p$, not against zero.

C: For the IVP $ay'' + by' + cy = g(x)$ with $y(x_0) = y_0$, $y'(x_0) = y_0'$, the initial conditions are applied [after] forming $y = y_c + y_p$, not before.

## 7.14 Worked Example: $y'' + y = \sec x$

Q: For $y'' + y = \sec x$, why is undetermined coefficients unsuitable?
A: Because $\sec x$ is not a polynomial, exponential, sine, cosine, or product of these; its derivatives generate an infinite chain $\sec x\tan x$, $\sec x \tan^2 x + \sec^3 x$, etc. No finite-form guess closes the algebra, so variation of parameters is required.

Q: For $y'' + y = 0$, what are the standard $y_1, y_2$ and their Wronskian $W$?
A: $y_1 = \cos x$, $y_2 = \sin x$, and $W = y_1 y_2' - y_1' y_2 = \cos x\cdot\cos x - (-\sin x)\sin x = \cos^2 x + \sin^2 x = 1$, independent of $x$.

P: Solve $y'' + y = \sec x$ using variation of parameters.

S:
**IDENTIFY**: Nonhomogeneous second-order linear ODE in standard form (leading coefficient $1$) with forcing $g(x) = \sec x$ not in the guess table.

**PLAN**:
- Solve the homogeneous equation to get $y_1, y_2$ and $W$.
- Write $y_p = u_1 y_1 + u_2 y_2$ with the auxiliary condition $u_1' y_1 + u_2' y_2 = 0$.
- Use $u_1' = -y_2 g/W$ and $u_2' = y_1 g/W$.
- Integrate to find $u_1, u_2$ and assemble $y = y_c + y_p$.

**EXECUTE**:
1. Homogeneous: $r^2 + 1 = 0 \Rightarrow r = \pm i$, so $y_1 = \cos x$, $y_2 = \sin x$, and $y_c = c_1 \cos x + c_2 \sin x$.
2. Wronskian: $W = \cos^2 x + \sin^2 x = 1$.
3. $u_1' = -\dfrac{\sin x \cdot \sec x}{1} = -\tan x$, so $u_1 = \int -\tan x\, dx = \ln|\cos x|$.
4. $u_2' = \dfrac{\cos x \cdot \sec x}{1} = 1$, so $u_2 = \int 1\, dx = x$.
5. Particular solution: $y_p = \cos x \cdot \ln|\cos x| + x \sin x$.
6. General solution: $y = c_1 \cos x + c_2 \sin x + \cos x\, \ln|\cos x| + x \sin x$.

**EVALUATE**:
- The presence of $\ln|\cos x|$ and $x\sin x$ confirms we are outside the guess table, consistent with using variation of parameters.
- Differentiating $y_p$ twice and adding yields $\sec x$, as required.
- Constants of integration were dropped in $u_1, u_2$ because they would only reproduce multiples of $\cos x$ and $\sin x$, already captured in $y_c$.

## 7.15 Worked Example: Undetermined Coefficients with $y'' - 3y' + 2y = 4e^{3x}$

Q: For $y'' - 3y' + 2y = 4 e^{3x}$, is $e^{3x}$ already a homogeneous solution?
A: The characteristic equation $r^2 - 3r + 2 = 0$ factors as $(r-1)(r-2) = 0$, giving roots $r = 1, 2$. Since $3$ is not a root, $e^{3x}$ is NOT in $y_c$, so the naive guess $y_p = A e^{3x}$ is safe without modification.

P: Solve $y'' - 3y' + 2y = 4 e^{3x}$ using undetermined coefficients.

S:
**IDENTIFY**: Nonhomogeneous second-order linear ODE with constant coefficients; forcing $g(x) = 4 e^{3x}$ is a pure exponential — guess table applies.

**PLAN**:
- Solve $y'' - 3y' + 2y = 0$ to get $y_c$.
- Check whether $e^{3x}$ overlaps $y_c$; it does not, so try $y_p = A e^{3x}$.
- Substitute into the ODE and solve for $A$.
- Combine: $y = y_c + y_p$.

**EXECUTE**:
1. Characteristic equation: $r^2 - 3r + 2 = 0 \Rightarrow r = 1, 2$, so $y_c = c_1 e^x + c_2 e^{2x}$.
2. Overlap check: $3 \notin \{1, 2\}$, so no modification needed. Guess $y_p = A e^{3x}$.
3. Derivatives: $y_p' = 3A e^{3x}$, $y_p'' = 9A e^{3x}$.
4. Substitute: $9A e^{3x} - 3(3A e^{3x}) + 2(A e^{3x}) = (9A - 9A + 2A) e^{3x} = 2A e^{3x}$.
5. Match forcing: $2A e^{3x} = 4 e^{3x} \Rightarrow A = 2$.
6. General solution: $y = c_1 e^x + c_2 e^{2x} + 2 e^{3x}$.

**EVALUATE**:
- No $x$-factor appears in $y_p$ because $3$ is not a characteristic root — consistent with the overlap check.
- Direct substitution: $y_p'' - 3y_p' + 2y_p = 18e^{3x} - 18 e^{3x} + 4 e^{3x} = 4 e^{3x}$ ✓.
- Units and structure match: $y_p$ is exponential of the same shape as $g$.

## 7.16 Comparing the Two Methods

Q: In one sentence, contrast undetermined coefficients and variation of parameters.
A: Undetermined coefficients matches a fixed algebraic guess to a structured $g$, while variation of parameters builds $y_p$ from integrals of the homogeneous solutions against an arbitrary $g$.

Q: For which of these forcings is undetermined coefficients appropriate: $g = x^2$, $g = e^{2x}\sin x$, $g = \ln x$, $g = \sec^2 x$?
A: Undetermined coefficients works for $g = x^2$ (polynomial) and $g = e^{2x}\sin x$ (exponential times sine). It fails for $g = \ln x$ and $g = \sec^2 x$, whose derivatives leave any finite guess family — variation of parameters is required.

Q: If both methods apply, why do we usually prefer undetermined coefficients?
A: It replaces integration with algebra: no integrals to evaluate, just linear equations for the undetermined coefficients. Variation of parameters, while always valid, often yields integrals that are tedious or non-elementary.
