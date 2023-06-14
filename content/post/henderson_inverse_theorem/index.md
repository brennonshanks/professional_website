---
title: The Henderson Inverse Theorem
date: 2023-05-26T05:53:47.038Z
draft: false
featured: false
authors:
  - admin
tags:
  - statistical mechanics
image:
  filename: ""
  focal_point: Smart
  preview_only: false
---

The content of the Henderson Inverse Theorem is as follows: Two systems with Hamiltonians of the form,

$$
  \mathcal{H} = \sum_i \frac{p_i^2}{2m} + \frac{1}{2} \sum_{i \neq j} u(|\mathbf{r_i} - \mathbf{r_j}|)
$$

with the same radial distribution function, $g^{(2)}(\mathbf{r_i},\mathbf{r_j})$,

$$
g^{(2)}(\mathbf{r_i},\mathbf{r_j}) = \frac{1}{\rho^2}\bigg\langle \sum_i \sum_j \delta(\mathbf{r} - \mathbf{r_i}) \delta(\mathbf{r}' - \mathbf{r_j}) \bigg\rangle
$$

have pair potentials, $u(|\mathbf{r_i} - \mathbf{r_j}|)$, that differ by at most a trivial constant.

Proof: Let $\rho_1$ and $\rho_2$ be positive, trace-class, and linear density operators on a Hilbert space, $H$, such that $Tr(\rho_i) = 1$. Then we can express the states $\rho_1$ and $\rho_2$ in an arbitrary basis of $H$ such that,

$$
\rho_1 = \sum_\alpha p_\alpha \braket{\alpha}{\alpha}
$$

