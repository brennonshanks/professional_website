---
title: The Henderson Inverse Theorem
date: 2023-06-13T05:53:47.038Z
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

The Henderson Inverse Theorem is an important result on the relationship between the radial distribution function and pairwise additive potential in a statistical ensemble. This theorem is the basis for the structure-optimized potential refinement algorithm and provides a variational solution to the statistical mechanical inverse problem. 

We first need to establish the Gibbs and Gibbs-Bogoliubov inequalities for a quantum system. The Gibbs inequality is an important result about the information entropy of a system while the Gibbs-Bogoliubov inequality establishes an important relationship between the free energy and entropy in the canonical ensemble.

## The Gibbs Inequality

Proof: Let $\rho_1$ and $\rho_2$ be positive, trace-class, and linear density operators on a Hilbert space, $H$, such that $Tr(\rho_i) = 1$. Then we can express the states $\rho_1$ and $\rho_2$ in an arbitrary basis of $H$ such that,

$$
\rho_1 = \sum_\alpha p_\alpha \ket{\alpha} \bra{\alpha}
$$

$$
\rho_2 = \sum_\alpha q_\alpha \ket{\alpha} \bra{\alpha}
$$

We then compute the difference between the cross entropy, $\rho_1 \log (\rho_2)$, and information entropy of $\rho_1$, $\rho_1 \log (\rho_1)$,

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

Proof: Suppose we take the state $\rho_2$ in the canonical ensemble so that,

$$
\rho_2 = \exp(-\beta \mathcal{H_2}) / Z
$$

where $\beta$ is the inverse thermal energy, $\mathcal{H_2}$ is the Hamiltonian, and $Z$ is the partition function. Then for some $\rho_1$ we have,

$$
Tr(\rho_1 (-\beta \mathcal{H_2} - \log Z)) \leq Tr(\rho_1 \log (\rho_1)) = - S_1 / k_B
$$

where $S_1 = -k_B Tr(\rho_1 \log (\rho_1))$ is the entropy of system 1 and $k_B$ is the Boltzmann constant. Since the trace is a linear operator, we can separate the argument of the trace on the left hand side and divide both sides by the thermodynamic $\beta$ to obtain,

$$
Tr(\rho_1\mathcal{H_2}) + k_BT \log Tr(Z) \geq + T S_1
$$

But $Tr(\rho_1\mathcal{H_2})$ is just the expectation of $\mathcal{H_2}$ over system state 1 and $-k_BT \log Tr(Z)$ is the definition of the Helmholtz free energy in the Canonical ensemble. Thus,

$$
F_2 \leq \langle \mathcal{H_2} \rangle_1  - T S_1
$$

For system 1, 

$$
F_1 \leq \langle \mathcal{H_1} \rangle_1  - T S_1
$$

Combining the two expressions gives us the Gibbs-Bogoliubov inequality,

$$
F_2 \leq F_1 + \langle \mathcal{H_2} - \mathcal{H_1} \rangle_1
$$

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

Proof: Suppose that two systems with a pairwise additive Hamiltonian have equal radial distribution functions and $u_1 - u_2 \neq c$ where $c$ is some constant. Then,

$$
\langle \mathcal{H_2} - \mathcal{H_1} \rangle_1 \neq c
$$

and since the Helmholtz free energies are constants,

$$
F_2 - F_1 < \langle \mathcal{H_2} - \mathcal{H_1} \rangle_1
$$

where we lose the possibility of equality from the Gibbs-Bogoliubov inequality. Now, we can expand the expectation of the Hamiltonian in terms of the radial distribution function (since the system is pairwise additive) so that,

$$
F_2 - F_1 < \frac{n}{2} \int [u_2 - u_1] g_1(\mathbf{r}) d^3\mathbf{r}
$$

and the same holds for a swap of the indices,

$$
F_1 - F_2 < \frac{n}{2} \int [u_1 - u_2] g_2(\mathbf{r}) d^3\mathbf{r}
$$

Combining these two equations gives,

$$
0 < 0
$$

a contradiction. Therefore, our premise that the radial distribution functions are equal while the pairwise additive potential energies differ by a trivial constant must be false. The only other possible difference between the potential energies is constant, so this must be true to satisfy the Gibbs-Bogoliubiv inequality.

The Henderson Inverse Theorem is a valuable tool to predict this unique (up to a constant) potential energy function from the radial distribution function of a fluid. It is often employed in coarse-grained models under the name of iterative Boltzmann inversion (IBI) and in experimental data with empirical potential structure refinement (EPSR) or structure-optimized potential refinement (SOPR) [1].

[1] Brennon L. Shanks, Jeffrey J. Potoff, and Michael P. Hoepfner The Journal of Physical Chemistry Letters 2022 13 (49), 11512-11520
DOI: 10.1021/acs.jpclett.2c03163

