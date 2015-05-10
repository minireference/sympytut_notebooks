
## Complex numbers

Ever since Newton, the word &ldquo;number&rdquo; has been used to refer to one
of the following types of math objects: the naturals $\mathbb{N}$, the integers
$\mathbb{Z}$, the rationals $\mathbb{Q}$, and the real numbers $\mathbb{R}$. Each set of numbers is
associated with a different class of equations. The natural numbers
$\mathbb{N}$ appear as solutions of the equation $m + n = x$, where $m$ and $n$ are
natural numbers (denoted $m, n \in \mathbb{N}$). The integers $\mathbb{Z}$ are the solutions
to equations of the form $x + m = n$, where $m, n \in \mathbb{N}$. The rational
numbers $\mathbb{Q}$ are necessary to solve for $x$ in $mx = n$, with $m, n \in \mathbb{Z}$.
The solutions to $x^2 = 2$ are irrational (so $\not\in \mathbb{Q}$) so we need an even
larger set that contains *all* possible numbers: real set of numbers $\mathbb{R}$.
A pattern emerges where more complicated equations require the
invention of new types of numbers.

Consider the quadratic equation $x^2 = -1$. There are no real solutions
to this equation, but we can define an imaginary number $i = \sqrt{-1}$
(denoted `I` in `SymPy`) that satisfies this equation:


    I*I




$$-1$$




    solve( x**2 + 1 , x)




$$\left [ - i, \quad i\right ]$$



The solutions are $x = i$ and $x = -i$, and indeed we can verify that
$i^2 + 1 = 0$ and $(-i)^2 + 1 = 0$ since $i^2 = -1$.

The complex numbers $\mathbb{C}$ are defined as $\{ a+bi \,|\, a,b \in \mathbb{R} \}$. Complex numbers
contain a real part and an imaginary part:


    z = 4 + 3*I
    z




$$4 + 3 i$$




    re(z)




$$4$$




    im(z)




$$3$$



The *polar* representation of a complex number is $z\!\equiv\!|z|\angle\theta\!\equiv \!|z|e^{i\theta}$.
For a complex number $z=a+bi$, 
the quantity $|z|=\sqrt{a^2+b^2}$ is known as the absolute value of $z$,
and $\theta$ is its *phase* or its *argument*:


    Abs(z)




$$5$$




    arg(z)




$$\operatorname{atan}{\left (\frac{3}{4} \right )}$$



The complex conjugate of $z = a + bi$ is the number $\bar{z} = a - bi$:


    conjugate( z )




$$4 - 3 i$$



Complex conjugation is important for computing the absolute value
of $z$ $\left(|z|\equiv\sqrt{z\bar{z}}\right)$ and for division by $z$ $\left(\frac{1}{z}\equiv\frac{\bar{z}}{|z|^2}\right)$.

### Euler's formula

[Euler's formula](https://en.wikipedia.org/wiki/Euler's_formula) shows an important relation between the exponential
function $e^x$ and the trigonometric functions $sin(x)$ and $cos(x)$:

$$e^{ix} = \cos x + i \sin x.$$

To obtain this result in `SymPy`, you must specify that the number $x$ is
real and also tell `expand` that you're interested in complex expansions:


    x = symbols('x', real=True)
    exp(I*x).expand(complex=True)




$$i \sin{\left (x \right )} + \cos{\left (x \right )}$$




    re( exp(I*x) )




$$\cos{\left (x \right )}$$




    im( exp(I*x) )




$$\sin{\left (x \right )}$$



Basically, $\cos(x)$ is the real part of $e^{ix}$, and $\sin(x)$ is the imaginary
part of $e^{ix}$. Whaaat? I know it's weird, but weird things are bound
to happen when you input imaginary numbers to functions.

Euler's formula is often used to rewrite the functions `sin` and `cos` in
terms of complex exponentials. For example,


    (cos(x)).rewrite(exp)




$$\frac{e^{i x}}{2} + \frac{1}{2} e^{- i x}$$



Compare this expression with the definition of hyperbolic cosine.
