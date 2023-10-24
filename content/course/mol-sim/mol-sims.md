---
title: Molecular Simulations
type: book
weight: 50
math: true
tags:
  - mol-sims
---

## Why Use Computer Simulations?

We have just completed a rather quick introduction to statistical mechanics, and found that we could connect results from classical mechanics, quantum mechanics, and thermodynamics by studying statistical ensembles of many particles. Indeed, we were able to recover the ideal gas law by considering a collection of non-interacting particles and derive microscopic expressions for entropy and free energy. The power of the statistical mechanics framework is evident.

However, statistical mechanics actually has very few analytically tractable problems. Perhaps the most famous is the Nobel prize winning 2D Ising model, which represents a lattice of particles attached by springs. Some other examples include the ideal gas and Einstein crystal. Despite the difficulty in obtaining analytical solutions, many statistical mechanics problems succumb rather easily to computational techniques. Computer simulations offer an easy and affordable route to study how microscopic details of a system influence the macroscopic properties of experimental interest. These simulations can be applied to systems that we can't study experimentally due to extreme pressures and/or temperatures or in extremely hazardous environments such as nuclear reactors or planetary cores. Finally, computer simulation "experiments" can serve as a bridge between pure theory and experiment.

## Force Fields for Molecular Simulation

Recall that the probability distribution functions for a system of interest were assumed to be functions of the system Hamiltonian, which is just the sum of the kinetic and potential energy contributions on the system. In our notation, we wrote the Hamiltonian of an atomic system in terms of its position and momentum so that,

$$
    H(q^f, p^f) = K(p^f) + V(q^f)
$$

where $K$ is the kinetic part and $V$ is the potential part of the Hamiltonian. In general, we could write kinetic and potential parts of the Hamiltonian for each individual electron and nucleus separately, but in computer simulations of liquids we will often not model electrons explicitly, reducing the computational complexity of the simulation. This amounts to the approximation that the electrons move so quickly that they redistribute around a nucleus at every timestep of nuclear motion (known as the Born-Oppenheimer approximation).

For a simple atomic system, the kinetic part of the Hamiltonian is just,

$$
    K(p^f) = \sum_i \frac{||\mathbf{p_i}||^2}{2m_i}
$$

which is just the sum of the kinetic energy contribution for all atoms in the system $i = 1, ..., N$ in each direction $(x,y,z)$.

As you recall from our coverage of the Velocity-Verlet algorithm for time integration of Hamilton's equations of motion, we need to compute the forces on the atoms according to,

$$
    \mathbf{F} = - \nabla V(q^f)
$$

where $\nabla$ is the gradient operator. The hard part, and what controls the behavior of the atomic system, is specific form of $V(q^f)$. Based on this form, the simulation can be reactive or non-reactive, all-atom or coarse grained, and/or general purpose or highly specific.

### Bonded Interactions

For force fields, the $V(q^f)$ can be decomposed into a bonded and non-bonded part,

$$
    V(q^f) = V_{bound}(q^f) + V_{unbound}(q^f)
$$

where the bonded interactions typically include contributions from bond stretching, vibrations, and torsions,

$$
    V_{bound}(q^f) = V_{stretch}(q^f) + V_{bend}(q^f) + V_{torsion}(q^f)
$$

Bond stretching is usually modeled as a harmonic oscillator over all bonded pairs $ij$,

$$
    V_{stretch}(q^f) = \frac{1}{2} \sum_{ij} k_{bond, ij} (x - x_{0,ij})^2
$$

where $x_{0,ij}$ is the equilibrium bond length of bond $ij$ and $k_{bond, ij}$ is the bond spring constant. As an example, the bond between the carbons in ethane $H_3C-CH_3$ has an equilibrium bond length of 1.52 angstrom and a bond spring constant of 317 kcal/mol/angstrom$^2$. The frequency of vibration can be solved with the generalized harmonic oscillator for a two mass system attached to a spring to give a bond frequency $\omega = \sqrt{k/\mu}$, where $\mu$ is the reduced mass, $\mu = \frac{m_1m_2}{m_1 + m_2}$, of about 10 femtoseconds.

Angle bending is also modeled as a harmonic oscillator, but this time over combinations of three bonded atoms,

$$
    V_{bend}(q^f) = \frac{1}{2} \sum_{ijk} k_{angle, ijk} (\theta - \theta_{0,ijk})^2
$$

where $\theta_{0,ijk}$ is the equilibrium bond angle of bonds $ijk$ and $k_{angle, ijk}$ is the bond spring constant. 

Proper torsion, which describes the rotation of 4 atoms around a central bond, is usually modeled with a cosine series expansion that is a well-behaved and has multiple minima (invoking symmetry),

$$
    V_{torsion, prop}(q^f) = \sum_{n = 0}^N k_n (1 + \cos (n \phi - \delta) )
$$

where $n$ is the number of terms in the cosine expansion, $\delta$ is the angle at which the function has a minimum, and $\phi$ is the angle of rotation around the central bond. Torsion is considered 'improper' if the molecule is planar but flexes out of plane. This interaction is usually modeled as a harmonic oscillator,

$$
    V_{torsion, improp}(q^f) = \frac{1}{2} \sum_{ijk} k_{improp, ijk} (\theta - \xi_{0,ijk})^2
$$

where the sum goes over all bound, 4 atom complexes that could have improper torsions (\textit{e.g.} $BCl_3$). This gives a standard bonded contribution to the potential part or the Hamiltonian as,

$$
    V_{bound}(q^f) = \frac{1}{2} \sum_{ij} k_{bond, ij} (x - x_{0,ij})^2 + \frac{1}{2} \sum_{ijk} k_{angle, ijk} (\theta - \theta_{0,ijk})^2 + \\ 
    \sum_{n = 0}^N k_n (1 + \cos (n \phi - \delta) ) + \frac{1}{2} \sum_{ijk} k_{im, ijk} (\theta - \xi_{0,ijk})^2
$$

### Non-Bonded Interactions

The potential part, $V$, is what contains the most interesting information for a computer simulation since it defines all of the interactions of particles with their environment and each other. In general, we can divide up the potential part into a set of contributions from singlets, pairs, triplets, all the way to $N$ body terms such that,

$$
    V(q^f) = \sum_i v_1(\mathbf{q}_i) + \sum_i \sum_{j \neq i} v_2(\mathbf{q_i}, \mathbf{q_j}) + \sum_i \sum_{j \neq i} \sum_{k \neq i,j} v_3(\mathbf{q}_i, \mathbf{q}_j, \mathbf{q}_k) + ...
$$

where the series at an $N$ sum term. The first term represents the interactions of particles with an external field, the second term depends on the relative positions of pairs of atoms, the third triples of atoms, and so on. It has been shown that the external field, pair, and triplet are highly significant in modeling liquids. Therefore, four and higher-order terms are often neglected in molecular simulations and not modeled explicitly. 

Despite the relative importance of three-body terms in liquid simulations, they are actually rarely used. Instead, three body terms are effectively included in a pair potential by defining an effective pair potential so that,

$$
    V_{unbound}(q^f) \approx \sum_i v_1(\mathbf{q_i}) + \sum_i \sum_{j \neq i} v^{eff}_2(\mathbf{q}_i, \mathbf{q}_j)
$$

where $v^{eff}_2(\mathbf{q}_i, \mathbf{q}_j)$ is optimized to some set of experimental data (often density, heat capacity, diffusivity, etc). The most significant consequence of this approximation is that the effective pair potential will now significantly depend on thermodynamic state whereas the true pair potential should not.

The pairwise additive part typically includes both van der Waals (in the form of a Lennard-Jones potential) and electrostatic interactions,

$$
    V_{unbound}(q^f) =     \sum_{ij} 4 \epsilon_{ij} \bigg[ \bigg(\frac{\sigma_{ij}}{r_{ij}}\bigg)^{12} - \bigg(\frac{\sigma_{ij}}{r_{ij}}\bigg)^6 \bigg] + \sum_{ij} \frac{q_i q_j}{4 \pi \epsilon_0 r_{ij}}
$$

where $ij$ indexes over all non-bonded atoms, $\sigma$ is the collision diameter or effective atomic size, $\epsilon$ is the dispersion energy or depth of the potential well, $q_i$ is the Coulombic charge on atom $i$, and $r_{ij}$ is the distance between atoms $i$ and $j$. We often optimize these potential parameters to a set of thermodynamic properties and then employ 'mixing rules' to get all of the parameters of the cross interactions (when $i$ and $j$ are different atom types) so that,

$$
    \sigma_{ij} = \frac{\sigma_i + \sigma_j}{2}
$$

$$
    \epsilon_{ij} = \sqrt{\epsilon_i \epsilon_j}
$$
