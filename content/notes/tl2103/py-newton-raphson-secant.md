---
title: "py newton-raphson secant"
date: 2023-10-04T20:41:00+07:00
authors: ['Sparisoma Viridi']
tags: ['tl2103']
draft: false
math: true
url: "0087"
---
{{< toc >}}


## direction
+ Mr. Satoru is stuck in a train station with a bunch of monsters (which he needs to kill) and humans (which he needs to save). He can expand a “sure-kill” domain that kills anyone within its perimeters, with him as the center, but he must consider the optimal amount of monsters killed and humans saved.
+ The monsters are distributed around him in a randomized manner, but can be represented with the equation
$$\tag{1}
M(x) = 20x - x^2.
$$
+ The humans distributed around him can also be represented with the equation
$$\tag{2}
H(x) = \sin 2x.
$$
+ Mr. Satoru’s judgement on the radius in which he would expand him domain can be represented with the following equation
$$\tag{3}
R(x) = M(x) + H(x).
$$
+ Optimize the radius of Mr. Satoru’s domain using the Newton-Raphson method, and Secant Method until the error $\varepsilon < 10^{-3}$! (Hint: To optimize a function, differentiate it first and find its root).


## derivative
+ differentiate Eqn (3), with the help of Eqns (1) and (2) wil give
$$\tag{4}
R\'(x) = M\'(x) + H\'(x) = 20 - 2x + 2\cos 2x. 
$$
+ Optimum radius is obtained when
$$\tag{5}
R\'(x_{\rm optimum}) = 0.
$$
+ Find root of $x\'(x)$ to get $x_{\rm optimum}$.


## iterative method
+ Newton-Raphson method
$$\tag{6}
x_{n+1} = x_n - \frac{f(x_n)}{f\'(x_n)}.
$$
+ Secant method
$$\tag{7}
x_{n+2} = x_{n+1} - \frac{(x_{n+1} - x_n) f(x_{n+1})}{f(x_{n+1}) - f(x_n)}.
$$
+ Newton-Raphson method requires one initial value $x_0$ and secant method requires two initial values $x_0$ and $x_1$.
