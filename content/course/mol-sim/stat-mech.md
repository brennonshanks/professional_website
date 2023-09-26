---
title: Statistical Mechanics
type: book
weight: 40
---

<!--more-->

## What is Statistical Mechanics?

In previous lectures, we have studied how particle positions and momenta evolve in time according to Hamilton's equations of motion. Of course, when dealing with real systems, we are almost never concerned with the motion of all of the particles in the system and we know that materials can be well-described by simple thermodynamic laws. However, up to this point, you may feel a bit uneasy that we have swept the dynamics of particles under the rug when we discussed thermodynamics. So far, we collected all of the microscopic modes of energy transfer into the heat term and introduced the entropy fundamental relation. From these very simple assumptions we have found that we can derive nearly all of thermodynamics. But what is heat? Or entropy? To answer these questions, we need to study statistical mechanics. 

We will see that statistical mechanics is a powerful tool to unite microscopic dynamics with macroscopic theory. Statistical mechanics holds whether the system is classical or quantum mechanical, and has been applied to study systems as diverse as molecular systems, black holes, and bird flocking.

## Some Important Definitions

Before we dive into the primary results of statistical mechanics, let's first set the stage with some important concepts, definitions, and notation.

### Dynamical Variables

Recall that a dynamical variable was some variable $A = A(q^f, p^f, t)$. Let's suppose that we want to measure the dynamic variable in the lab. How do we actually define what the true value is? Is it the value of $A$ at the specific instant in time we measure it? How do we accommodate for the fact that $A$ could be changing extremely fast due to atomic motions?  

We can define the value of $A$ as its average over the amount of time that the variable is measured. If the time scale of the measurement is significantly larger than the time scale of molecular motion, the value of A that we measure will take the form,

$$
    A_{exp} = \lim_{\tau \rightarrow \infty}\frac{1}{\tau}\int_{t}^{t+\tau}A(q^f(t'),p^f(t'),t')dt'
$$

which is just an integral relation for the time average of $A$ over a measurement time $\tau$. To see this, just consider that the integral is equivalent to adding up all of the contributions to $A$ over time and the $1/\tau$ term is dividing by the total time of the measurement. The limit ensures that the time measurement is long enough to accurately capture the average. This is analogous to taking an average of a set of measurements in which you add up all the measurement values and divide by the number of samples.

### Phase Space

The mechanical state of a system is specified by 2f variables; namely, the momentum and generalized coordinates of the $f$ particles in a system. The mechanical state comprises some specific point in this space, and we refer to this point as the phase point. Over time, the phase point changes according to the equations of motion, and forms a phase trajectory.

### Ensemble Average

Suppose that we allow some 1-D system to evolve over a time $\tau$. If we choose a volume element, then the probability that the system phase is in the volume element is given by,

$$
    \rho dq^fdp^f = \lim_{\tau \rightarrow \infty}\frac{\Delta t(q^f,p^f,t)}{\tau}
$$

where $\Delta t$ is the total time that the particle spends in the volume element. We call $\rho = \rho(q^f, p^f, t)$ the probability density function. Now, we can combine the dynamical variable measurement for the volume element with our probability density definition to see that,

$$
    A_{exp}(t) = \int A(q^f,p^f,t)\rho (q^f,p^f,t)dq^fdp^f
$$

Note that this integration occurs over the entire phase space. Furthermore, note that this equation only holds if explicit time dependence of A occurs sufficiently slowly over $\tau$. 

Since $\rho$ is a probability density function, it has a few special properties: 

1. $\rho$ is a probability distribution function, so it must normalize to 1. This means that,

    $$
        \int \rho dq^fdp^f = 1
    $$

2. $\rho$ must be non-negative so that, $\rho \leq 0$.

It is very reasonable to question why we would rewrite our original expression with some new, seemingly not useful function $\rho$. We haven't really made too much progress computationally, as all we have done is rearranged the problem with some new definitions. However, the hope is that by defining $\rho$ in this way that we can find a $\rho$ to use in eq \eqref{eq:dynamical} that will allow us to solve for $ A_{exp}(t)$ without ever needing to solve the equations of motion directly. Furthermore, by reformulating the motion of many-particles with respect to this probability density function, perhaps we can gain novel insight that would otherwise be difficult to describe or notice.

### Statistical Equilibrium

Statistical equilibrium occurs when the change in all measured dynamic variables with respect to time is zero, unless the dynamic variable depends explicitly on time. This implies that at equilibrium $A = A(q^f, p^f)$, where the explicit time-dependence is dropped. Thus,

$$
    \frac{dA_{exp}}{dt} = \lim_{\Delta t \rightarrow 0}\frac{1}{\Delta t}\left[\int A(q^f, p^f)[\rho(q^f, p^f, t+\Delta t)-\rho(q^f, p^f, t)]\right]dq^fdp^f
$$

and applying a first-order Taylor expansion on the probability density function gives,

$$
    \frac{dA_{exp}}{dt}= \lim_{\Delta t \rightarrow 0}\int A(q^f, p^f)\frac{\partial \rho}{\partial t}dq^fdp^f
$$

Therefore, the condition of statistical equilibrium is that $\rho$ does not depend explicitly on time, or,

$$
    \frac{\partial \rho}{\partial t} = 0
$$

Since the previous expression must hold for any choice of $A$. 

### The Statistical Ensemble

The concept of a statistical ensemble was introduced by Gibbs. Let's suppose that we make $\mathcal{N}$ identical copies of a system, and we completely transfer the explicit time dependence and Hamiltonian for each copy. This is known as the statistical ensemble. Now, the number of copies of the system that fall in the volume element $dq^fdp^f$ is given by,

$$
    \mathcal{N}\rho(q^f,p^f,t)dq^fdp^f
$$

This represents the number of copies in the phase space around the point $(q^f,p^f)$. Noting that copies of the system are neither generated nor destroyed in this process, the total copy density $N\rho$ is conserved.

