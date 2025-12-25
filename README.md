# Roots modulo p(rime)

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

## Calculating any root modulo a prime number

Euler's Criterion generates confusion in general. When we use it, we are not finding any root. We just know if the number itself [for ex. $7$ we considered previously] is the square root (if it is a **quadratic residue**) of **something** or if it is not the square root of something. But we don't know what **"something"** is, and in general, we don't know if it could be some greater root of something else. Recalling the fact we are always operating on some **generator** $g$, then, we'll always handle something like $g^{y} \mod p$ when doing operations modulo $p$. This means that if we need to find some $n-th$ root of $g^{y}$ we could immediately perform $g^{y / n}$. Now, what if $n \nmid y$ ? In those cases, we can simply state that particular root does not exist inside $Z_{p}^{\ast}$. Indeed, if you look at the previous sections, if $k$ is not even, that is, is not a multiple of $2$ **hence is not divisible by $2$, then it cannot be a quadratic residue**.

> Consider now this scenario. We want to find the actual $n-th$ root of some value modulo $p$ without having obtained it as some power of some generator $g$. This is a huge problem. In general, for the square root we should consider Tonelli-Shanks algorithm along with other arcane algorithms, but note that **if we can avoid those, then we SHOULD**. For ex. consider this example. We want to find a generator modulo $17$. If you run the following algorithm you'll see that $7$ is a generator. In this case $17 - 1 = 16$. Now, imagine we want to know the square root of $11$. We immediately know that $7^{5} \equiv 11 \mod 17$, and since $2 \nmid 5$ then $11$ can't be a quadratic residue. Indeed $11^{16 / 2 = 8} \equiv 16 \equiv - 1 \mod 17$.


Now, the exponents are part of $Z_{p - 1}^{+}$. This means that if we want to find the $n-th$ root of $g^{y} \mod p$, we just need to find

```math
y \equiv z \mod (p - 1)
```

and some $x$ such that

```math
((g^{z})^{n})^{x} = g^{znx} \equiv g^{z} \mod p
```

This last equation means that $x$ must be the multiplicative inverse of $n$, and, in that case, our $n-th$ root will be

```math
g^{x} = g^{n^{- 1}} \equiv g^{z}_{\_}nth_{\_}root \mod p
```

This restrict the problem to find $n^{- 1} \mod (p - 1)$ which is solvable using the extendend Euclidean Algorithm iff $gcd(n, p - 1) = 1$, otherwise we'll need some other trick. This another reason why extension fields are so powerful (we can find $p - 1$ prime, where $p$ is **not** prime, but we can't do this $mod p$ where $p$ is prime).

```math

```
