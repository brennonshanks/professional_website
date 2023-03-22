---
title: Classical Mechanics
type: book
weight: 20
math: true
tags:
  - classical_mechanics
---

<!--more-->

## Newton's Equation of Motion

First consider an inertial frame of reference, which is a reference environment for a mechanical system such that when a material point or particle is subject to no net force, the velocity of the particle is unchanged. In such a reference frame, particles follow Newton's equation of motion,

$$
    \mathbf{F} = m\frac{d^2 \mathbf{r}}{dt^2}
$$

where $\mathbf{F}$ is the force, $m$ is the object's mass, and $\mathbf{r}$ is the object's position. This relation suggests that if the mechanical state of the system ($\mathbf{r}, \mathbf{v} \equiv \frac{d\mathbf{r}}{dt}$) is known at some initial time (t = 0), then the mechanical state of the system at arbitrary t is completely determined. The integral of the force over a path is called work, 

$$
    W = \int \mathbf{F} \cdot d\mathbf{r}
$$

which for a closed path is expressed as,

$$
    W = \oint \mathbf{F_C} \cdot d\mathbf{r}
$$

where the symbol $\oint$ indicates that the path is closed. If this integral is zero, then the force $\mathbf{F_C}$ is called conservative. Conservative forces do not depend on the path that the particle takes; rather, they depend only on the initial and final points of the trajectory. We call work that only depends on the position of a particle with respect to some external potential the work done by the potential energy,

$$
    W_{A \rightarrow B} = \psi (\mathbf{r_A},\mathbf{r_B}) 
$$

in which $\psi$ is the potential energy of the particle at position $\mathbf{r_B}$ with respect to $\mathbf{r_A}$. Now, lets integrate the expression for an arbitrary force given by Newton's equation of motion and compute the work over a velocity change,

$$
    W = \int m\frac{d^2 \mathbf{r}}{dt^2} \cdot d\mathbf{r}
$$

By noting that the position vector is also a function of time, we can rewrite $d\mathbf{r}$ such that,

$$
    W = \int m\frac{d^2 \mathbf{r}}{dt^2} \cdot \frac{d\mathbf{r}}{dt}dt = \frac{1}{2}m[\mathbf{v}\cdot\mathbf{v}]_{t_1}^{t_2} =\frac{1}{2}m[v_2^2 - v_1^2]
$$

and we call this work due to the motion of the particle the work from the kinetic energy, $mv^2/2$. Now, let's consider the movement of a particle in a conservative force field, $\psi(\mathbf{r})$, subject to some external force $\mathbf{F_{ext}}$, 

$$
    \mathbf{F_{ext}} -\nabla \psi(\mathbf{r}) = m\frac{d^2 \mathbf{r}}{dt^2} 
$$

Integrating over the external force gives the work done on the system by the force,

$$
    W = \int \mathbf{F_{ext}} \cdot d\mathbf{r} = \int \left[\nabla \psi(\mathbf{r}) + m\frac{d^2 \mathbf{r}}{dt^2}\right]\cdot d\mathbf{r}
$$

which gives the classic expression that the work performed by the system on a particle is equal to the change in mechanical energy of the particle,

$$
    W = \Delta PE + \Delta KE = \Delta E
$$

Thus, under no external force ($\mathbf{F_{ext}} = \mathbf{0}$), the mechanical energy (E) of a particle does not change with time. Such a quantity is a constant of motion.

  Of course, in the statistical theory of liquids we need to extend Newton's equations of motion to systems of many particles. The result is a system of equations describing the positions and velocities of each particle,

$$
    \mathbf{F_i} = m_i\frac{d^2 \mathbf{r_i}}{dt^2}
$$

where $i = 1,...,N$ and $N$ is the total number of particles in the system. The mechanical energy of a many-particle system is more complex since in general there are interactions between particles that are not accounted for by the kinetic or external field potential energy terms used previously. Assume that these interactions are given by a conservative force, $\phi$. Then similarly to a single particle system, applying Newton's equation of motion to the many body system gives,

$$
    E = \sum_{i=1}^N \left[\frac{1}{2}m_iv_i^2+\psi(\mathbf{r_i})\right] + \phi (\mathbf{r_1}, ..., \mathbf{r_N})
$$

where the total energy $E$ is now the sum of the kinetic and potential energies of all particles plus the configuration dependent potential energy of the particle-particle interactions, $\phi (\mathbf{r_1}, ..., \mathbf{r_N})$. For a system of many particles, the terms in the total energy are dependent on both the particle velocities ($\mathbf{v_i}$) and positions ($\mathbf{r_i}$) of every particle in the system. Since velocity and position are both three-dimensional, each particle contributes 6-dimensions to the many particle system. In total, the many particle system can therefore be described by a $6N$-dimensional phase space of $3N$-dimensions in velocity and $3N$-dimensions in position. 

## Langrange and Hamilton Equation of Motion

For convenience, we introduce a quantity known as the Lagrangian, which for generalized coordinates $z, \dot{z}$ is the difference between the kinetic and potential energy,

$$
    L \equiv \frac{1}{2}m\dot z^2  - mgz
$$

whose time integral is defined as the action,

$$
    \mathcal{L}[z] \equiv \int_{t_1}^{t_2} L(\dot z, z) dt
$$

A useful relation between the actions of a particle following two different paths is known as Hamilton's principle, which states that the difference between the actions of a particle taking two different paths with the same start and end points is zero in the first order terms,

$$
    \mathcal{L}[z+\delta z] - \mathcal{L}[z] = 0
$$

where $z + \delta z$ indicates that the particle in the first term follows a perturbed path from $z$ but still starts and ends in the same place.

Let's expand the relation given by Hamilton's principle in terms of the notation of the Lagrangian,

$$
    \mathcal{L}[z+\delta z] - \mathcal{L}[z] = \int_{t_1}^{t_2}\left[L(z + \delta z, \dot z + \dot \delta z) - L(z,\dot z) \right]dt = 0
$$

Applying a Taylor expansion in the first order to the integrand gives,

$$
    \int_{t_1}^{t_2}\left[L(z + \delta z, \dot z + \dot \delta z) - L(z,\dot z) \right]dt = \int_{t_1}^{t_2}\left[\frac{\partial L}{\partial z}\delta z + \frac{\partial L}{\partial \dot z}\dot{\delta z}\right]dt + \text{h.o.} = 0
$$

where h.o. refers to "higher-order" terms. Then, integrating by parts on the second term and recognizing that the surface term must vanish according to Hamilton's principle we obtain,

$$
     \mathcal{L}[z+\delta z] - \mathcal{L}[z] = \delta \mathcal{L} = \int_{t_1}^{t_2}\left[\frac{\partial L}{\partial z} - \frac{d}{dt} \bigg( \frac{\partial L}{\partial \dot z}\bigg)\right] \delta z dt = 0  
$$

which can be evaluated to give the Lagrange equation of motion,

$$
    \frac{d}{dt}\bigg(\frac{\partial L}{\partial \dot z}\bigg) - \frac{\partial L}{\partial z} = 0
$$

The Lagrange equation of motion is an expression of the relationships between the generalized position coordinates, $z$, and the generalized velocity coordinates, $\dot{z}$. However, suppose instead that we wanted to express the time-evolution of the classical system in terms of the momenta, $p_i$, which expressed through the Lagrangian is,

$$
    p_i = \frac{\partial L}{\partial \dot{z}}
$$

First, let's consider the Lagrangian for a system with an arbitrary number of generalized coordinates, $f$, so that,

$$
    L[q_1,...,q_f, \dot{q_1}, ..., \dot{q_f}]
$$

is a function of $2f$ independent variables; namely, $f$ generalized position coordinates and $f$ generalized velocity coordinates. We are looking for a new function that depends on the generalized momenta, $p_i$, rather than the generalized velocities,

$$
    H[q_1,...,q_f, p_1, ..., p_f]
$$

that can recover the Lagrangian for the classical time evolution of the system. One way to construct this function is to consider that the momentum corresponding to a specific generalized velocity, $\dot{q_i}$, is just the derivative of the Lagrangian with respect to $\dot{q_i}$, or equivalently the slope of the tangent line to the Lagrangian at $\dot{q_i}$. If we visualize the Lagrangian as a function of $\dot{q_i}$, then the tangent lines along this function will intersect the y-axis ($\dot{q_i} = 0$) as a function of the value of $p_i$. Therefore, we anticipate that our new function $H$ is determined when these tangent lines intersect the y-axis, occurring precisely when,

$$
    p_i = \frac{\partial L}{\partial \dot{q_i}} \bigg|_{\dot{q_i}} = \frac{L - H}{\dot{q_i} - 0}
$$

leading to the following relation,

$$
    H = L - p_i \dot{q_i}
$$

where $-H = \mathcal{H}$ is known as the Hamiltonian for particle $i$. Generalizing to $f$ particles, the Hamiltonian can be expressed as,

$$
    \mathcal{H} = \sum_{i=1}^f p_i \dot{q_i} - L
$$

This transformation is known as a Legendre transformation and it will appear in thermodynamics with respect to transformation of thermodynamic variables.

We can now derive equations of motion from the Hamiltonian by considering the total derivative,

$$
    d\mathcal{H} = \sum^f_{i = 1} (p_i d \dot{q_i} + \dot{q_i} d p_i) - dL
$$

but $dL$ is equal to,

$$
    \sum^f_{i = 1} (\dot{p_i} d q_i + p_i d \dot{q_i}) + \frac{\partial L}{\partial t}dt
$$

which after substituting into the expression for $d \mathcal{H}$ gives,

$$
    d\mathcal{H} = \sum^f_{i = 1} (- \dot{p_i} d q_i + \dot{q_i} d p_i) - \frac{\partial L}{\partial t}dt
$$

Since $\mathcal{H} = \mathcal{H}[H[q_1,...,q_f, p_1, ..., p_f]]$, its total derivative is also given by,

$$
    d\mathcal{H} = \sum^f_{i = 1} \bigg(\frac{\partial H}{\partial p_i} d p_i + \frac{\partial H}{\partial q_i} d q_i\bigg) + \frac{\partial H}{\partial t}dt
$$

so that,
   
$$
    \frac{\partial H}{\partial p_i} = \dot{q_i}
$$

$$
    \frac{\partial H}{\partial q_i} = - \dot{p_i}
$$

$$
    \frac{\partial H}{\partial t} = - \frac{\partial L}{\partial t}
$$

which are known as Hamilton's equations of motion.

References
1. Kusaka, I. Statistical Mechanics for Engineers. (Springer International Publishing, 2015). doi:10.1007/978-3-319-13809-1.

## Problem Set 1
1. Show that the Lagrangian reduces to Newton’s equation of motion for a particle in a uniform gravitational field. (Hint) First, write the correct form of the Lagrangian and then use the following definition for the Langrange equation of motion, 

$$
  \frac{d}{dt}\bigg(\frac{\partial L}{\partial \dot{z}}\bigg) - \frac{\partial L}{\partial z} = 0
$$

2. Find the conjugate momenta ($p_r, p_\theta$) and write the Hamiltonian for a system with the following Lagrangian,

$$
  L = m(\dot{r}^2 + r^2\theta^2)/2 - V(r)
$$

3. In molecular modeling, the Hamilton equations of motion are solved numerically given some Hamiltonian. While we will go into detail on the specifics of these Hamiltonians later in the course, for now just identify the kinetic and potential parts of the following molecular Hamiltonian ($K$ is a spring constant and $r_{ij}$ is the distance between atoms $i$ and $j$).

$$
  H = \sum_{particles} \frac{p_i^2}{2m_i} + \sum_{bonds} K_b (b - b_0)^2 + \sum_{non-bonded} \frac{q_i q_j}{r_{ij}} + \sum_{non-bonded} v(r_{ij})
$$

4. Consider the following physical system in which masses $M, m_1$, and $m_2$ move at the speeds and directions indicated in the figure below. Solve for the acceleration of $M$ and $m_2$. (Hint) Use the Lagrange equation of motion on both the coordinate $x$ and $y$ and solve the system of equations for $\ddot{x}$ and $\ddot{y}$.

![screen reader text](pulley.png)

## Problem Set 2

1. Two masses $m_1$ and $m_2$ are oscillating attached by a spring with spring constant $k$. Determine the frequency of oscillation of the two masses $\omega$ using the Lagrangian of the system assuming there no external forces in the system.

2.

3. The dispersion energy in molecular systems is often modeled by the Lennard-Jones potential, which gives the potential energy of two particles separated by a distance $r_{ij} = |\mathbf{r_i} - \mathbf{r_j}|$. Using Python, plot the Lennard-Jones potential and Lennard-Jones force (on separate plots) for a system with $\sigma = 1$, $\epsilon = 1$ for $0.9 \leq r \leq 4$. At what $r$ is the force zero? If two particles with a Lennard-Jones potential interaction are closer together than the radius of zero force, will they attract or repel each other (think about what the sign of the force means)?

$$
  v(r_{ij}) = 4 \epsilon \bigg[ \bigg(\frac{\sigma}{r_{ij}}\bigg)^{12} - \bigg(\frac{\sigma}{r_{ij}}\bigg)^6 \bigg]
$$

4. Consider the infinite Atwood’s machine. All the masses are equal to $m$, and all the pulleys and strings are massless. The masses are held fixed and then simultaneously released. What is the acceleration of the top mass?

![screen reader text](infatwood.png)
