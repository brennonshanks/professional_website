---
title: Structure Optimized Potential Refinement (SOPR)
date: 2023-07-28T12:00:00.00Z
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

Structure-optimized potential refinement (SOPR) is designed to predict accurate and transferable interaction potentials from a provided set of site-site partial radial distribution functions, known as the inverse problem in statistical mechanics. SOPR leverages the Henderson Inverse Theorem and Gaussian Process Regression to generate interaction potentials that well-represent fluid structures, are continuous, smooth, and transferable to other thermodynamic properties. The SOPR method enables new use-cases for neutron diffraction, such as the development of accurate force fields for structure and self-assembly predictions and the quantification of many-body interactions in fluid ensembles.

SOPR has been successfully implemented in noble gas fluids [1] and more recently a set of molecular liquids (benzene, methane, and water) [2]. These studies represent the most complete solution for the inverse problem ever demonstrated for real systems.  

## Current Challenges

1. Currently, the site-site partial radial distribution functions must be calculated from experimental neutron/X-ray diffraction data using existing techniques such as empirical potential structure refinement (EPSR) or reverse Monte Carlo (RMC). However, we are currently working towards eliminating SOPR's reliance on these methods by implementing machine learning techniques to infer these quantities probabilistically.

2. Furthermore, we want to continue to implement SOPR for systems in which understanding the structure and self-assembly are critical. Since the SOPR potentials are also transferable to other thermodynamic properties, we aim to also evaluate complex thermodynamic quantities in systems where experimental data is difficult or impossible to obtain. Such systems include high temperature and pressure liquid metals, supercritical fluids, and complicated mixtures of liquid organics.

[1]  1. Shanks, B. L., Potoff, J. J. & Hoepfner, M. P. Transferable Force Fields from Experimental Scattering Data with Machine Learning Assisted Structure Refinement. J. Phys. Chem. Lett. 11512–11520 (2022) doi:10.1021/acs.jpclett.2c03163.

[2] A.R. Shazed, B.L. Shanks, M.P. Hoepfner, (In review) Structure-optimized potential refinement for molecular liquids (2023)

