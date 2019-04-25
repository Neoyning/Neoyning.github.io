---
layout: post
title:  "A Smooth trajectory generation"
date:   2019-03-13
categories: self-learning
---

### Reference
----------------

This post is some idea about the paper "Minimum Snap Trajectory Generation and Control for Quadrotors" by Daniel Mellinger and Vijay Kumar.
Thanks for thier work, I got a deeper understanding of Trajectory Generation and Optimisation problem with Quadratic programming.

----------------
\\[
 \begin{aligned}
 \dot{x} & = \sigma(y-x) \\\
 \dot{y} & = \rho x - y - xz \\\
 \dot{z} & = -\beta z + xy
 \end{aligned}
\\]

$$
c^\intercal=
\begin{bmatrix}
c_1 & c_2 & \dots&c_{12} \\
\end{bmatrix}
$$
$$
A=\begin{bmatrix}
    -1 & 0 & 0 & \dots  & 0 \\
    0 & -1 & 0 & \dots  & 0 \\
    0 & 0 & -1 & \dots  & 0 \\
    \vdots & \vdots & \vdots & \ddots & \vdots \\
    0 & 0 & 0 & \dots  & -1\\
    1 & 0 & 0 & \dots  & 0 \\
    0 & 1 & 0 & \dots  & 0 \\
    0 & 0 & 1 & \dots  & 0 \\
    \vdots & \vdots & \vdots & \ddots & \vdots \\
    0 & 0 & 0 & \dots  & 1
\end{bmatrix}\quad
b=\begin{bmatrix}
    0\\
    0\\
    0\\
    \vdots\\
    0\\
    P_{1,max}\\
    P_{2,max}\\
    P_{3,max}\\
    \vdots\\
    P_{12,max}
\end{bmatrix}
$$
$$
G=\begin{bmatrix}
1 &1 &\dots&1 \\
\end{bmatrix}
\quad
h=P_{demand}
$$