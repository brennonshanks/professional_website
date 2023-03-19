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

\begin{equation}
    \mathbf{F} = m\frac{d^2 \mathbf{r}}{dt^2}
\end{equation}

where $\mathbf{F}$ is the force, $m$ is the object's mass, and $\mathbf{r}$ is the object's position. This relation suggests that if the mechanical state of the system ($\mathbf{r}, \mathbf{v} \equiv \frac{d\mathbf{r}}{dt}$) is known at some initial time (t = 0), then the mechanical state of the system at arbitrary t is completely determined. The integral of the force over a path is called work, 

\begin{equation}
    W = \int \mathbf{F} \cdot d\mathbf{r}
\end{equation}

which for a closed path is expressed as,

\begin{equation}
    W = \oint \mathbf{F_C} \cdot d\mathbf{r}
\end{equation}

where the symbol $\oint$ indicates that the path is closed. If this integral is zero, then the force $\mathbf{F_C}$ is called conservative. Conservative forces do not depend on the path that the particle takes; rather, they depend only on the initial and final points of the trajectory. We call work that only depends on the position of a particle with respect to some external potential the work done by the potential energy,

\begin{equation}
    W_{A \rightarrow B} = \psi (\mathbf{r_A},\mathbf{r_B}) 
\end{equation}

in which $\psi$ is the potential energy of the particle at position $\mathbf{r_B}$ with respect to $\mathbf{r_A}$. Now, lets integrate the expression for an arbitrary force given by Newton's equation of motion and compute the work over a velocity change,

\begin{equation}
    W = \int m\frac{d^2 \mathbf{r}}{dt^2} \cdot d\mathbf{r}
\end{equation}

By noting that the position vector is also a function of time, we can rewrite $d\mathbf{r}$ such that,

\begin{equation}
    W = \int m\frac{d^2 \mathbf{r}}{dt^2} \cdot \frac{d\mathbf{r}}{dt}dt = \frac{1}{2}m[\mathbf{v}\cdot\mathbf{v}]_{t_1}^{t_2} =\frac{1}{2}m[v_2^2 - v_1^2]
\end{equation}

and we call this work due to the motion of the particle the work from the kinetic energy, $mv^2/2$. Now, let's consider the movement of a particle in a conservative force field, $\psi(\mathbf{r})$, subject to some external force $\mathbf{F_{ext}}$, 

\begin{equation}
    \mathbf{F_{ext}} -\nabla \psi(\mathbf{r}) = m\frac{d^2 \mathbf{r}}{dt^2} 
\end{equation}

Integrating over the external force gives the work done on the system by the force,

\begin{equation}
    W = \int \mathbf{F_{ext}} \cdot d\mathbf{r} = \int \left[\nabla \psi(\mathbf{r}) + m\frac{d^2 \mathbf{r}}{dt^2}\right]\cdot d\mathbf{r}
\end{equation}

which gives the classic expression that the work performed by the system on a particle is equal to the change in mechanical energy of the particle,

\begin{equation}
    W = \Delta PE + \Delta KE = \Delta E
\end{equation}

Thus, under no external force ($\mathbf{F_{ext}} = \mathbf{0}$), the mechanical energy (E) of a particle does not change with time. Such a quantity is a constant of motion.

  Of course, in the statistical theory of liquids we need to extend Newton's equations of motion to systems of many particles. The result is a system of equations describing the positions and velocities of each particle,

\begin{equation}
    \mathbf{F_i} = m_i\frac{d^2 \mathbf{r_i}}{dt^2}
\end{equation}

where $i = 1,...,N$ and $N$ is the total number of particles in the system. The mechanical energy of a many-particle system is more complex since in general there are interactions between particles that are not accounted for by the kinetic or external field potential energy terms used previously. Assume that these interactions are given by a conservative force, $\phi$. Then similarly to a single particle system, applying Newton's equation of motion to the many body system gives,

\begin{equation}
    E = \sum_{i=1}^N \left[\frac{1}{2}m_iv_i^2+\psi(\mathbf{r_i})\right] + \phi (\mathbf{r_1}, ..., \mathbf{r_N})
\end{equation}

where the total energy $E$ is now the sum of the kinetic and potential energies of all particles plus the configuration dependent potential energy of the particle-particle interactions, $\phi (\mathbf{r_1}, ..., \mathbf{r_N})$. For a system of many particles, the terms in the total energy are dependent on both the particle velocities ($\mathbf{v_i}$) and positions ($\mathbf{r_i}$) of every particle in the system. Since velocity and position are both three-dimensional, each particle contributes 6-dimensions to the many particle system. In total, the many particle system can therefore be described by a $6N$-dimensional phase space of $3N$-dimensions in velocity and $3N$-dimensions in position. 

## Langrange and Hamilton Equation of Motion

## Problem Set 1
1. 

2. Show that the Lagrangian reduces to Newton’s equation of motion for a particle in a uniform gravitational field. (Hint) First, write the correct form of the Lagrangian and then use the following definition for the Langrange equation of motion, 

$$
  \frac{d}{dt}\bigg(\frac{\partial L}{\partial \dot{z}}\bigg) - \frac{\partial L}{\partial z} = 0
$$

   \tab where $z$ is the vertical position and $\dot{z}$ is the vertical velocity.

3. 

4. (Bonus) 

## Problem Set 2

1.

2.

3.

4.
