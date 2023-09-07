---
title: Thermodynamics
type: book
weight: 30
math: true
---

<!--more-->

An agglomerate of matter consists of an enormous amount of atoms. A single glass of water contains somewhere between $10^{24}$ and $10^{25}$ atoms alone! From a classical mechanics point of view, modeling the glass of water would require solving momentum equations for all $10^{25}$ atoms simultaneously. Clearly, this is beyond even the most powerful supercomputers that exist today. So, the question becomes, how can we study systems composed of an inconceivable number of particles without appealing to classical mechanics?

The characteristic time period of an atomic motion is on the order of $10^{-15}$ seconds. Therefore, even during a measurement of a system that is captured in a single microsecond, the atoms of a typical solid still go through ten million vibrations. This implies that a macroscopic measurement senses only averages of the atomic coordinates. A map of how the atomic coordinates change is known as a normal mode. A normal mode is a coupled motion of atomic coordinates that include divergence (increase in particle density), convergence (decrease in particle density), and vibration. Some normal modes can be seen macroscopically, such as a change in volume or electric dipole. Others, like atomic vibrations, cannot be seen and are therefore "lost" in macroscopic observation. Classical Thermodynamics is concerned with normal modes that are observable on a macroscopic scale.

By taking this macroscopic view, we lose a sense of how the motions of atomic coordinates can transfer energy. In Thermodynamics, we refer to this "invisible" mode of energy transfer as heat. From the Classical Mechanics perspective, heat is non-existent, since the energy of the system is completely characterized by generalized momentum and position for each particle. From this perspective, conservation of energy of a closed system requires that the change in energy be directly equal to the classical mechanical work done on the system, W'.

$$
    \Delta E = W'
$$

To accommodate the fact that we cannot observe all forms of energy transfer macroscopically (what we will call work), we must split the W' into observable energy transfer, W, and unobservable energy transfer, Q (heat). This gives us the first law of thermodynamics. 

$$
    \Delta E = W + Q
$$

Now, in thermodynamics we are not typically concerned with the motion of a system in space or its change in position with respect to an external field, so we can simplify our energy conservation equation to simply include the internal energy, U.

$$
    \Delta U = W + Q
$$

W and Q are path functions, meaning that they depend on the exact way that changes are brought about by them. W is a path function because, in defining it, we have lost track of microscopic displacements, whereas classical mechanical work W' is a path-independent function. An infinitesimal view of this equation is shown below.

$$
    dU = d_{inc} W + d_{inc} Q
$$

were $d_{inc}$ represents an "incomplete" differential of the quantity.

## Equilibrium Thermodynamics

Thermodynamics is concerned with both reversible and irreversible processes, but for now let us consider equilibrium thermodynamics. An equilibrium state is a state of the system that, given a certain set of internal parameters U, V, and $N_i$ (i = 1, ..., n), the system tends to evolve towards. This leads us to the first postulate.

Postulate 1. There exist particular states, called equilibrium states, that are completely characterized by U, V, $N_i$ (i = 1, ..., n).

A system at macroscopic equilibrium is a system where all representative atomic states of the system exist in the time scale of a macroscopic measurement.

Postulate 2. There exists a function, S, such that, S = S(U,V,N). Furthermore, the extensive parameters take values so that this function is maximized over the manifold of constrained equilibrium states.

This postulate applies only to equilibrium states. The following two postulates apply to properties of S.

Postulate 3. S is additive over subsequent subsystems. Furthermore, S is a continuous, differentiable, and a monotonically increasing function of energy.

There are immediate consequences of this postulate which are listed below.

$$
    S = \sum_{\alpha}S^{(\alpha)}
$$

Corollary 1: The entropy of a simple system is a homogeneous, first-order function of the extensive parameters.

$$
    S(\lambda U, \lambda V, \lambda N) = \lambda S(U, V, N)
$$

Corollary 2: The monotonic property implies that temperature is non-negative. In other words, 

$$
    \left(\frac{\partial S}{\partial U}\right)_{V,N} > 0
$$

Corollary 3: Entropy can be inverted with respect to energy because it is a single-valued, continuous, and differentiable function with respect to S, V, N.

Postulate 4: The entropy of any system vanishes in the state when T = 0.

Entropy can change as a result of internal or external processes. We express the differential change in entropy as, 

$$
    dS = d_{inc}{S_e} + d_{inc}{S_i}
$$

We now accept that the expression for $d_{inc}{S_e}$ is given by,

$$
d_{inc}{S_e} = \frac{d_{inc}{Q}}{T} 
$$

On the other hand, an important consequence of of the second law is that, 

$$
d{S_i} \geq 0 
$$

Equality holds in the previous equation when the thermodynamic process is reversible. A reversible process is such that the sequence of states visited by the system can be traversed in the opposite direction by an infinitesimal change in the boundary conditions. According to the second law, processes resulting in a decrease of the entropy are impossible for an isolated system. In terms of statistical mechanics, this is not actually the case (as will be seen later).

Consequences of these postulates include: the fundamental equation, equations of state, the Euler relation, Gibbs-Duhem relation, Maxwell relations, and free energies. Notes on these will be provided in the lectures.

## Problem Set

1. A pure gas is well described by the fundamental equation,

$$
  S = aN + NR\log{}\frac{U^{3/2}V}{N^{5/2}}
$$

a.  Find the equation of state of the gas of the form $P = P(T, V, N)$.

b. Show that $U = \frac{3}{2}PV$.

c. Show that $PV^{5/3} = c$ where $c$ is a constant.

2. The fundamental equation of a pure system is given by,

$$
  S = a(UVN)^b
$$

where $a$ is a positive constant. The system is held at 0.3 MPa.

a. What is $b$?

b. Find $U/V$.

c. Find $\mu$ in J/mol when $N/V = 0.1$ $(mol/cm^3)$ 

3. Consider an isolated system separated into two compartments by a rigid, diathermal wall impermeable to all species and fixed by stops. Show that when the stops are removed and the wall is allowed to move that it moves towards the low pressure compartment from the high pressure compartment. Assume that the temperature is equal during the process.

4. Compute the coefficient of expansion $\alpha$ and the isothermal compressibility $\kappa_{T}$ in terms of $P$ and $V$ for a system that obeys the Van der Waals equation of state,

$$
  P = \frac{NRT}{V-bn} - \frac{N^2a}{V^2}
$$

5. For an $n$-component system, how many Maxwell relations are there?

6. Using the Gibbs-phase rule, determine if it is possible to independently vary temperature and pressure in a system containing a solid and saturated solution of that solid.
