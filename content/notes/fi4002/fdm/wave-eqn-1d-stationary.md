---
title: "wave eqn 1d stationary"
date: 2023-11-02T19:31:00+07:00
authors: ['Sparisoma Viridi']
tags: ['fi4002']
draft: false
math: true
url: "0134"
---
{{< toc >}}


## theory
+ The 1-d wave equation is
  $$\tag{1}
  \frac{\partial^2 u}{\partial t^2} = c^2 \frac{\partial^2 u}{\partial x^2}
  $$
  with displacement $u$, time $t$, velocity $c$, dan position $x$ ([Dawkins, 2022](https://tutorial.math.lamar.edu/classes/de/TheWaveEquation.aspx)).
+  A function of two variables $u(x, y)$ can be represented
as product of two functions with single variables
  $$\tag{2}
  u(x, t) = a(x) \ b(t),
  $$
  which is known as separation of variables ([Dawkins, 2022](https://tutorial.math.lamar.edu/classes/de/SeparationofVariables.aspx)).
+ Eigen value problem
  $$\tag{3}
  \mathbf{M}\mathbf{X} = \lambda \mathbf{X},
  $$
  that will be applied to second order differential equation ([Salih, 2016](https://www.iist.ac.in/sites/default/files/people/IN08026/Eigenvalue.pdf)).


## substitution
+ Substitute (2) to (1) will give
  $$
  \begin{array}{rcl}
  \displaystyle a \frac{d^2 b}{dt^2} & = & \displaystyle c^2 b \frac{d^2 a}{dx^2} \newline \newline
  \displaystyle \frac1b \frac{d^2 b}{dt^2} & = & \displaystyle c^2 \frac1a \frac{d^2 a}{dx^2},
  \end{array}
  $$
  and choose both side is $-\omega^2$.


## left side
$$\tag{4}
\begin{array}{rcl}
\displaystyle \frac1b \frac{d^2 b}{dt^2} & = & -\omega^2 \newline \newline
\displaystyle \frac{d^2 b}{dt^2} & = & -\omega^2 b.
\end{array}
$$


## right side
$$\tag{5}
\begin{array}{rcl}
\displaystyle c^2 \frac1a \frac{d^2 a}{dx^2} & = & -\omega^2 \newline \newline
\displaystyle \frac{d^2 a}{dx^2} & = & \displaystyle -\frac{\omega^2}{c^2} a \newline \newline
\displaystyle \frac{d^2 a}{dx^2} & = & \displaystyle -k^2 a.
\end{array}
$$


## fdm x
$$\tag{6}
\begin{array}{rcl}
\displaystyle \frac{ a_{i-1,j} - 2a_{i,j} + a_{i+1,j} }{h^2} & = & - k^2 a_{i,j} \newline \newline
a_{i-1,j} - 2a_{i,j} + a_{i+1,j} & = & - h^2 k^2 a_{i,j} \newline \newline
a_{i-1,j} - 2a_{i,j} + a_{i+1,j} & = & - l^2 a_{i,j} 
\end{array}
$$

With boundary condition $a_1 = 0$ and $a_n = 0$ where $n$ is number of data.


## bvp
+ (5) will be
$$\tag{7}
\left[
\begin{matrix}
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \newline
1 & -2 & 1 & 0 & 0 & 0 & 0 & 0 \newline
0 & 1 & -2 & 1 & 0 & 0 & 0 & 0 \newline
0 & 0 & 1 & -2 & 1 & 0 & 0 & 0 \newline
0 & 0 & 0 & 1 & -2 & 1 & 0 & 0 \newline
0 & 0 & 0 & 0 & 1 & -2 & 1 & 0 \newline
0 & 0 & 0 & 0 & 0 & 1 & -2 & 1 \newline
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \newline
\end{matrix}
\right]
\left[
\begin{matrix}
a_1 \newline
a_2 \newline
a_3 \newline
a_4 \newline
a_5 \newline
a_6 \newline
a_7 \newline
a_8 \newline
\end{matrix}
\right]
=
-l^2
\left[
\begin{matrix}
a_1 \newline
a_2 \newline
a_3 \newline
a_4 \newline
a_5 \newline
a_6 \newline
a_7 \newline
a_8 \newline
\end{matrix}
\right]
$$
  for $n = 8$.
+ It turns into an eigen value problem

## code
url https://onecompiler.com/python/3zsbrukaf