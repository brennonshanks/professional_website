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

## The Henderson Inverse Theorem

The content of the Henderson Inverse Theorem is as follows: Two systems with Hamiltonians of the form,

$$
  \mathcal{H} = \sum_i \frac{p_i^2}{2m} + \frac{1}{2} \sum_{i \neq j} u(|\mathbf{r_i} - \mathbf{r_j}|)
$$

with the same radial distribution function, $g^{(2)}(\mathbf{r_i},\mathbf{r_j})$,

$$
g^{(2)}(\mathbf{r_i},\mathbf{r_j}) = \frac{1}{\rho^2}\bigg\langle \sum_i \sum_j \delta(\mathbf{r} - \mathbf{r_i}) \delta(\mathbf{r}' - \mathbf{r_j}) \bigg\rangle
$$

have pair potentials, $u(|\mathbf{r_i} - \mathbf{r_j}|)$, that differ by at most a trivial constant.

Proof: We first need to establish the Gibbs and Gibbs-Bogoliubov inequalities for a quantum system. The Gibbs inequality is an important result about the information entropy of a system while the Gibbs-Bogoliubov inequality establish important relationships between the free energy and entropy in the canonical ensemble.

## The Gibbs Inequality

Proof: Let $\rho_1$ and $\rho_2$ be positive, trace-class, and linear density operators on a Hilbert space, $H$, such that $Tr(\rho_i) = 1$. Then we can express the states $\rho_1$ and $\rho_2$ in an arbitrary basis of $H$ such that,

$$
\rho_1 = \sum_\alpha p_\alpha \ket{\alpha} \bra{\alpha}
$$

$$
\rho_2 = \sum_\alpha q_\alpha \ket{\alpha} \bra{\alpha}
$$

We then compute the difference between the cross entropy, $\rho_1 \log (\rho_2)$, and information of entropy of $\rho_1$, $\rho_1 \log (\rho_1)$,

$$
\rho_1 \log (\rho_2) - \rho_1 \log (\rho_1) = \sum_{\alpha,\beta} [p_\alpha \ket{\alpha} \bra{\alpha} \log (q_\beta) \ket{\beta} \bra{\beta} - p_\alpha \ket{\alpha} \bra{\alpha} \log (p_\beta) \ket{\beta} \bra{\beta}]
$$

and since ${\alpha}$ and ${\beta}$ are orthonormal bases,

$$
= \sum_{\alpha} [p_\alpha \log (q_\alpha) - p_\alpha \log (p_\alpha)]\ket{\alpha} \bra{\alpha}
$$

Taking the trace of this operator we obtain,

$$
Tr(\rho_1 \log (\rho_2) - \rho_1 \log (\rho_1)) = \sum_{\alpha} [p_\alpha \log (q_\alpha) - p_\alpha \log (p_\alpha)] = \sum_{\alpha} p_\alpha \log \frac{q_\alpha}{p_\alpha}
$$

Note that since $\log x \leq x - 1$,

$$
\sum_{\alpha} p_\alpha \log \frac{q_\alpha}{p_\alpha} \leq \sum_{\alpha} [q_\alpha - p_\alpha] = 0
$$

and finally, since the trace is a linear operator, this means that,

$$
Tr(\rho_1 \log (\rho_2)) \leq Tr(\rho_1 \log (\rho_1))
$$

## The Gibbs-Bogoliubov Inequality

Suppose we take the state $\rho_2$ in the canonical ensemble so that,

$$
\rho_2 = \exp(-\beta \mathcal{H_2}) / Z
$$

where $\beta$ is the inverse thermal energy, \mathcal{H_2} is the Hamiltonian, and $Z$ is the partition function. Then for some $\rho_1$ we have,

$$
Tr(\rho_1 (-\beta \mathcal{H_2} - \log Z)) \leq Tr(\rho_1 \log (\rho_1)) = -\beta S_1
$$

