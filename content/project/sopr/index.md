---
title: Structure Optimized Potential Refinement (SOPR)
date: 2024-01-03T12:00:00.00Z
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

Structure-optimized potential refinement (SOPR) is a machine learning assisted iterative Boltzmann inversion method designed to predict accurate and transferable interaction potentials from a provided set of site-site partial radial distribution functions. SOPR leverages Henderson's inverse theorem and Gaussian process regression (GPR) to generate interaction potentials from scattering that are continuous, smooth, and transferable to other thermodynamic properties. The SOPR method enables new use-cases for neutron diffraction, such as the development of accurate force fields for structure and self-assembly predictions and the quantification of many-body interactions in fluid ensembles.

SOPR has been successfully implemented in noble gas fluids [1] and more recently a set of molecular liquids (benzene, methane, and water) [2]. These studies represent the most complete solution for the inverse problem ever demonstrated for real systems. SOPR potentials derived from neutron scattering data on noble gases have also been shown to be consistent with the quantum Drude oscillator model of atomic dipole polarization [3], providing evidence that the nonparametric form of the SOPR potential can learn subtle physics that extends beyond its classical representation.  

## Current Challenges

1. Currently, the site-site partial radial distribution functions must be calculated from experimental neutron/X-ray diffraction data using existing techniques such as empirical potential structure refinement (EPSR) or reverse Monte Carlo (RMC).

2. Furthermore, we want to continue to implement SOPR for systems in which understanding structure and self-assembly are critical for engineering and design. Since the SOPR potentials are also transferable to other thermodynamic properties, we aim to use SOPR to predict thermophysical properties in systems where experimental data is difficult or impossible to obtain. Such systems include high temperature and pressure liquid metals, supercritical fluids, and complicated mixtures of liquid organics.
   
3. Finally, SOPR may have further uses in the realm of machine learning potentials (MLPs). A recent paper has shown that IBI can refine MLP potentials to improve structural representations, however, the work did not use SOPRs probabilistic framework to perform this refinement in a rigorous way.  

[1] B.L. Shanks, J.J. Potoff, M.P. Hoepfner. Transferable Force Fields from Experimental Scattering Data with Machine Learning Assisted Structure Refinement. J. Phys. Chem. Lett. 11512–11520 (2022) https://pubs.acs.org/doi/10.1021/acs.jpclett.2c03163

[2] A.R. Shazed, B.L. Shanks, H.W. Sullivan, M.P. Hoepfner, (In review) Structure-optimized potential refinement for molecular liquids (2025)

[3] B.L. Shanks, H.W. Sullivan, P. Jungwirth, M.P. Hoepfner. Experimental Evidence of Quantum Drude Oscillator Behavior in Liquids Revealed with Probabilistic Iterative Boltzmann Inversion. J. Chem. Phys. (2025)



