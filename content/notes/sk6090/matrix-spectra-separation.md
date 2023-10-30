---
title: "matrix spectra separation"
date: 2023-10-30T15:03:00+07:00
authors: ['Aria Wahyu Wicaksono', 'Nina Siti Aminah', 'Sparisoma Viridi']
tags: ['sk6091']
draft: false
math: true
url: "0127"
---
{{< toc >}}


## dicussion
+ `30-oct-2023` A reference, Gillette (1983), is given. [pr5ye](https://osf.io/pr5ye)
+ `26-oct-2023` Google drive links is given for current available data. [762au](https://osf.io/762au)



## 30-oct-2023
+ Skim Gillette (1983) and still do not understand the matrix and spectra connection. Perhaps previous references therein should be read first.

### $\mathbf{C}$ and $\mathbf{D}$ matrices
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


## refs
+ Paul C. Gillette, Jerome B. Lando, Jack L. Koenig, "Factor analysis for separation of pure component spectra from mixture spectra", Analytical Chemistry, vol 55, no 4, pp 630-633, Apr 1983, url https://doi.org/10.1021/ac00255a011. [pr5ye](https://osf.io/pr5ye)
