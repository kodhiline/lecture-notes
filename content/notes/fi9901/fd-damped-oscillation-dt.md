---
title: "fd damped oscillation dt"
date: 2023-09-25T19:56:00+07:00
authors: ['Sparisoma Viridi']
tags: ['fi9900']
draft: false
math: true
url: "0066"
---
{{< toc >}}


## description
+ Equation of motion of a damped oscillation
$$\tag{1}
\ddot{x} + 2 \gamma \dot{x} + \omega^2 x = 0.
$$
+ Numerical approach using Finite Difference
$$\tag{2}
f(t + \Delta t) = f(t) + \frac{df(t)}{dt} \Delta t.
$$
+ Solution for $x$ if $\gamma = \gamma(t)$ and $\omega = \omega(t)$, but now only for constants values in order to find suitable $\Delta t$.


## formulation
+ Time
$$\tag{7}
t_{n+1} = t_n + \Delta t, \ \ \ n = 0, 1, 2, \dots. 
$$
+ Acceleration
$$\tag{4}
\ddot{x}(t_n) = - 2 \gamma \dot{x}(t_n) - \omega^2 x(t_n).
$$
+ Velocity
$$\tag{5}
\dot{x}(t_{n+1}) = \dot{x}(t_n) + \ddot{x}(t_n) \Delta t. 
$$
+ Position
$$\tag{6}
x(t_{n+1}) = x(t_n) + \dot{x}(t_n) \Delta t. 
$$


## initial conditions
+ Iteration
$$\tag{7}
n = 0.
$$
+ Time
$$\tag{8}
t = t_0.
$$
+ Velocity
$$\tag{9}
v(t_0) = v_0
$$
+ Posittion
$$\tag{10}
x(t_0) = x_0.
$$


## parameters
+ Oscillation period
$$\tag{11}
T = 2 \pi \sqrt{\frac{m}{k}}.
$$
+ Time step
$$\tag{12}
\Delta t \lt \lt T.
$$
+ Simple harmonic motion
$$\tag{13}
\gamma = 0.
$$
