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

## Calculating any root modulo a prime number

Euler's Criterion generates confusion in general. When we use it, we are not finding any root. We just know if the number itself [for ex. $7$ we considered previously] is the square root (if it is a **quadratic residue**) of **something** or if it is not the square root of something. But we don't know what **"something"** is, and in general, we don't know if it could be some greater root of something else. Recalling the fact we are always operating on some **generator** $g$, then, we'll always handle something like $g^{y} \mod p$ when doing operations modulo $p$. This means that if we need to find some $n-th$ root of $g^{y}$ we could immediately perform $g^{y / n}$. Now, what if $n \nmid y$ ? In those cases, we can simply state that particular root does not exist inside $Z_{p}^{\ast}$. Indeed, if you look at the previous sections, if $k$ is not even, that is, is not a multiple of $2$ **hence is not divisible by $2$, then it cannot be a quadratic residue**.

> Consider now this scenario. We want to find the actual $n-th$ root of some value modulo $p$ without having obtained it as some power of some generator $g$. This is a huge problem. In general, for the square root we should consider Tonelli-Shanks algorithm along with other arcane algorithms, but note that **if we can avoid those, then we SHOULD**. For ex. consider this example. We want to find a generator modulo $17$. If you run the following algorithm you'll see that $7$ is a generator. In this case $17 - 1 = 16$. Now, imagine we want to know the square root of $11$. We immediately know that $7^{5} \equiv 11 \mod 17$, and since $2 \nmid 5$ then $11$ can't be a quadratic residue. Indeed $11^{16 / 2 = 8} \equiv 16 \equiv - 1 \mod 17$.

```shell
[14ms][~]$ python3 ZZ.py            
Enter integer number to see every multiplicative subgroup:
17

Printing results using n as modulo and stopping at Phi(n)...

 1 ->[ 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 [ 1 ] ]

 2 ->[ 2 4 8 16 15 13 9 1 2 4 8 16 15 13 9 [ 1 ] ]

 3 ->[ 3 9 10 13 5 15 11 16 14 8 7 4 12 2 6 [ 1 ] ]

 4 ->[ 4 16 13 1 4 16 13 1 4 16 13 1 4 16 13 [ 1 ] ]

 5 ->[ 5 8 6 13 14 2 10 16 12 9 11 4 3 15 7 [ 1 ] ]

 6 ->[ 6 2 12 4 7 8 14 16 11 15 5 13 10 9 3 [ 1 ] ]

 7 ->[ 7 15 3 4 11 9 12 16 10 2 14 13 6 8 5 [ 1 ] ]

 8 ->[ 8 13 2 16 9 4 15 1 8 13 2 16 9 4 15 [ 1 ] ]

 9 ->[ 9 13 15 16 8 4 2 1 9 13 15 16 8 4 2 [ 1 ] ]

 10 ->[ 10 15 14 4 6 9 5 16 7 2 3 13 11 8 12 [ 1 ] ]

 11 ->[ 11 2 5 4 10 8 3 16 6 15 12 13 7 9 14 [ 1 ] ]

 12 ->[ 12 8 11 13 3 2 7 16 5 9 6 4 14 15 10 [ 1 ] ]

 13 ->[ 13 16 4 1 13 16 4 1 13 16 4 1 13 16 4 [ 1 ] ]

 14 ->[ 14 9 7 13 12 15 6 16 3 8 10 4 5 2 11 [ 1 ] ]

 15 ->[ 15 4 9 16 2 13 8 1 15 4 9 16 2 13 8 [ 1 ] ]

 16 ->[ 16 1 16 1 16 1 16 1 16 1 16 1 16 1 16 [ 1 ] ]

Factors: [[17, 1]]
Every co-factor of Phi: [16]
Multiplied co-factors phis: 16
Phi factors: [[2, 4]]
Every Phi s co-factors Phi: [[2, 4]]
Multiplied Phi s co-factors phis: 8
Resume: Phi(n) =  16 , Phi(Phi(n)) =  8
```

The code used was the following.

```python
import sys

def factorize(n):
	factors = []
	c = 0
	exp = 0
	i = 2
	while i <= n:
		while n%i == 0:
			n/=i
			exp+=1
		if exp > 0:
			factors.append([i, exp])
			exp=0
		i+=1
	return factors
	
def phiExpansion(factors):
	phis = []
	z = 1
	for factor in factors:
		z *= (factor[0]**factor[1] - factor[0]**(factor[1]-1))
		phis.append(z)
		z = 1
	return phis
	
def synthPhi(phisFactors):
	synthPhi = 1
	for phis in phisFactors:
		synthPhi *= phis
	return synthPhi
	
Zn = int(input("Enter integer number to see every multiplicative subgroup:\n"))
Factors = factorize(Zn)

PhiExp = phiExpansion(Factors)
Phi = synthPhi(PhiExp)

FPhi = factorize(Phi)
FPhiExp = phiExpansion(FPhi)
PhiPhi = synthPhi(FPhiExp)

print("\nPrinting results using n as modulo and stopping at Phi(n)...")

for j in range(1, Zn):
	print("\n", j, "->[", end = " ")
	for i in range(1, Phi + 1):
		if(i == Phi):
			print("[", j**i % Zn, "]", end = " ")
		else:
			print(j**i % Zn, end = " ")
	print("]")
	
print("\nFactors:", Factors)
print("Every co-factor of Phi:", PhiExp)
print("Multiplied co-factors phis:", Phi)
print("Phi factors:", FPhi)
print("Every Phi s co-factors Phi:", FPhi)
print("Multiplied Phi s co-factors phis:", PhiPhi)
print("Resume: Phi(n) = ", Phi, ", Phi(Phi(n)) = ", PhiPhi)
```

## Calculating ANY root FAST in some Galois field extension where the order of the multiplicative group is prime

If we want to find the $n-th$ root of $g(x)^{y} \mod I(x)$, (**where $I(x)$ is irreducible and it has degree $d$ such that $d - 1 = p$ is a Mersenne prime number**) we just need to find

```math
y \equiv z \mod p
```

and some $x$ such that

```math
((g(x)^{z})^{n})^{x} = g(x)^{znx} \equiv g^{z} \mod I(x)
```

This last equation means that $x$ **must be the multiplicative inverse of $n$**, and, in that case, our $n-th$ root will be

```math
g(x)^{x} = g(x)^{n^{- 1}} \equiv g(x)^{z}_{\_}nth_{\_}root \mod I(x)
```

This restrict the problem to find $n^{- 1} \mod p$ which is solvable using the extendend Euclidean Algorithm iff $gcd(n, d - 1) = 1$ (otherwise we'll fall into the previous problems $\mod p$ on the integers). This is another reason why extension fields are so powerful (we can find $d - 1 = p$ prime, where $d$ is **not** prime, but we can't do this $\mod p$ where $p$ is prime on the integers).
