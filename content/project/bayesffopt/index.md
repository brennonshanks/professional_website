---
title: Bayesian Force Field Optimization
date: 2025-06-27T12:00:00.000Z
draft: false
featured: false
authors:
  - admin
tags:
  - statistical mechanics
  - thermodynamics
  - machine learning
image:
  filename: ""
  focal_point: Smart
  preview_only: false
---

Structure and self-assembly are complex, emergent properties of matter that are often poorly captured by conventional molecular simulation models. Both statistical mechanics and empirical studies have shown that incorporating structural experimental data—such as scattering measurements—can significantly improve the accuracy, transferability, and physical consistency of classical force fields. In this work, we apply Bayesian inference and optimization to develop force fields that more accurately reproduce the structural behavior of liquid-state systems.

We develop efficient and simple methods to implement Bayesian inference for molecular simulations using local Gaussian process surrogate models [1] and are currently working on specific applications of Bayesian inference in neutron scattering. For instance, we have shown that neutron scattering data must be very precisely measured in order to directly learn interatomic forces [2], demonstrating for the first time that it is possible to learn subtle features of the interaction potential such as repulsive exponent and dispersion energy. The methodology has recently been integrated into force field development for biologically relevant ions [3] and to learn partial charge distributions from ab initio molecular dynamics trajectories. 

[1] B.L. Shanks, et al. Accelerated Bayesian Inference for Molecular Simulations using Local Gaussian Process Surrogate Models, J. Chem. Theory Comput. (2024), https://doi.org/10.1021/acs.jctc.3c01358

[2] B.L. Shanks, et al. Bayesian Analysis Reveals the Key to Extracting Pair Potentials from Neutron Scattering Data. J. Phys. Chem. Lett. (2024), https://pubs.acs.org/doi/abs/10.1021/acs.jpclett.4c02941#

[3] Fan, S. et al. Charge Scaling Force Field for Biologically Relevant Ions Utilizing a Global Optimization Method. chemRxiv https://doi.org/10.26434/chemrxiv-2025-k63tq (2025).


