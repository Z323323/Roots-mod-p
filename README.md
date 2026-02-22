# Some concepts regarding roots in multiplicative groups

## Quadratic residues and nonresidues

Let $p$ an odd prime and $g$ a generator for $Z_{p}^{\ast}$. $(g^{m})^{2} = g^{2m} \equiv a \mod p$ maps all the exponents which are multiples of $2$ inside $\\{ 1, 2, \dots, p - 1 \\}$, and therefore $(p - 1) / 2$ values [half of $Z_{p}^{\ast}$ values]. These values $(a)$ are called **quadratic residues**. All other values are called **quadratic nonresidues**.

## Euler's Criterion

It's simple to misinterpret Euler's Criterion. This one doesn't try to prove anything about what is a quadratic residue and what is a quadratic nonresidue. Indeed, we already know it. If we have $g^{k} \equiv a \mod p$ then $a$ is a **quadratic residue** if $k$ is **even**. Otherwise, if $k$ is **odd** then we have a quadratic nonresidue. But now, say we have $7 \mod 79$ with $79$ prime. How can you say if $7$ is a quadratic residue or not? We need some calculation to prove it. And this is exactly what Euler's Criterion does. It finds a calculation.

Consider $g^{k} \equiv a \mod p$. If $k$ is **odd** (then $a$ would be a quadratic nonresidue **but we don't know it**) then $k = 2m + 1$ and

```math
a^{(p - 1) / 2} = (g^{(2m + 1)})^{(p - 1) / 2} = g^{[2m(p - 1) / 2] + [(p - 1) / 2]} = g^{m(p - 1)}g^{(p - 1) / 2} \equiv 1 \cdot g^{(p - 1) / 2} = g^{(p - 1) / 2} \mod p
```

Now $g^{p - 1}$ is the square of $g^{(p - 1) / 2}$. This means that $g^{(p - 1) / 2}$ is either $1$ or $- 1$, but since the order of $g \mod p$ is $p - 1$, then $g^{(p - 1) / 2} \equiv - 1 \mod p$ **and** $a^{(p - 1) / 2} \equiv - 1 \mod p$. This means that if $k$ is **odd**, that is, **$a$ is a quadratic non residue** then

```math
a^{(p - 1) / 2} \equiv - 1 \equiv p - 1 \mod p \iff a_{\_}is_{\_}a_{\_}quadratic_{\_}nonresidue
```

> To better understand this last conclusion, note that the only element of order $2$ (modulo a prime odd number) is **always** $- 1$, that is $p - 1$. Indeed there are always $\phi(2) = 1$ subgroups of order $2$ [if the group has generators].

Now, if $k$ is **even**, then $g^{k} \equiv a \mod p$ is a **quadratic residue**, and

```math
a^{(p - 1) / 2} = (g^{2m})^{(p - 1) / 2} = g^{2m(p - 1) / 2} = g^{m(p - 1)} \equiv 1 \mod p
```

This basically means that

```math
a^{(p - 1) / 2} \equiv 1 \mod p \iff a_{\_}is_{\_}a_{\_}quadratic_{\_}residue
```

Recalling $7 \mod 79$, then, if $7^{(79 - 1) / 2} \equiv 1 \mod 79$ then $7$ is a **quadratic residue**. Otherwise, if $7^{(79 - 1) / 2} \equiv - 1 \equiv 78 \mod 79$ then $7$ is a **quadratic nonresidue**.

```math
7^{(79 - 1) / 2} = 7^{39} \equiv 78 \mod 79
```

This means that $7$ is a **quadratic nonresidue** modulo $79$.

## Stating the existence of any root immediately and calculating it quickly modulo a prime number

Euler's Criterion generates confusion in general. When we use it, we are not finding any root. We just know if the number itself [for ex. $7$ we considered previously] is the square (if it is a **quadratic residue**) of **something** or if it is not the square of something. But we don't know what **"something"** is, and in general, we don't know if it could be some greater (than 2) power of something else. Recalling the fact we are always operating on some **generator** $g$, then, we'll always handle something like $g^{y} \mod p$ when doing operations modulo $p$. This means that if we need to find some $n-th$ root of $g^{y}$ we could immediately perform $g^{y / n = y \cdot (n^{- 1} \mod \phi(p))}$. Now, $n^{- 1} \mod \phi(p)$ exists if and only if $gcd(n, \phi(p)) = 1$, because $1$ is an element of $Z_{\phi(p)}^{\star}$ and if $n$ is not coprime with $\phi(p)$ then whatever we multiply by $n$ will never be part of $Z_{\phi(p)}^{\star}$ (there's a simple theorem proving this). This means that there exist many cases where our root doesn't exist and it's not even hard to state it or to find those, we will just need to apply the Extended Euclidean Algorithm and check the result. If $gcd(n, \phi(p)) \neq 1$ then the root doesn't even exist. If it equals $1$ then the $n - th$ root is $g^{y(n^{- 1} \mod \phi(p)} \mod p$ because $(g^{y(n^{- 1} \mod \phi(p))})^{n} = g^{y(n^{- 1} \mod \phi(p))n} = g^{y} \mod p$.

## Calculating ANY root quickly in some Galois field extension where the order of the multiplicative group is prime

Galois Fields are particular. For example, using integers we will never end up having some $g^{y} \mod p$ where $y$ is cyclic by a prime order, because $\phi(p)$ **is almost never a prime number**. This is different in Galois Fields because the order of a multiplicative group defined modulo an irreducible polinomial $I(x)$ (and a prime number $p$) is equal to $p^{deg(I(x))} - 1$. This means that if $deg(I(x))$ is some fair prime number and $p = 2$, we'll have $p^{deg(I(x))} - 1 = p^{k} - 1$ being a Mersenne prime number $M$. This means that in this case, **any $n-th$ root of any $g(x)^{y} \mod I(x)$ will exist and will be computable as follows.**

### Method 1

```math
y \equiv z \mod M
```

We'll need some $w$ such that

```math
((g(x)^{z})^{n})^{w} = g(x)^{znw} \equiv g(x)^{z} \mod I(x)
```

This last equation means that $w$ **must be the multiplicative inverse of $n$**, and, in that case, our $n-th$ root will be

```math
g(x)^{zw} = g(x)^{z(n^{- 1} \mod M)} \mod I(x)
```

This restrict the problem to find $n^{- 1} \mod M$ which is solvable using the Extendend Euclidean Algorithm.

### Method 2

We can just compute

```math
g(x)^{z / n = z \cdot (n^{- 1} \mod M) = zw} \mod I(x)
```

