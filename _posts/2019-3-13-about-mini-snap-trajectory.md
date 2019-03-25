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