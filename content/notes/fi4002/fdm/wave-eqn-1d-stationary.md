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


## assignment
+ [Solving wave equation with FDM for stationary wave case](https://github.com/dudung/lecture-notes/issues/22)


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
+ url https://onecompiler.com/python/3zsbrukaf

```python
import math
import numpy as np
from numpy.linalg import eig

xmin = 0
xmax = 1
h = 0.1
N = int((xmax - xmin) / h + 1)
x = [round(xmin + i*h, 2) for i in range(N)]
print("h =", h)
print("N =", N)
print("x =", x)
print()

M = np.zeros((N, N))
for i in range(1, N-1):
  M[i][i] = -2
  M[i][i-1] = 1
  M[i][i+1] = 1
M[0][0] = 0
M[N-1][N-1] = 0

print("M =")
for i in M:
  for j in i:
    print(j.round(2), end='\t')
  print()
print()

w, v = eig(M)

print("E=val")
for i in w:
    print(round(i, 4))
print()


ii = 0
for i in range(N):
  ii += 1
  print("E-vect", ii, "=")
  vj = v[:, i]
  for j in vj:
    print(j.round(3))
  print()
```



## charts 1
{{< chart 60 240 >}}
{
 type: 'scatter',
 data: {
    datasets: [{
/* -- */

label: "E-val = 3.902",
data: [
	{x: 0.0, y: 0.0},
	{x: 0.1, y: 0.138},
	{x: 0.2, y: 0.263},
	{x: 0.3, y: 0.362},
	{x: 0.4, y: 0.425},
	{x: 0.5, y: 0.447},
	{x: 0.6, y: 0.425},
	{x: 0.7, y: 0.362},
	{x: 0.8, y: 0.263},
	{x: 0.9, y: 0.138},
	{x: 1.0, y: 0.0},
],

/* -- */
       backgroundColor: ['#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa'],
       borderColor: ['#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88'],
       radius: 4,
    }],
 },
 options: {
    responsive: false,
    scales: {
       x: {
          type: 'linear',
          position: 'bottom,'
       }
    }
 },
}{{< /chart >}}


## charts 2
{{< chart 60 240 >}}
{
 type: 'scatter',
 data: {
    datasets: [{
/* -- */

label: "E-val = 3.618",
data: [
	{x: 0.0, y: 0.0},
	{x: 0.1, y: -0.263},
	{x: 0.2, y: -0.425},
	{x: 0.3, y: -0.425},
	{x: 0.4, y: -0.263},
	{x: 0.5, y: 0.0},
	{x: 0.6, y: 0.263},
	{x: 0.7, y: 0.425},
	{x: 0.8, y: 0.425},
	{x: 0.9, y: 0.263},
	{x: 1.0, y: 0.0},
],

/* -- */
       backgroundColor: ['#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa'],
       borderColor: ['#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88'],
       radius: 4,
    }],
 },
 options: {
    responsive: false,
    scales: {
       x: {
          type: 'linear',
          position: 'bottom,'
       }
    }
 },
}{{< /chart >}}


## charts 3
{{< chart 60 240 >}}
{
 type: 'scatter',
 data: {
    datasets: [{
/* -- */

label: "E-val = 3.176",
data: [
	{x: 0.0, y: 0.0},
	{x: 0.1, y: -0.362},
	{x: 0.2, y: -0.425},
	{x: 0.3, y: -0.138},
	{x: 0.4, y: 0.263},
	{x: 0.5, y: 0.447},
	{x: 0.6, y: 0.263},
	{x: 0.7, y: -0.138},
	{x: 0.8, y: -0.425},
	{x: 0.9, y: -0.362},
	{x: 1.0, y: 0.0},
],

/* -- */
       backgroundColor: ['#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa'],
       borderColor: ['#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88'],
       radius: 4,
    }],
 },
 options: {
    responsive: false,
    scales: {
       x: {
          type: 'linear',
          position: 'bottom,'
       }
    }
 },
}{{< /chart >}}


## charts 4
{{< chart 60 240 >}}
{
 type: 'scatter',
 data: {
    datasets: [{
/* -- */

label: "E-val = 2.618",
data: [
	{x: 0.0, y: 0.0},
	{x: 0.1, y: 0.425},
	{x: 0.2, y: 0.263},
	{x: 0.3, y: -0.263},
	{x: 0.4, y: -0.425},
	{x: 0.5, y: 0.0},
	{x: 0.6, y: 0.425},
	{x: 0.7, y: 0.263},
	{x: 0.8, y: -0.263},
	{x: 0.9, y: -0.425},
	{x: 1.0, y: 0.0},
],

/* -- */
       backgroundColor: ['#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa'],
       borderColor: ['#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88'],
       radius: 4,
    }],
 },
 options: {
    responsive: false,
    scales: {
       x: {
          type: 'linear',
          position: 'bottom,'
       }
    }
 },
}{{< /chart >}}


## charts 5
{{< chart 60 240 >}}
{
 type: 'scatter',
 data: {
    datasets: [{
/* -- */

label: "E-val = 2.0",
data: [
	{x: 0.0, y: 0.0},
	{x: 0.1, y: 0.447},
	{x: 0.2, y: 0.0},
	{x: 0.3, y: -0.447},
	{x: 0.4, y: -0.0},
	{x: 0.5, y: 0.447},
	{x: 0.6, y: 0.0},
	{x: 0.7, y: -0.447},
	{x: 0.8, y: 0.0},
	{x: 0.9, y: 0.447},
	{x: 1.0, y: 0.0},
],

/* -- */
       backgroundColor: ['#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa'],
       borderColor: ['#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88'],
       radius: 4,
    }],
 },
 options: {
    responsive: false,
    scales: {
       x: {
          type: 'linear',
          position: 'bottom,'
       }
    }
 },
}{{< /chart >}}


## charts 6
{{< chart 60 240 >}}
{
 type: 'scatter',
 data: {
    datasets: [{
/* -- */

label: "E-val = 0.098",
data: [
	{x: 0.0, y: 0.0},
	{x: 0.1, y: 0.138},
	{x: 0.2, y: -0.263},
	{x: 0.3, y: 0.362},
	{x: 0.4, y: -0.425},
	{x: 0.5, y: 0.447},
	{x: 0.6, y: -0.425},
	{x: 0.7, y: 0.362},
	{x: 0.8, y: -0.263},
	{x: 0.9, y: 0.138},
	{x: 1.0, y: 0.0},
],

/* -- */
       backgroundColor: ['#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa'],
       borderColor: ['#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88'],
       radius: 4,
    }],
 },
 options: {
    responsive: false,
    scales: {
       x: {
          type: 'linear',
          position: 'bottom,'
       }
    }
 },
}{{< /chart >}}


## charts 7
{{< chart 60 240 >}}
{
 type: 'scatter',
 data: {
    datasets: [{
/* -- */

label: "E-val = 0.382",
data: [
	{x: 0.0, y: 0.0},
	{x: 0.1, y: 0.263},
	{x: 0.2, y: -0.425},
	{x: 0.3, y: 0.425},
	{x: 0.4, y: -0.263},
	{x: 0.5, y: 0.0},
	{x: 0.6, y: 0.263},
	{x: 0.7, y: -0.425},
	{x: 0.8, y: 0.425},
	{x: 0.9, y: -0.263},
	{x: 1.0, y: 0.0},
],

/* -- */
       backgroundColor: ['#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa'],
       borderColor: ['#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88'],
       radius: 4,
    }],
 },
 options: {
    responsive: false,
    scales: {
       x: {
          type: 'linear',
          position: 'bottom,'
       }
    }
 },
}{{< /chart >}}


## charts 8
{{< chart 60 240 >}}
{
 type: 'scatter',
 data: {
    datasets: [{
/* -- */

label: "E-val = 1.382",
data: [
	{x: 0.0, y: 0.0},
	{x: 0.1, y: -0.425},
	{x: 0.2, y: 0.263},
	{x: 0.3, y: 0.263},
	{x: 0.4, y: -0.425},
	{x: 0.5, y: -0.0},
	{x: 0.6, y: 0.425},
	{x: 0.7, y: -0.263},
	{x: 0.8, y: -0.263},
	{x: 0.9, y: 0.425},
	{x: 1.0, y: 0.0},
],

/* -- */
       backgroundColor: ['#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa'],
       borderColor: ['#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88'],
       radius: 4,
    }],
 },
 options: {
    responsive: false,
    scales: {
       x: {
          type: 'linear',
          position: 'bottom,'
       }
    }
 },
}{{< /chart >}}


## charts 9
{{< chart 60 240 >}}
{
 type: 'scatter',
 data: {
    datasets: [{
/* -- */

label: "E-val = 0.824",
data: [
	{x: 0.0, y: 0.0},
	{x: 0.1, y: -0.362},
	{x: 0.2, y: 0.425},
	{x: 0.3, y: -0.138},
	{x: 0.4, y: -0.263},
	{x: 0.5, y: 0.447},
	{x: 0.6, y: -0.263},
	{x: 0.7, y: -0.138},
	{x: 0.8, y: 0.425},
	{x: 0.9, y: -0.362},
	{x: 1.0, y: 0.0},
],

/* -- */
       backgroundColor: ['#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa'],
       borderColor: ['#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88'],
       radius: 4,
    }],
 },
 options: {
    responsive: false,
    scales: {
       x: {
          type: 'linear',
          position: 'bottom,'
       }
    }
 },
}{{< /chart >}}


## charts 10
{{< chart 60 240 >}}
{
 type: 'scatter',
 data: {
    datasets: [{
/* -- */

label: "E-val = 0.0",
data: [
	{x: 0.0, y: 0.51},
	{x: 0.1, y: -0.459},
	{x: 0.2, y: 0.408},
	{x: 0.3, y: -0.357},
	{x: 0.4, y: 0.306},
	{x: 0.5, y: -0.255},
	{x: 0.6, y: 0.204},
	{x: 0.7, y: -0.153},
	{x: 0.8, y: 0.102},
	{x: 0.9, y: -0.051},
	{x: 1.0, y: 0.0},
],

/* -- */
       backgroundColor: ['#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa'],
       borderColor: ['#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88'],
       radius: 4,
    }],
 },
 options: {
    responsive: false,
    scales: {
       x: {
          type: 'linear',
          position: 'bottom,'
       }
    }
 },
}{{< /chart >}}


## charts 11
{{< chart 60 240 >}}
{
 type: 'scatter',
 data: {
    datasets: [{
/* -- */

label: "E-val = 0.0",
data: [
	{x: 0.0, y: 0.0},
	{x: 0.1, y: -0.051},
	{x: 0.2, y: 0.102},
	{x: 0.3, y: -0.153},
	{x: 0.4, y: 0.204},
	{x: 0.5, y: -0.255},
	{x: 0.6, y: 0.306},
	{x: 0.7, y: -0.357},
	{x: 0.8, y: 0.408},
	{x: 0.9, y: -0.459},
	{x: 1.0, y: 0.51},
],

/* -- */
       backgroundColor: ['#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa', '#faa'],
       borderColor: ['#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88', '#f88'],
       radius: 4,
    }],
 },
 options: {
    responsive: false,
    scales: {
       x: {
          type: 'linear',
          position: 'bottom,'
       }
    }
 },
}{{< /chart >}}

