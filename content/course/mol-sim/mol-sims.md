---
title: Molecular Simulations
type: book
weight: 50
math: true
tags:
  - mol-sims
---

<!--more-->

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

where the sum goes over all bound, 4 atom complexes that could have improper torsions (ex: $BCl_3$). This gives a standard bonded contribution to the potential part or the Hamiltonian as,

$$
    V_{bound}(q^f) = \frac{1}{2} \sum_{ij} k_{bond, ij} (x - x_{0,ij})^2 + \frac{1}{2} \sum_{ijk} k_{angle, ijk} (\theta - \theta_{0,ijk})^2 + \\ 
    \sum_{n = 0}^N k_n (1 + \cos (n \phi - \delta) ) + \frac{1}{2} \sum_{ijk} k_{im, ijk} (\theta - \xi_{0,ijk})^2
$$

### Non-Bonded Interactions

The potential part, $V$, is what contains the most interesting information for a computer simulation since it defines all of the interactions of particles with their environment and each other. In general, we can divide up the potential part into a set of contributions from singlets, pairs, triplets, all the way to $N$ body terms such that,

$$
    V(q^f) = \sum_i v_1(\mathbf{q_i}) + \sum_i \sum_{j \neq i} v_2(\mathbf{q_i}, \mathbf{q_j}) + \sum_i \sum_{j \neq i} \sum_{k \neq i,j} v_3(\mathbf{q}_i, \mathbf{q}_j, \mathbf{q}_k) + ...
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

## Tricks of the Trade

### Units

In molecular simulations, we need to use special units because typical values of molecular quantities in SI units are either very big or very small. Let's look at the example of where we calculate the energy of 1000 molecules in an ideal gas at 300$K$. The energy expectation, $\langle E \rangle = \frac{3}{2}Nk_BT \approx 10^{-17}$ joules. If we then proceed to multiply or add numbers at these magnitudes, floating point errors can significantly reduce the accuracy of the calculation. Therefore, we adopt a system of units called "microscopic" units. Some common microscopic units for molecular simulation are listed below.

1. Mass        [=] atomic mass unit (amu)
2. Energy      [=] kcal/mol, kJ/mol, eV
3. Length      [=] \AA, nm
4. Charge      [=] electron charge
5. Temperature [=] Kelvin

All other units can be derived from these base units. For example,

1. Area     [=] Length$^2$
2. Time     [=] Length * Mass$^{1/2}$ * Energy$^{-1/2}$
3. Pressure [=] Energy * Length$^{-3}$
4. Velocity [=] Mass$^{-1/2}$ * Energy$^{1/2}$

It is also common to use so-called reduced units in which the force field parameters themselves are used as units. For example, a Lennard-Jones model of liquid argon has parameters $\sigma = 3.4$ \AA and $\epsilon = 1$ kJ/mol. To model the system in reduced units, we define the length by $\sigma$ and the energy by $\epsilon$ and derive the rest of the units from these. 

1. Time        [=] $\sigma$ * Mass$^{1/2}$ * $\epsilon^{-1/2}$
2. Pressure    [=] $\epsilon$ * Length$^{-3}$
3. Temperature [=] Mass$^{-1/2}$ * $\epsilon^{1/2}$
4. Density     [=] Mass * $\sigma^{-3}$

Of course, reduced units will be different for every system. So if we run simulations at the same reduced units for different systems (Ar and Kr), we should be careful to recognize that these are at completely different thermodynamic states.

### Boundary Conditions

When we run a simulation, our goal is often to describe a system at a much larger scale than is accessible by experiment. How can we achieve this when we are severely limited by the number of atoms that we can simulate? The answer lies in implementing periodic boundary conditions that make the system behave like a bulk fluid without adding too much simulation expense. The idea behind periodic boundary conditions is that we take our original system and surround it by copies of the same system. The atoms in the original system are then made to interact with all atoms in all the copies surrounding the system, thereby eliminating any surface effects in the system and making the system behave more like a bulk fluid. 

To implement periodic boundary conditions, we need a way to account for the possibility that an atom leaves the original box. Practically, we code this so that when a particle leaves the original box, it appears on the other side. As an example, consider a 1D system in which a particle moves along the x-coordinate only within a box from $x_1$ = 0 and $x_2$ = L. The following logic statements guarantee that when a particle passes outside of $x_1$ or $x_2$, it will subsequently appear on the other side of the original box.

1. If $(x<0)$, then $x = x + L$
2. Elseif $(x>L)$, then $x = x - L$

We also need to be aware that by constructing copies around the original system that we may end up overcounting the number of pair interactions in the system. This problem can be directly addressed by ensuring that a particle interacts with only particles that are nearest images of a particle. In other words, if a particle on one end of a box is interacting with a particle on the other side, it will instead interact with its nearest image (which may be right next to our particle) rather than the image thats farther away in the original box. In analogy to our 1D example, we can ensure the interaction with the nearest neighbor by looking at the distances between each particle and assigning a new value to that distance which is at a minimum.

1. $\Delta x = x_2 - x_1$
2. If $\Delta x < -L/2$, $\Delta x = \Delta x + L$
3. Elseif $\Delta x > L/2$, $\Delta x = \Delta x - L$

### Potential Truncation

Let's consider the long range behavior of simple pair potentials. Even in the Lennard-Jones fluid, the potential energy never becomes zero and the force is always positive at large $r$. Therefore, to really implement a Lennard-Jones potential we need a box that is infinitely large or for the system to interact with an infinite number of periodic copies. Of course, this is entirely infeasible and can be corrected by introducing so-called analytical tail corrections. Practically, we define a cutoff functions so that the interactions are only considered over a short range, 

$$
v(r) = 
\begin{cases}
  4\epsilon\bigg[\bigg(\frac{\sigma}{r}\bigg)^{12} - \bigg(\frac{\sigma}{r}\bigg)^{6}\bigg] & \text{if $r < r_{cut}$} \\
  ,0 & \text{otherwise}
\end{cases}
$$

which of course introduces a discontinuity in the potential at $r_{cut}$. This discontinuity can make the energy and pressure calculations incorrect, so we need a way to account for this discontinuity. The way this is usually done is to cut and shift the potential in the following manner. If the potential is less than $r_{cut}$, then add a constant to all values of the potential to shift the potential to zero at $r_cut$. Since the force is related only to the derivative of the potential, this doesn't impact the force, but it does eliminate the discontinuity. So long as $r_{cut}$ is large enough, the truncation effects should then be minimized.

There are a few important considerations with respect to box size when using these analytical tail corrections. First, to preserve the mirror image convention from the previous section we must have $r_{cut} < L/2$. This means that the minimum box size should be $L = 2 r_{cut}$. However, if there are correlations in structure and/or dynamics at longer length scales, as is the case with critical properties and elastic membranes, you need much larger simulation boxes.

### Neighbor Lists

One of the most important considerations for molecular simulations is how computationally expensive they are to run. For instance, if a simulation of 1000 atoms takes 5 hours, how long will a simulation of 10,000 atoms take? The answer is around 500 hours! This is because the simulation time will scale by $N^2$ where $N$ is the number of atoms in the system. This is irregardless of using a potential truncation since we still need to compute the distances between all atom pairs in the system.

We can address this issue by introducing a neighbor list. The first step in constructing a neighborlist is separating the simulation box into smaller cubes with length slightly smaller than $2 r_{cut}$. A neighbor list works by defining a set of atoms within $r_{cut}$ of a given origin plus a spherical shell of radius $r_{cut} + \Delta r$ where $\Delta r$ is some positive number with a usual value of $0.5 \sigma$. The $\Delta r$ is selected so that the particles can evolve within this radius without leaving or entering the larger sphere region within a few timesteps. The force calculation is then only considered over the particles in this neighbor list, reducing the time-complexity to approximately $\mathcal{O}(N)$. Then, if a particle moves beyond $\Delta r$, the list is rebuilt with the $\mathcal{O}(N^2)$ time-complexity.

An implementation of this idea is to break up the system into cubic cells with edge lengths greater than or equal to $r_{cut}$. A sphere of radius $r_{cut} + \Delta r$ is then drawn around the center of each cell and lists of neighbors are formed. The interactions are limited to only partners of atoms within that list, while others are excluded. We simply identify what cell each member of the system is in and compute the force on that particle based on its interactions with members only within the surrounding cells.

## Analyzing Molecular Simulation Trajectories

Recall that the time average or expectation of some dynamical quantity $A$ can be written in the following way,

$$
    \langle A \rangle = \lim_{\tau \to \infty}\frac{1}{\tau} \int^{t + \tau}_t A(q^f, p^f, t) dt
$$

or in terms of the phase space probability density function,

$$
    \langle A \rangle = \int A(q^f, p^f, t) \rho(q^f, p^f, t) d p^f d q^f
$$

### The Ergodic Hypothesis

We will take as a hypothesis that the time average and ensemble average are equal to each other. This is known as the ergodic hypothesis. Of course, we have not (and are not able to) prove this statement. Although we obtain excellent theoretical predictions from statistical mechanics with this hypothesis, fundamentally it is not known whether the ergodic hypothesis is true or not, and, indeed, there are a number of non-ergodic systems that exist in nature. 

### Temperature

Recall from thermodynamics that temperature is defined as the partial derivative of internal energy with respect to entropy,

$$
    T = \bigg(\frac{\partial U}{\partial S}\bigg)_{V,N} 
$$

which isn't immediately useful in the statistical mechanics formalism. However, from the equipartition theorem we know that each quadratic term in the Hamiltonian contributes $\frac{1}{2}k_BT$ to the ensemble average energy,

$$
    \bigg\langle \sum_i^N \frac{1}{2} m_i v_i^2 \bigg\rangle = \frac{3}{2} N k_B T
$$

which can be rearranged to give,

$$
    T = \frac{2}{3 N k_B} \bigg\langle \sum_i^N \frac{1}{2} m_i v_i^2 \bigg\rangle
$$

or at a specific instant in time,

$$
     T_{inst}(t) = \frac{2}{3 N k_B} \sum_i^N \frac{1}{2} m_i v_i^2
$$

This instantaneous temperature should fluctuate in time to conserve the total energy and can be easily measured from a molecular simulation trajectory and/or snapshot. All you need to do is compute the sum of the momenta of every particle and multiple by the leading constants to obtain an estimate of the temperature. 

### Thermostats

Thermostats are implemented in molecular simulations to maintain the temperature average of a system at a fixed value. In a large system at constant temperature, the shear size of the system acts as a heat bath to maintain the temperature of the system. However, it is not immediately obvious how we should enforce this behavior within a small box of simulated particles. A naive approach is to rescale the velocities at each timestep, $v_i = \alpha v_i$, where,

$$
    \alpha = \sqrt{\frac{T}{T_{inst}}}
$$

ensuring that the instantaneous temperature is always equal to the target. However, this method does not reproduce the Maxwell-Boltzmann distribution and therefore is not a physically accurate way to adjust the temperature in a simulation. A better approach involves coupling a friction term to slow down or speed up the particles until the target temperature is reached. We can write Newton's equation of motion for such a system as,

$$
    \mathbf{F_i} - \xi m_i \mathbf{v_i} = m_i \mathbf{a_i}
$$

where the time derivative of the fictitious friction variable $xi$ is given by,

$$
    \frac{\partial \xi}{\partial t} = \frac{1}{Q}\bigg[\sum_i^N \frac{1}{2} m_i v_i^2 - \frac{3N + 1}{2} k_B T\bigg]
$$

where $Q$ is a fictitious 'mass' or 'inertial' term that determines the relaxation time of the system (larger Q means the thermostat will adjust the temperature more slowly) and $T$ is the target temperature. This can be reexpressed as, 

$$
    \frac{\partial \xi}{\partial t} = \frac{1}{Q}\bigg[\frac{3N + 1}{2} k_B (T_{inst} - T)\bigg]
$$

which means that if the instantaneous temperature is larger than the target, the friction increases and if instantaneous temperature is smaller than the target, the friction decreases. This method is easily implemented in the velocity-verlet algorithm by including this friction term (try as an exercise). It is also possible to use diffusion based (Langevin thermostat) and stochastic methods (Anderson thermostat) as thermostats.

### Pressure

Recall that pressure can be written as the negative partial derivative of Helmholtz free energy with respect to volume at constant temperature and number of particles, or equivalently,

$$
    P = -\bigg(\frac{\partial F}{\partial V}\bigg) = k_B T \bigg(\frac{\partial \log Z}{\partial V}\bigg)
$$

We can solve this expression for $P$ (try as an exercise) as,

$$
    P = k_B T \bigg[\frac{N}{V} + \frac{1}{Q_N} \bigg(\frac{\partial Q_N}{\partial V}\bigg)_{T,N}]
$$

where $Q_N$ is the configurational part of the partition function. We can reexpress this equation in terms of the virial defined as,

$$
    \mathcal{V} = - \frac{1}{3} \sum_i^N \mathbf{r_i} \cdot \nabla_i \phi
$$

where $\phi$ is the potential energy. For pairwise additive interactions, the resulting instantaneous pressure is equal to,

$$
    P_{inst} = \frac{N k_B T}{V} + \frac{1}{3V} \sum_{i,j} \mathbf{F_{i,j}} \cdot \mathbf{r_{i,j}}
$$

which can be quickly recognized as the ideal gas pressure plus additional pressure contributions from the interactions. Therefore, attractive interactions result in a decrease in pressure whereas repulsive interactions increase the pressure. Barostats are similar to thermostats but couple to the pressure term and cause re-scaling of the box size to accommodate changes in pressure.

### Structure

First, the local atomic density correlation is formalized by counting the number of atomic neighbors as a function of position with respect to a reference atom and taking the ensemble average,

$$
    g(\mathbf{r}) = \frac{1}{\rho} \bigg \langle \frac{1}{N} \sum_{i=1}^N \sum_{j=1}^N \delta^3(\mathbf{r} - \mathbf{r}_j + \mathbf{r}_i) \bigg \rangle
$$

where $g(\mathbf{r})$ is referred to as the radial distribution function, $\delta^3$ is the three-dimensional Dirac delta function, $\rho$ is the thermodynamic density and $N$ is the total number of particles in the system. The radial distribution function is an important quantity used to describe the average atomic structures of molecular systems. Of course, if there are multiple atom types there will be multiple radial distribution functions for each unique atom pair.

### Structure Factors

We actually can't measure the radial distribution functions experimentally. Instead, methods such as neutron / X-ray scattering are able to measure how particles scatter off of atoms in the system. The resulting diffraction pattern can be analyzed to obtain estimates of the pair correlation functions. For a system containing $N$ distinct atom types, there exist $\frac{N(N+1)}{2}$ unique density pair correlation functions. The density correlation function measured in reciprocal space is known as the partial structure factor, $S_{ij}(Q)$, between unique atom pairs $i$ and $j$. In principle, we cannot determine $S_{ij}(Q)$ experimentally since the diffraction measurement contains all correlation functions in a combined, total structure factor $F(Q)$. However, we can write $F(Q)$ as a weighted sum of the $S_{ij}(Q)$ such that,

$$
    F(Q) = \sum_{i\geq j}^N [2 - \delta_{ij}]b_ib_jc_ic_jS_{ij}(Q)
$$

where $b_i$ and $c_i$ are the coherent scattering lengths and atomic concentration of species $i$, respectively. By applying the coherent scattering lengths the total structure factor is then neutron-weighted. The partial structure factor is related to the radial distribution function via Fourier transform such that,

$$
    S_{ij}(Q) = 4 \pi \rho \int^{\infty}_0 [g_{ij}(r) - 1]\frac{\sin(Qr)}{Qr}r^2 dr
$$

where $\rho$ is the atomic number density of the combined system.
