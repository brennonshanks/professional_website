---
title: Thermodynamics
type: book
weight: 30
math: true
---

<!--more-->

## Introduction to Classical Thermodynamics

{{< youtube Ig1JXPcgv80 >}}

An agglomerate of matter consists of an enormous amount of atoms. A single glass of water contains somewhere between $10^{24}$ and $10^{25}$ atoms alone! From a classical mechanics point of view, modeling the glass of water would require solving momentum equations for all $10^{25}$ atoms simultaneously. Clearly, this is beyond even the most powerful supercomputers that exist today. So, the question becomes, how can we study systems composed of an inconceivable number of particles without appealing to classical mechanics? 

The characteristic time period of an atomic motion is on the order of $10^{-15}$ seconds. Therefore, even during a measurement of a system that is captured in a single microsecond, the atoms of a typical solid still go through ten million vibrations. This implies that a macroscopic measurement senses only averages of the atomic coordinates. 

A map of how the atomic coordinates change is known as a normal mode. A normal mode is a coupled motion of atomic coordinates that include divergence (increase in particle density), convergence (decrease in particle density), and vibration. Some normal modes can be seen macroscopically, such as a change in volume or electric dipole. Others, like atomic vibrations, cannot be seen and are therefore "lost" in macroscopic observation. Classical thermodynamics is concerned with normal modes that are observable on a macroscopic scale.

By taking this macroscopic view, we lose a sense of how the motions of atomic coordinates can transfer energy. In Thermodynamics, we refer to this "invisible" mode of energy transfer as \textbf{heat}. From the Classical Mechanics perspective, heat is non-existent, since the energy of the system is completely characterized by generalized momentum and position for each particle. From this perspective, conservation of energy of a closed system requires that the change in energy be directly equal to the classical mechanical work done on the system, W'.

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
    dU = \dbar W + \dbar Q
$$

where $\dbar$ indicates an imperfect differential. The differential is imperfect since W and Q are path-dependent functions.

### What is $\dbar W$?

Consider a system with a force exerted on its boundary through a surface element dA, resulting in a linear displacement d$\mathbf{l}$. The entire system experiences differential work, $\dbar{W}$, given by

$$
   \dbar{W} = d\mathbf{l}\cdot \mathbf{t}dS
$$

Expressing the stress vector in terms of the stress tensor and noting that for an infinitely slow moving boundary the extra stress tensor $\mathbf{T_v}$ is approximately 0, we obtain, 

$$
   W = -P\int_{S}d\mathbf{l}\cdot \mathbf{n}dS = -P\int_{V}dV
$$

which is just $W = - P dV$

## Thermodynamic Postulates

Thermodynamics is concerned with both reversible and irreversible processes, but for now let us consider equilibrium thermodynamics. An equilibrium state is a state of the system that, given a certain set of internal parameters U, V, and $N_i$ (i = 1, ..., n), the system tends to evolve towards. This leads us to the first postulate.

Postulate 1: There exist particular states, called equilibrium states, that are completely characterized by U, V, $N_i$ (i = 1, ..., n).

Note that in more complex systems, we require an inclusion of elastic strain parameters and electric dipole moment (also macroscopically measurable properties). A system at macroscopic equilibrium is a system where all representative atomic states of the system exist in the time scale of a macroscopic measurement.

Postulate 2: There exists a function, S, such that, S = S(U,V,N). Furthermore, the extensive parameters take values so that this function is maximized over the manifold of constrained equilibrium states.

This postulate applies only to equilibrium states, but in general not to non-equilibrium states. Essentially, we are postulating the existence of some function, called the entropy, that is maximized at equilibrium with respect to all of its dependent variables. The following two postulates apply to properties of the entropy and they are shown below.

Postulate 3: Entropy is additive over subsequent subsystems. Furthermore, S is a continuous, differentiable, and a monotonically increasing function of energy.

There are immediate consequences of this postulate which are listed below.

Corollary 1: 

$$
S = \sum_{\alpha}S^{(\alpha)}
$$

Corollary 2: The entropy of a simple system is a homogeneous, first-order function of the extensive parameters.

$$
S(\lambda U, \lambda V, \lambda N) = \lambda S(U, V, N)
$$

Corollary 3: The monotonic property implies that temperature is non-negative. In other words, 

$$
\left(\frac{\partial S}{\partial U}\right )_{V,N} > 0
$$

Corollary 4: Entropy can be inverted with respect to energy because it is a single-valued, continuous, and differentiable function with respect to S, V, N.

Postulate 4: The entropy of any system vanishes in the state when T = 0.

## Fundamental Relations and Equations of State

{{< youtube Krwwis0z7U0 >}}

To this point we have discussed entropy as a function on internal energy, volume, and the number of moles of each chemical species. We know that based on the properties of this function that we can solve for internal energy directly and it will be a function of entropy, volume, and the number of moles of each chemical species. Thus,

$$
U = \left[U(S, V, N_i) :  i = (1, ..., n)\right]
$$

To examine infinitesimal changes in the energy, we compute the first differential of U to obtain,

$$
dU = \left(\frac{\partial U}{\partial S}\right )dS + \left(\frac{\partial U}{\partial V}\right )dV + \sum_{i}\left(\frac{\partial U}{\partial N_i}\right )dN_i
$$

The previous partial derivatives are called intensive parameters, and are given the following definitions.

$$
    \left(\frac{\partial U}{\partial S}\right )_{V,N} \equiv T
$$

$$
 \left(\frac{\partial U}{\partial V}\right )_{S,N} \equiv -P 
$$

$$
 \left(\frac{\partial U}{\partial N_i}\right )_{S,V} \equiv \mu_i
$$

With these definitions, the first differential dU can be expressed as, 

$$
dU = TdS - PdV + \sum_{i}\mu_i dN_i
$$

It should now be clear that $\dbar{Q} = TdS$, $\dbar{W_m} = - PdV$ (as shown previously), and that we have an additional work term known as the quasi-static chemical work, $\dbar{W_c} = \sum_{i}\mu_i dN_i$. We should note, however, that this does not hold for irreversible processes since these are path-dependent functions.

### Equations of State

The intensive parameters defined previously are functions of S,V,N since they are partial derivatives of a function of those variables. Therefore, 

$$
    T = T(S,V,N_i)
$$

$$
    P = P(S,V,N_i) 
$$

$$
    \mu_i = \mu_i(S,V,N_i)
$$

These relationships that express intensive parameters in terms of the extensive parameters, are known as equations of state. In addition, since the fundamental relation is homogeneous first order, equations of state are homogeneous zero order. In other words,

$$
    T(\lambda S, \lambda V, \lambda N_i) = T(S,V,N_i)
$$

Physically, we can interpret this as the temperature of two subsystems of a composite system is not additive. In fact, at equilibrium, any number of subsystems chosen from a composite system will have the same temperature as the composite system as a whole.

### The Euler Form

Recall the first order homogeneous property of the fundamental relation.

$$
U(\lambda S, \lambda V, \lambda N) = \lambda U(S, V, N)
$$

Differentiating with respect to $\lambda$, we find, 

$$
    U = \left(\frac{\partial U}{\partial (\lambda S)}\right ) \frac{\partial (\lambda S)}{\partial \lambda} + \left(\frac{\partial U}{\partial (\lambda V)}\right ) \frac{\partial (\lambda V)}{\partial \lambda} + \sum_{i}\left(\frac{\partial U}{\partial (\lambda N_i)}\right ) \frac{\partial (\lambda N_i)}{\partial \lambda}
$$

This is true for any value of $\lambda$. Simplifying this expression and taking $\lambda = 1$,

$$
    U = TS - PV  + \sum_{i}\mu_iN_i
$$

### The Gibbs-Duhem Relation

Taking the Euler form of the fundamental relation and taking an infinitesimal variation gives,

$$
    dU = TdS + SdT - PdV - VdP + \sum_{i}\mu_idN_i + \sum_{i}N_id\mu_i
$$

However, we know that the proper form of the equation from the fundamental relation is, 

$$
    dU = TdS - PdV + \sum_{i}\mu_idN_i 
$$

We then take the difference between these two relations to obtain the Gibbs-Duhem Relation,

$$
    0 = SdT - VdP + \sum_{i}N_id\mu_i
$$

This relation demonstrates the intensive parameters (T, P, and $\mu$), cannot be varied independently. In addition, this relation shows that in a system of n components, n + 1 intensive parameters can be varied independently. This is referred to as the thermodynamic degrees of freedom of the system.

### Gibbs Phase Rule

The interface between coexisting phases may be regarded as a partition that is diathermal, movable, and permeable to all species. Thus, at equilibrium, there must be a consistency in temperature, pressure, and chemical potential across all M phases.

$$
    T_1 = T_2 = ... = T_M
$$

$$
    P_1 = P_2 = ... = P_M
$$

$$
    \mu_1 = \mu_2 = ... = \mu_M
$$

If we perturb the state of the system by increasing the temperature by some $dT$, then in order to preserve the M phases, each phase parameter must be preserved after this change as well.

$$
    T_1 + dT_1 = T_2+ dT_2 = ... = T_M+ dT_M
$$

$$
    P_1 + dP_1 = P_2 + dP_2 = ... = P_M + dP_M
$$

$$
    \mu_1 + d\mu_1 = \mu_2 + d\mu_2 = ... = \mu_M + d\mu_M
$$

Thus we find that, 

$$
    dT_1 = dT_2 = ... = dT_M
$$

$$
   dP_1 = dP_2 = ... = dP_M
$$

$$
     d\mu_1 =  d\mu_2 = ... = d\mu_M
$$

Now, these relationships must be consistent with the Gibbs-Duhem relation, namely, 

$$
    0 = SdT - VdP + \sum_{i}^{n}N_id\mu_i
$$

If we hold pressure constant and vary only temperature, we find that, 

$$
    0 = S^{(j)}dT + \sum_{i}^{n}N^{(j)}_id\mu_i
$$

for all phases $1,...,M$. But this requires that $dT$ and $d\mu_i$ are zero. That is, if we want to perturb the state of the system while maintaining the phase coexistence, we cannot possibly hold P constant. We now have (n + 2) infinitesimal quantities with M equations. Therefore, to ensure the system has solutions, we can only specify (n + 2 - M) of those variables independently. This is known as the Gibbs phase rule.

References
1. Kusaka, I. Statistical Mechanics for Engineers. (Springer International Publishing, 2015). doi:10.1007/978-3-319-13809-1.
2. Callen, H, Thermodynamics and an Introduction to Thermostatistics (Wiley, 1985). ISBN: 978-0-471-86256-7.

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
