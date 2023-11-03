---
title: "eigenvalue problem intro"
date: 2023-11-03T10:41:00+07:00
authors: ['Sparisoma Viridi']
tags: ['fi4002']
draft: false
math: true
url: "0135"
---
{{< toc >}}


## code
```python
import math
import numpy as np
from numpy.linalg import eig

# matrix
print("M = ")
M = np.array([
  [2, 9],
  [8, 1]
])
print(M)
print()

# eigenvalue, eigenvector
val, vec = eig(M)

# eigenvalues
print("Eigenvalue =", val)
print()

# eigenvectors
print("v =")
print(vec)
print()

v1 = vec[:, 0]
print("v1 =", v1)
print()

v2 = vec[:, 1]
print("v2 =", v2)
print()

# check relations
Mv1 = M @ v1
print("M v1 / val1 =", end=' ')
print(Mv1 / val[0])
print()

Mv2 = M @ v2
print("M v2 / val2 =", end=' ')
print(Mv2 / val[1])
print()
```
+ url https://onecompiler.com/python/3zschkwhd


## results
```shell
M = 
[[2 9]
 [8 1]]

Eigenvalue = [10. -7.]

v =
[[ 0.74740932 -0.70710678]
 [ 0.66436384  0.70710678]]

v1 = [0.74740932 0.66436384]

v2 = [-0.70710678  0.70710678]

M v1 / val1 = [0.74740932 0.66436384]

M v2 / val2 = [-0.70710678  0.70710678]
```


## theory
+ matrix
$$\tag{1}
\left[
\begin{matrix}
2 & 9 \newline
8 & 1
\end{matrix}
\right]
\left[
\begin{matrix}
v_1 \newline
v_2
\end{matrix}
\right] =
\lambda
\left[
\begin{matrix}
v_1 \newline
v_2
\end{matrix}
\right]
$$

$$\tag{2}
\left[
\begin{matrix}
2 & 9 \newline
8 & 1
\end{matrix}
\right]
\left[
\begin{matrix}
v_1 \newline
v_2
\end{matrix}
\right] =
\lambda
\left[
\begin{matrix}
1 & 0 \newline
0 & 1
\end{matrix}
\right]
\left[
\begin{matrix}
v_1 \newline
v_2
\end{matrix}
\right]
$$

$$\tag{3}
\left[
\begin{matrix}
2 & 9 \newline
8 & 1
\end{matrix}
\right]
\left[
\begin{matrix}
v_1 \newline
v_2
\end{matrix}
\right] -
\lambda
\left[
\begin{matrix}
1 & 0 \newline
0 & 1
\end{matrix}
\right]
\left[
\begin{matrix}
v_1 \newline
v_2
\end{matrix}
\right] = 0
$$

$$\tag{4}
\left[
\begin{matrix}
2 - \lambda & 9 \newline
8 & 1 - \lambda
\end{matrix}
\right]
\left[
\begin{matrix}
v_1 \newline
v_2
\end{matrix}
\right] = 0
$$

+ determinant $|M| = 0$