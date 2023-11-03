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



## charts
{{< chart 60 240 >}}
{
  type: 'bar',
  data: {
    labels: [-150, -149, -148, -147, -146, -145, -144, -143, -142, -141, -140, -139, -138, -137, -136, -135, -134, -133, -132, -131, -130, -129, -128, -127, -126, -125, -124, -123, -122, -121, -120, -119, -118, -117, -116, -115, -114, -113, -112, -111, -110, -109, -108, -107, -106, -105, -104, -103, -102, -101, -100, -99, -98, -97, -96, -95, -94, -93, -92, -91, -90, -89, -88, -87, -86, -85, -84, -83, -82, -81, -80, -79, -78, -77, -76, -75, -74, -73, -72, -71, -70, -69, -68, -67, -66, -65, -64, -63, -62, -61, -60, -59, -58, -57, -56, -55, -54, -53, -52, -51, -50, -49, -48, -47, -46, -45, -44, -43, -42, -41, -40, -39, -38, -37, -36, -35, -34, -33, -32, -31, -30, -29, -28, -27, -26, -25, -24, -23, -22, -21, -20, -19, -18, -17, -16, -15, -14, -13, -12, -11, -10, -9, -8, -7, -6, -5, -4, -3, -2, -1, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99, 100, 101, 102, 103, 104, 105, 106, 107, 108, 109, 110, 111, 112, 113, 114, 115, 116, 117, 118, 119, 120, 121, 122, 123, 124, 125, 126, 127, 128, 129, 130, 131, 132, 133, 134, 135, 136, 137, 138, 139, 140, 141, 142, 143, 144, 145, 146, 147, 148, 149, 150],
    datasets: [
      {
        label: '1st',
        data: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 2, 0, 0, 0, 0, 0, 8, 0, 0, 14, 0, 0, 13, 0, 0, 27, 0, 0, 36, 0, 0, 61, 0, 0, 123, 0, 0, 156, 0, 0, 215, 0, 0, 293, 0, 0, 374, 0, 0, 475, 0, 0, 567, 0, 0, 633, 0, 0, 762, 0, 0, 812, 0, 0, 805, 0, 0, 823, 0, 0, 713, 0, 0, 691, 0, 0, 554, 0, 0, 496, 0, 0, 351, 0, 0, 289, 0, 0, 220, 0, 0, 178, 0, 0, 123, 0, 0, 70, 0, 0, 44, 0, 0, 30, 0, 0, 13, 0, 0, 13, 0, 0, 8, 0, 0, 5, 0, 0, 2, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
        backgroundColor: 'rgba(150, 150, 255, 0.5)',
      },
    ]
  },
  options: {
    maintainAspectRatio: false,
    scales: {
      yAxes: [{
        scaleLabel: {
          display: true,
          labelString: 'Occurence'
        },
        ticks: {
          beginAtZero: true
        }
      }],
      xAxes: [{
        scaleLabel: {
          display: true,
          labelString: 'Final position'
        }
      }],
    },
    plugins: {
      legend: false
    }
  }
}
{{< /chart >}}
