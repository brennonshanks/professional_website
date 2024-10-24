---
title: Bayesian Force-Field Optimization
date: 2023-07-27T12:00:00.000Z
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

Structure and self-assembly are complex, emergent properties of matter that are often misrepresented by existing molecular simulation models. In this project, we use Bayesian optimization, an accurate and robust statistical method, to optimize novel force fields based on experimental neutron/X-ray diffraction data to better model the structural behavior of liquid state systems.

We have developed an efficient and simple method to implement Bayesian inference for molecular simulations using local Gaussian process surrogate models [1] and are currently working on specific applications of Bayesian inference in neutron scattering. For instance, we have shown that neutron scattering data must be very precisely measured in order to directly learn interatomic forces [2], demonstrating for the first time that it is possible to learn subtle features of the interaction potential such as repulsive exponent and dispersion energy.

[1] B.L. Shanks, H.W. Sullivan, A. R. Shazed and M.P. Hoepfner, Accelerated Bayesian Inference for Molecular Simulations using Local Gaussian Process Surrogate Models, J. Chem. Theory Comput., https://doi.org/10.1021/acs.jctc.3c01358

[2] B.L. Shanks, H.W. Sullivan, M.P. Hoepfner. Bayesian Analysis Reveals the Key to Extracting Pair Potentials from Neutron Scattering Data. arXiv (2024).
