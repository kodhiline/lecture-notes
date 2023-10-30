---
title: "code of gillette 1983"
date: 2023-10-30T15:03:00+07:00
authors: ['Sparisoma Viridi', 'Nina Siti Aminah', 'Aria Wahyu Wicaksono']
tags: ['sk6091']
draft: false
math: true
url: "0127"
---
{{< toc >}}


## notes
+ Skim Gillette (1983) and still do not understand the matrix and spectra connection. Perhaps previous references therein should be read first.


## matrices c & d
+ Mixture spectra matrix
$$
\mathbf{D} = \left(
\begin{array}{ccc}
0.26 & 0.22 & 0.14 \newline
0.20 & 0.40 & 0.80 \newline
1.60 & 1.20 & 0.40 \newline
0.12 & 0.14 & 0.18
\end{array}
\right)
$$
+ Covariance / correlation marix
$$
\mathbf{C} = \left(
\begin{array}{ccc}
2.682 & 2.074 & 0.858 \newline
2.074 & 1.668 & 0.856 \newline
0.858 & 0.856 & 0.852
\end{array}
\right)
$$
+ Relation
$$
\mathbf{C} = \mathbf{D}^T \mathbf{D}.
$$
+ Code https://onecompiler.com/python/3zrz763xa
```python
import numpy as np

D = np.array(
  [
    [0.26, 0.22, 0.14],
    [0.20, 0.40, 0.80],
    [1.60, 1.20, 0.40],
    [0.12, 0.14, 0.18]
  ]
)
print(D)

DT = D.T
print(DT)

C = DT @ D
print(C)
```
+ Result (confirmed)
```shell
[[0.26 0.22 0.14]
 [0.2  0.4  0.8 ]
 [1.6  1.2  0.4 ]
 [0.12 0.14 0.18]]
[[0.26 0.2  1.6  0.12]
 [0.22 0.4  1.2  0.14]
 [0.14 0.8  0.4  0.18]]
[[2.682 2.074 0.858]
 [2.074 1.668 0.856]
 [0.858 0.856 0.852]]
```


## matrices c, e, l
+ Using previous $\mathbf{C}$.
+ Relation $\mathbf{C}\mathbf{E} =  \mathbf{E} \mathbf{L}$.
+ Result
$$
\mathbf{E} = \left(
\begin{array}{ccc}
0.745 & -0.400 & 0.000 \newline
0.596 & 0.039 & 0.000 \newline
0.300 & 0.916 & 0.000
\end{array}
\right)
$$
$$
\mathbf{L} = \left(
\begin{array}{ccc}
4.688 & 0.000 & 0.000 \newline
0.000 & 0.514 & 0.000 \newline
0.000 & 0.000 & 0.000
\end{array}
\right)
$$
+ Code https://onecompiler.com/python/3zrzg7yfj
```python
import numpy as np
from numpy import linalg as la

C = np.array(
    [
      [2.682, 2.074, 0.858],
      [2.074, 1.668, 0.856],
      [0.858, 0.856, 0.852],
      ]
  )

print("C =",)
print(C)
print()

print("CE = EL")
L, E = la.eig(C)

print("E = ")
print(E.round(3))
print()

print("L = ")
print(np.diag(L).round(3))
print()

```
+ Result (not confirmed)
```shell
C =
[[2.682 2.074 0.858]
 [2.074 1.668 0.856]
 [0.858 0.856 0.852]]

CE = EL
E = 
[[-0.745 -0.535 -0.4  ]
 [-0.596  0.802  0.039]
 [-0.3   -0.267  0.916]]

L = 
[[4.688 0.    0.   ]
 [0.    0.    0.   ]
 [0.    0.    0.514]]
```
+ Notice that eigenvalues are the same but not the eigenvectors.


## refs
+ Paul C. Gillette, Jerome B. Lando, Jack L. Koenig, "Factor analysis for separation of pure component spectra from mixture spectra", Analytical Chemistry, vol 55, no 4, pp 630-633, Apr 1983, url https://doi.org/10.1021/ac00255a011. [pr5ye](https://osf.io/pr5ye)


## dicussion
+ `30-oct-2023` A reference, Gillette (1983), is given. [pr5ye](https://osf.io/pr5ye)
+ `26-oct-2023` Google drive links is given for current available data. [762au](https://osf.io/762au)
