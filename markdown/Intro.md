
# Taming math and physics using `SymPy`

Tutorial based on the [No bullshit guide](http://minireference.com/) series of textbooks by [Ivan Savov](&#109;&#097;&#105;&#108;&#116;&#111;:&#105;&#118;&#097;&#110;&#046;&#115;&#097;&#118;&#111;&#118;+&#083;&#089;&#077;&#080;&#089;&#084;&#085;&#084;&#064;&#103;&#109;&#097;&#105;&#108;&#046;&#099;&#111;&#109;)

## Abstract

Most people consider math and physics to be scary
beasts from which it is best to keep one's distance. Computers,
however, can help us tame the complexity and tedious arithmetic
manipulations associated with these subjects. Indeed, math and
physics are much more approachable once you have the power of
computers on your side.

This tutorial serves a dual purpose. On one hand, it serves
as a review of the fundamental concepts of mathematics for
computer-literate people. On the other hand, this tutorial serves
to demonstrate to students how a computer algebra system can
help them with their classwork. A word of warning is in order.
Please don't use `SymPy` to avoid the suffering associated with your
homework! Teachers assign homework problems to you because
they want you to learn. Do your homework by hand, but if you
want, you can check your answers using `SymPy`. Better yet, use
`SymPy` to invent extra practice problems for yourself.

## Contents

* [Fundamentals of mathematics](Fundamentals-of-mathematics.ipynb)
* [Complex numbers](Complex-numbers.ipynb)
* [Calculus](Calculus.ipynb)
* [Vectors](Vectors.ipynb)
* [Mechanics](Mechanics.ipynb)
* [Linear algebra](Linear-algebra.ipynb)

## Introduction

You can use a computer algebra system (CAS) to compute complicated
math expressions, solve equations, perform calculus procedures,
and simulate physics systems.

All computer algebra systems offer essentially the same functionality,
so it doesn't matter which system you use: there are free
systems like `SymPy`, `Magma`, or `Octave`, and commercial systems like
`Maple`, `MATLAB`, and `Mathematica`. This tutorial is an introduction to
`SymPy`, which is a *symbolic* computer algebra system written in the
programming language `Python`. In a symbolic CAS, numbers and
operations are represented symbolically, so the answers obtained are
exact. For example, the number &radic;2 is represented in `SymPy` as the
object `Pow(2,1/2)`, whereas in numerical computer algebra systems
like `Octave`, the number &radic;2 is represented as the approximation
1.41421356237310 (a `float`). For most purposes the approximation
is okay, but sometimes approximations can lead to problems:
`float(sqrt(2))*float(sqrt(2))` = 2.00000000000000044 &ne; 2. Because
`SymPy` uses exact representations, you'll never run into such
problems: `Pow(2,1/2)*Pow(2,1/2)` = 2.

This tutorial is organized as follows. We'll begin by introducing the
`SymPy` basics and the bread-and-butter functions used for manipulating
expressions and solving equations. Afterward, we'll discuss the
`SymPy` functions that implement calculus operations like differentiation
and integration. We'll also introduce the functions used to deal with
vectors and complex numbers. Later we'll see how to use vectors and
integrals to understand Newtonian mechanics. In the last section,
we'll introduce the linear algebra functions available in `SymPy`.

This tutorial presents many explanations as blocks of code. Be sure
to try the code examples on your own by typing the commands into
`SymPy`. It's always important to verify for yourself!

## Using SymPy

The easiest way to use `SymPy`, provided you're connected to the
Internet, is to visit http://live.sympy.org. You'll be presented with
an interactive prompt into which you can enter your commands&mdash;right
in your browser.

If you want to use `SymPy` on your own computer, you must install
`Python` and the python package `sympy`. You can then open a command
prompt and start a `SymPy` session using:

```
you@host$ python
Python X.Y.Z
[GCC a.b.c (Build Info)] on platform
Type "help", "copyright", or "license" for more information.
>>> from sympy import *
>>>
```

The `>>>` prompt indicates you're in the Python shell which accepts
Python commands. The command `from sympy import *` imports all
the `SymPy` functions into the current namespace. All `SymPy` functions
are now available to you. To exit the python shell press `CTRL+D`.

I highly recommend you also install `ipython`, which is an improved
interactive python shell. If you have `ipython` and `SymPy` installed,
you can start an `ipython` shell with `SymPy` pre-imported using the
command `isympy`. For an even better experience, you can try `ipython notebook`,
which is a web frontend for the `ipython` shell.

You can start your session the same way as `isympy` do, by running following commands, which will be detaily described latter.


    from sympy import init_session
    init_session()

    IPython console for SymPy 0.7.6 (Python 3.4.2-64-bit) (ground types: gmpy)
    
    These commands were executed:
    >>> from __future__ import division
    >>> from sympy import *
    >>> x, y, z, t = symbols('x y z t')
    >>> k, m, n = symbols('k m n', integer=True)
    >>> f, g, h = symbols('f g h', cls=Function)
    >>> init_printing()
    
    Documentation can be found at http://www.sympy.org


## Conclusion

I would like to conclude with some words of caution about the overuse of computers.
Computer technology is very powerful and is everywhere around us,
but let's not forget that computers are actually very dumb:
computers are mere calculators and they depend on your knowledge to direct them.
It's important that you learn how to do complicated math by hand in order to be 
able to instruct computers to do math for you and to check the results of your computer calculations.
I don't want you to use the tricks you learned in this tutorial to avoid math problems from now on
and simply rely blindly on `SymPy` for all your math needs.
I want both you and the computer to become math powerhouses!
The computer will help you with tedious calculations (they're good at that)
and you'll help the computer by guiding it when it gets  stuck (humans are good at that).

## Links

* [Installation instructions for `ipython notebook`](http://ipython.org/install.html)
* [The official `SymPy` tutorial](http://docs.sympy.org/latest/tutorial/intro.html)
* [A list of `SymPy` gotchas](http://docs.sympy.org/dev/gotchas.html)
* [`SymPy` video tutorials by Matthew Rocklin](http://pyvideo.org/speaker/583/matthew-rocklin)

## Book plug

![Cover](http://minireference.com/miniref/lib/tpl/miniref/dist/images/productshots/noBSguide_math_physics_softcover.png)

The examples and math explanations in this tutorial are sourced from the 
*No bullshit guide* series of books published by Minireference&nbsp;Co.
We publish textbooks that make math and physics accessible and affordable for everyone.
If you're interested in learning more about the math, physics, and calculus topics discussed in this tutorial,
check out the **No bullshit guide to math and physics**.
The book contains the distilled information that normally comes in two first-year university books:
the introductory physics book (1000+ pages) and the first-year calculus book (1000+ pages).
Would you believe me if I told you that you can learn the 
same material from a single book that is 1/7<sup>th</sup> the size and 1/10<sup>th</sup> of the 
price of mainstream textbooks?

This book contains short lessons on math and physics, calculus.
Often calculus and mechanics are taught as separate subjects.
It shouldn't be like that.
If you learn calculus without mechanics, it will be boring.
If you learn mechanics without calculus, you won't truly understand what is going on.
This textbook covers both subjects in an integrated manner.
    
Contents:

* High school math
* Vectors
* Mechanics
* Differential calculus
* Integral calculus
* 250+ practice problems

For more information, see the book's website at [minireference.com](http://minireference.com/)

The presented linear algebra examples are 
sourced from the [**No bullshit guide to linear algebra**](https://gum.co/noBSLA).
Check out the book if you're taking a linear algebra course of if you're missing the prerequisites 
for learning machine learning, computer graphics, or quantum mechanics.

I'll close on a note for potential readers who suffer from math-phobia.
Both books start with an introductory chapter that reviews all 
high school math concepts needed to make math and physics 
accessible to everyone.
Don't worry, we'll fix this math-phobia thing right up for you;
**when you've got `SymPy` skills, math fears *you*!**

To stay informed about upcoming titles,
follow [@minireference](https://twitter.com/minireference) on twitter 
and check out the facebook page at [fb.me/noBSguide](http://fb.me/noBSguide).
