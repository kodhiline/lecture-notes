---
title: "m inline poly fzero"
date: 2023-10-02T04:07:00+07:00
authors: ['Sparisoma Viridi']
tags: ['tl2103']
draft: false
math: true
url: "0078"
---
{{< toc >}}


## inline
+ Purpose: Define a function in the same `.m` file.
+ Note: Filename should not be `inline.m`, which could triggered error message.
+ Example is `func_inline.m` as follow.
  ```m
  f = inline('x^2 + 2.34');
  fprintf("x\tf(x)\n")
  for x = 0:4
   fprintf('%.0f\t%.2f\n', x, f(x)) 
  end
  ```
+ Result
  ```
  >> func_inline
  x	f(x)
  0	2.34
  1	3.34
  2	6.34
  3	11.34
  4	18.34
  ```


## fzero
+ Purpose: Find root of a function with initial guess.
+ Example is as follow.
  ```m
  f = inline('x^2 + 6.25');
  x = fzero(f, 4);
  fprintf('Equation \n');
  disp(f)
  fprintf('root = %0.2f', x)
  ```
+ Result
  ```
  Equation 

       Inline function:
       f(x) = x^2 - 6.25

  root = 2.50
  ```

## polynomial
+ A polynomial of $n$ degree is defined as
  $$\tag{1}
  p_n(x) = \sum_{i = 1}^n c_n x^n.
  $$
+ Its coefficient can be stored in a vector or array as follow
$$\tag{2}
c = [c_n \ \ c_{n-1} \ \ \dots \ \ c_i \ \ \dots \ \ c_1 \ \ c_0 ].
$$
