---
title: "m func der diff"
date: 2023-10-02T16:11:00+07:00
authors: ['Sparisoma Viridi']
tags: ['tl2103']
draft: false
math: true
url: "0080"
---
{{< toc >}}


## differentiation and derivative
+ Differentiation is a technique which can be used for analyzing the way in which a functions change, or in particular, it measures how rapidly a function is changing at any point ([HELM, 2008](https://www.ncl.ac.uk/webtemplate/ask-assets/external/maths-resources/images/Intro_diffrntiatn.pdf)).
+ In mathematics, differentiation is a process of finding the derivative, or rate of change, of a function, which can be carried out by purely algegraic manipulations using three basic derivatives, four rules of operation, and a knowledge of how to manipulate functions ([Britannica, 2022](https://www.britannica.com/science/differentiation-mathematics)).
+ Differentiation is a method of computing a derivative which the rate of change of the output $y$ of the function with respect to the change of the variable $x$ ([Nanda, 2023](https://www.tutorialspoint.com/difference-between-differential-and-derivative)).
+ Differentiation is a process that gives the derivative ([TZakrevskiy, 2017](https://math.stackexchange.com/a/2519697/645927)).


## polynomial function
+ It can be represented as its coefficient, e.g.

  $$\tag{1}
  f(x) = \sum_{i = 0}^n a_i \ x^i \equiv [a_n \ \ a_{n-1} \ \ \dots \ \ a_i \ \ \dots \ \ a_1 \ \ a_0].
  $$

+ Its derivative $\displaystyle g(x) = \frac{df(x)}{dx}$ will be

  $$\tag{2}
  g(x) = \sum_{i = 0}^{n-1} b_i \ x^i \equiv [b_n \ \ b_{n-1} \ \ \dots \ \ b_i \ \ \dots \ \ b_1 \ \ b_0].
  $$

+ And the relation between two sets of coefficients $\mathbf{b}$ and $\mathbf{a}$, in term of each element, is

  $$\tag{3}
  b_i = (i+1) \ a_{i+1}, \ \ \ \, i = 1, \ 2, \ 3, \ \dots, \ (n-1).
  $$


## string, inline, function
+ A string representation of a polynomial, e.g.
  ```m
  fstr = 'x^2 + 10x + 1';
  ```
+ A function can be constructed from the string, e.g.
  ```m
  f = inline(fstr);
  ```
+ A value can be calculated from the function, e.g.
  ```m
  f2 = f(2);
  ```
+ Complete code is as follow.
```m
```
