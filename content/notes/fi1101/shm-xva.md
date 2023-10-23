---
title: "shm x, v, a"
date: 2023-10-22T19:28:00+07:00
authors: ['Sparisoma Viridi']
tags: ['fi1101']
math: true
draft: false
url: "0109"
---
{{< toc >}}


## related notes
+ [m09-2: oscillations](../0097/)


## simple harmonic motion
+ It is periodic motion that is a sinusoidal function of time
  $$\tag{1}
  \begin{array}{rcl}
  x(t) & = & x_m \sin \theta \newline
  & = & x_m \sin (\omega t + \phi).
  \end{array}
  $$
+ It is solution of an ODE
  $$\tag{2}
  \frac{d^2x}{dt^2} + \omega^2 x = 0.
  $$


## variables
+ Each of variables meaning in Eqn (1) are as follow.
    
  Variable | Meaning | Unit
  :-: | :-: | :-:
  $x$ | displacement | m
  $x_m$ | maximum displacement, amplitude | m
  $\omega$ | angular frequency | rad/s
  $t$ | time | s
  $\theta$ | phase | rad
  $\phi$ | initial phase, phase angle, phase constant | rad


## phase constant
+ It shifts the sine or cosine function.
+ For certain $\phi_s$ and $\phi_c$ following relation,
  $$\tag{3}
  \cos (\omega t + \phi_c) = \sin (\omega t + \phi_s),
  $$
  will hold.


## trigonometric identities
Thera identities in 1st - 4th quadrants, map sine and cosine function to 1st quadrant.

### 1st quadrant
$$\tag{4.Q1.1}
\cos (2\pi + \beta) = \cos \beta
$$
$$\tag{4.Q1.2}
\sin (2\pi + \beta) = \sin \beta
$$
$$\tag{4.Q1.3}
\cos (\tfrac12 \pi - \beta) = \sin \beta
$$
$$\tag{4.Q1.4}
\sin (\tfrac12 \pi - \beta) = \cos \beta
$$

### 2nd quadrant
$$\tag{4.Q2.1}
\cos (\pi - \beta) = -\cos \beta
$$
$$\tag{4.Q2.2}
\sin (\pi - \beta) = \sin \beta
$$
$$\tag{4.Q2.3}
\cos (\tfrac12 \pi + \beta) = -\sin \beta
$$
$$\tag{4.Q2.4}
\sin (\tfrac12 \pi + \beta) = \cos \beta
$$

### 3rd quadrant
$$\tag{4.Q3.1}
\cos (\pi + \beta) = -\cos \beta
$$
$$\tag{4.Q3.1}
\sin (\pi + \beta) = -\sin \beta
$$
$$\tag{4.Q3.3}
\cos (\tfrac32 \pi - \beta) = -\sin \beta
$$
$$\tag{4.Q3.4}
\sin (\tfrac32 \pi - \beta) = -\cos \beta
$$

### 4th quadrant
$$\tag{4.Q4.1}
\cos (2\pi - \beta) = \cos \beta
$$
$$\tag{4.Q4.1}
\sin (2\pi - \beta) = -\sin \beta
$$
$$\tag{4.Q4.3}
\cos (\tfrac32 \pi + \beta) = \sin \beta
$$
$$\tag{4.Q4.4}
\sin (\tfrac32 \pi + \beta) = -\cos \beta
$$

The two Eqns (4.Q4.1) and (4.Q4.2) also mean that
+ $\cos (-\beta) = \cos \beta$,
+ $\sin (-\beta) = -\sin \beta$.

### examples
+ $\sin 330 \degree$
```
sin(-330) = sin(-360 + 30) = sin(30)
sin(-330) = -sin(330) = -sin(360-30) = sin(30)
sin(-330) = -sin(330) = -sin(270+60) = cos(60) 
```
{{< mermaid >}}
flowchart LR
  A --> B --> C
  A --> D --> E --> C
  D --> F --> G --> C
  A(["sin (&mdash;330)"])
  B(["sin (&mdash;360 + 30)"])
  C(["sin 30"])
  D(["&mdash;sin 330 "])
  E(["&mdash;sin (360 &mdash; 30)"])
  F(["&mdash;sin (270 + 60)"])
  G(["cos 60"])
{{< /mermaid >}}

+ $\cos 120 \degree$
```
```
