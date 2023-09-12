---
title: Classical Mechanics
type: book
weight: 20
math: true
tags:
  - classical-mechanics
---

<!--more-->

{{< youtube H0BCYDXEDco >}}

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

which gives the classic expression that the work performed on the system is equal to the change in mechanical energy of the system,

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

## Numerical Time-Evolution of the Equations of Motion

{{< youtube ii-N61PeeQU >}}

Numerically, we will solve Newton's equation of motion iteratively over a series of short timesteps, $\Delta t$. The general strategy looks like this,

1. Given $\mathbf{r}_i(t)$ and $\mathbf{v}_i(t)$, calculate the force on particle $i$, $\mathbf{F}_i(t)$.
2. Integrate equations of motion over a timestep, $\Delta t$, to obtain $\mathbf{r}_i(t + \Delta t)$ and $\mathbf{v}_i(t + \Delta t)$.
3. Calculate new forces, $\mathbf{F}_i(t + \Delta t)$
4. Repeat.

### The Euler Algorithm

Let's think about how we can move between step 1 and 2 in our general strategy. We want the quantity $\mathbf{r}_i(t + \Delta t)$ given an initial position $\mathbf{r}_i(t)$, so we can just express the new position as a Taylor expansion with the old term,

$$
    \mathbf{r}_i(t + \Delta t) = \mathbf{r}_i(t) + \frac{d\mathbf{r}_i}{dt}\bigg|_t \Delta t + \frac{1}{2!} \frac{d^2\mathbf{r}_i}{dt^2}\bigg|_t \Delta t^2 + \mathcal{O}(\Delta t^3)
$$

and recognizing the definition of velocity, acceleration and force in the previous equation gives,

$$
      \mathbf{r}_i(t + \Delta t) = \mathbf{r}_i(t) + \mathbf{v}_i(t) \Delta t + \frac{\Delta t^2}{2m_i} \mathbf{F}_i + \mathcal{O}(\Delta t^3)
$$

where the $\mathcal{O}(\Delta t^3)$ are considered sufficiently small (so long as $\Delta t$ is small). Now, writing a similar Taylor expansion on the velocity we obtain,

$$
      \mathbf{v}_i(t + \Delta t) = \mathbf{v}_i(t) + \frac{\Delta t}{m_i} \mathbf{F}_i + \mathcal{O}(\Delta t^2)
$$

where once again we assume that $\mathcal{O}(\Delta t^2)$ term is small so long as $\Delta t$ is small enough. \newline 

Let's now consider how we could implement this algorithm numerically. We know $\mathbf{r}_i(t)$ and $\mathbf{v}_i(t)$ and calculate $\mathbf{F}_i$ if we have some prescribed force field, $\mathbf{F}_i = - \nabla_i \psi$. We just need to choose a timestep and we can solve directly for both the updated position and velocity. What we will find is that this algorithm doesn't work; in fact, it does not satisfy the conservation of energy (see Problem Set 1, Question 3).

### The Velocity-Verlet Algorithm

We can amend the problem with the Euler algorithm by including an additional term to the velocity so that,

$$
    \mathbf{v}_i(t + \Delta t) = \mathbf{v}_i(t) + \frac{\Delta t}{m_i} \mathbf{F}_i + \frac{\Delta t^2}{2m_i} \frac{d \mathbf{F}_i}{dt} + \mathcal{O}(\Delta t^3)
$$

In general, we don't know the time-derivative of the force, but we can express the force at time $t = t + \Delta t$ by using a Taylor expansion,

$$
     \mathbf{F}_i(t + \Delta t) = \mathbf{F}_i(t) + \frac{d \mathbf{F}_i}{dt}\Delta t + \mathcal{O}(\Delta t^2)
$$

so that,

$$
     \frac{d \mathbf{F}_i}{dt} = \frac{\mathbf{F}_i(t + \Delta t) - \mathbf{F}_i(t)}{\Delta t}
$$

to the first order. Now, we can just substitute this into our velocity equation to obtain,

$$
    \mathbf{v}_i(t + \Delta t) = \mathbf{v}_i(t) + \frac{\Delta t}{m_i} \mathbf{F}_i + \frac{\Delta t}{2m_i} ( \mathbf{F}_i(t + \Delta t) - \mathbf{F}_i(t)) + \mathcal{O}(\Delta t^3)
$$

which is known as the Velocity-Verlet algorithm. One interesting thing to notice here is that we now have a "future" term in our velocity equation, $\mathbf{F}_i(t + \Delta t)$. Do we really need to know the future to solve this algorithm? \newline 

Technically, no. We can solve for the force $\mathbf{F}_i(t + \Delta t)$ by first calculating the force from the updated positions and then calculating the updated velocity. \newline 

The implementation looks like this:

1. Using current the current velocity, calculate the next positions.

$$
        \mathbf{r}_i(t + \Delta t) = \mathbf{r}_i(t) + \mathbf{v}_i(t) \Delta t + \frac{\Delta t^2}{2m_i} \mathbf{F}_i
$$

2. Given $ \mathbf{r}_i(t + \Delta t)$, compute force $\mathbf{F}_i(t + \Delta t)$.

3. Finally, compute new velocities.
   
$$
        \mathbf{v}_i(t + \Delta t) = \mathbf{v}_i(t) + \frac{\Delta t}{m_i} \mathbf{F}_i + \frac{\Delta t}{2m_i} ( \mathbf{F}_i(t + \Delta t) + \mathbf{F}_i(t))
$$

4. Repeat.

The Velocity-Verlet integrator is easy to implement, has excellent numerical stability and long time energy conservation, but does have poor short time energy conservation. Alternative integrators that are equivalent to Velocity-Verlet are the Verlet and leapfrog algorithms.

## The Langrangian, Action and Hamilton's Principle

{{< youtube OpqJjKDPJBA >}}

For convenience, we introduce a quantity known as the Lagrangian, which for generalized coordinates $z, \dot{z}$ is the difference between the kinetic and potential energy,

$$
    L \equiv KE - PE
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

## Conservation Laws Derived from the Lagrangian

{{< youtube HLr5ZeQUrBk >}}

As a mechanical system evolves according to the classical equations of motion, its generalized coordinates and velocities change. However, the values of specific variables may remain constant - these are referred to as constants of motion or conserved quantities. First consider a mechanical system A composed of n-particles. The Lagrangian of this system is given by a function of the form,

$$
    L^A = L(\mathbf{r_1}, ..., \mathbf{r_n}, \mathbf{\dot r_1}, ..., \mathbf{\dot r_n}, t)
$$

Now, let's create an "identical copy" of mechanical system A and translate it to a different point in space. We will give it the name mechanical system B. The only difference between these two states is their position in space, and we assume there exist no interactions between them. The Lagrangian for system B is thus,

$$
    L^B = L(\mathbf{r_1} + \Delta \mathbf{r}, ..., \mathbf{r_n}+\Delta \mathbf{r}, \mathbf{\dot r_1}, ..., \mathbf{\dot r_n}, t)
$$

If the two systems are sufficiently far away that they do not interact with each other, the Lagrangian for each system should be the same. This is known as the homogeneity of space or translational invariance. Translational invariance will occur if there are no external fields, because if $\Delta \mathbf{r}$ moves the system in some position-dependent external fields the Lagrangians may change. Now let's consider what happens if we translate the system by some infinitesimal displacement, $\delta \mathbf{r}$. The difference $L^B - L^A$ can now be expressed as a first-order Taylor expansion such that,

$$
    L^B - L^A = \sum_{i=1}^N\bigg(\frac{\partial L}{\partial \mathbf{r_i}} \cdot \delta \mathbf{r}\bigg) + h.o.
$$

We can rexpress this relation in terms of the momentum $\mathbf{p}_i$ so that, 

$$
     L^B - L^A = \sum_{i=1}^N\bigg(\frac{\partial L}{\partial \mathbf{r_i}} \cdot \delta \mathbf{r}\bigg) = \sum_{i=1}^N\bigg(\frac{d \mathbf{p_i}}{dt} \cdot \delta \mathbf{r}\bigg) = \delta \mathbf{r} \frac{d}{dt}\sum_{i=1}^N \mathbf{p_i}
$$

where we have used the definition of momentum, $\frac{\partial L}{\partial \dot{\mathbf{r}_i}} = \mathbf{p_i}$. If the system is translationally invariant, then the difference $\delta L = L^B - L^A = 0$ for any $\delta \mathbf{r}$, which implies,

$$
    \frac{d}{dt}\sum_{i=1}^N \mathbf{p_i} = 0
$$

Thus, the total sum of the linear momentum of all N particles, defined as the total linear momentum, $\mathbf{P}$, for the system is zero. Therefore, the total linear momentum is a constant of motion. 

Let's now turn our attention to the time dependence of the Lagrangian. The Lagrangian for our hypothetical system of f degrees of freedom has the Lagrangian given by,

$$
    L = L(q_1,...,q_f, \dot q_1,..., \dot q_f,t)
$$

The chain rule tells us that,

$$
    \frac{dL}{dt} = \sum_{i=1}^f\frac{\partial L}{\partial q_i} \dot q_i + \sum_{i=1}^f\frac{\partial L}{\partial \dot q_i} \ddot q_i + \frac{\partial L}{\partial t}
$$

Applying the Lagrange equation of motion, we obtain,

$$
    \frac{dL}{dt} = \sum_{i=1}^f\frac{d}{dt} \bigg(\frac{\partial L}{\partial \dot q_i}\bigg) \dot q_i + \sum_{i=1}^f\frac{\partial L}{\partial \dot q_i} \ddot q_i + \frac{\partial L}{\partial t} = \sum_{i=1}^f \frac{d}{dt} \bigg(\frac{\partial L}{\partial \dot q_i} \dot q_i\bigg) + \frac{\partial L}{\partial t}
$$

In which we find that,

$$
    \frac{d}{dt}\bigg(\frac{\partial L}{\partial \dot q_i} \dot q_i - L\bigg) = -\frac{\partial L}{\partial t}
$$

By the definition for energy given before, this means that,

$$
    \frac{dh}{dt} = -\frac{\partial L}{\partial t}
$$

Now we may ask what would happen if we solve the Lagrangian today ($t_A$) and tomorrow ($t_B$). The results of this computation should not change, so we accept that this system obeys homogeneity of time. But this means that $\frac{\partial L}{\partial t}$ is identically zero. Therefore, energy is a conserved quantity.

## Hamilton's Equations of Motion

{{< youtube 61CWqyocuOM >}} 

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
    p_i = \frac{\partial L}{\partial \dot{q_i}} \bigg| = \frac{L - H}{\dot{q_i} - 0}
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
