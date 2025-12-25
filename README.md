# Roots modulo p(rime)

## Quadratic residues and nonresidues

Let $p$ an odd prime and $g$ a generator for $Z_{p}^{\ast}$. $(g^{m})^{2} = g^{2m} \equiv a \mod p$ maps all the exponents which are multiples of $2$ inside $\\{ 1, 2, \dots, p - 1 \\}$, and therefore $(p - 1) / 2$ values [half of $Z_{p}^{\ast}$ values]. These values $(a)$ are called **quadratic residues**. All other values are called **quadratic nonresidues**.

## Euler's Criterion

It's simple to misinterpret Euler's Criterion. This one doesn't try to prove anything about what is a quadratic residue and what is a quadratic nonresidue. Indeed, we already know it. If we have $g^{k} \equiv a \mod p$ then $a$ is a **quadratic residue** if $k$ is **even**. Otherwise, if $k$ is **odd** then we have a quadratic nonresidue. But now, say we have $7 \mod 79$ with $79$ prime. How can you say if $7$ is a quadratic residue or not? We need some calculation to prove it. And this is exactly what Euler's Criterion does. It finds a calculation.

Consider $g^{k} \equiv a \mod p$. If $k$ is **odd** (then $a$ would be a quadratic nonresidue **but we don't know it**) then $k = 2m + 1$ and

```math
a^{(p - 1) / 2} = (g^{(2m + 1)})^{(p - 1) / 2} = g^{[2m(p - 1) / 2] + [(p - 1) / 2]} = g^{m(p - 1)}g^{(p - 1) / 2} \equiv 1 \cdot g^{(p - 1) / 2} = g^{(p - 1) / 2}
```

Now $g^{p - 1}$ is the square of $g^{(p - 1) / 2}$. This means that $g^{(p - 1) / 2}$ is either $1$ or $- 1$, but since the order of $g \mod p$ is $p - 1$, then $g^{(p - 1) / 2} \equiv - 1 \mod p$ **and** $a^{(p - 1) / 2} \equiv - 1 \mod p$. This means that if $k$ is odd, then since $ $ $a^{(p - 1) / 2}$ is a **quadratic $(g^{k} \equiv a)$

> To better understand this last conclusion, note that the only element of order $2$ (modulo a prime odd number) is **always** $- 1$, that is $p - 1$. Indeed there are always $\phi(\phi(p) / [ \phi(p) / 2 ]) = 1$ subgroups of order $2$ [if the group has generators].

