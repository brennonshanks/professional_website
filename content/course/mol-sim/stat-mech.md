---
title: Statistical Mechanics
type: book
weight: 40
---

<!--more-->

## What is Statistical Mechanics?

In previous lectures, we have studied how particle positions and momenta evolve in time according to Hamilton's equations of motion. Of course, when dealing with real systems, we are almost never concerned with the motion of all of the particles in the system and we know that materials can be well-described by simple thermodynamic laws. However, up to this point, you may feel a bit uneasy that we have swept the dynamics of particles under the rug when we discussed thermodynamics. So far, we collected all of the microscopic modes of energy transfer into the heat term and introduced the entropy fundamental relation. From these very simple assumptions we have found that we can derive nearly all of thermodynamics. But what is heat? Or entropy? To answer these questions, we need to study statistical mechanics. 

We will see that statistical mechanics is a powerful tool to unite microscopic dynamics with macroscopic theory. Statistical mechanics holds whether the system is classical or quantum mechanical, and has been applied to study systems as diverse as molecular systems, black holes, and bird flocks.

## Some Important Definitions

{{< youtube HDl63ZSFVwM >}}

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

It is very reasonable to question why we would rewrite our original expression with some new, seemingly not useful function $\rho$. We haven't really made too much progress computationally, as all we have done is rearranged the problem with some new definitions. However, the hope is that by defining $\rho$ in this way that we can find a $\rho$ that will allow us to solve for $A_{exp}(t)$ without ever needing to solve the equations of motion directly. Furthermore, by reformulating the motion of many-particles with respect to this probability density function, perhaps we can gain novel insight that would otherwise be difficult to describe or notice.

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

## Louiville's Theorem and the Canonical Ensemble

{{< youtube XiFEXVWNlpg >}}

### Louiville's Theorem

Recall the equation of continuity from continuum mechanics. The equation of continuity amounts to writing down a mass balance on a system noting that the total mass of a system is conserved. For some fixed region of space, referred to as a control volume, the number of particles in the control volume at any moment $t$ is given by,

$$
    \int_V \rho(\mathbf{r}, t) d \mathbf{r}
$$

where $V$ denotes the control volume and $\rho(\mathbf{r}, t)$ is the number density of particles at position $\mathbf{r}$ at time $t$. If there are no chemical reactions, the rate of change of this integral with respect to time is related to the flux of atoms across the surface of the control volume so that,

$$
    \frac{d}{dt} \int_V \rho(\mathbf{r}, t) d \mathbf{r} = \oint_S \rho(\mathbf{r}, t) v(\mathbf{r}, t) \cdot \mathbf{n}(\mathbf{r}) dS
$$

where $v$ is the average velocity of particles through the surface element $dS$ and $\mathbf{n}(\mathbf{r})$ is the outward unit normal to the control volume surface. We can rewrite the left hand side using the Leibniz integral rule (which can be proved by invoking the bounded convergence theorem) such that,

$$
    \frac{d}{dt} \int \rho(\mathbf{r}, t) d \mathbf{r} = \rho(\mathbf{r}, b) \frac{d b(\mathbf{r})}{dt} -  \rho(\mathbf{r}, a) \frac{d a(\mathbf{r})}{dt} + \int^{b(\mathbf{r})}_{a(\mathbf{r})} \frac{\partial}{\partial t} \rho(\mathbf{r}, t) d \mathbf{r}
$$

where the first two terms related to the specific shape of the control volume go to zero since $a(\mathbf{r}), b(\mathbf{r})$ are fixed in time (control volume cannot deform). We then obtain,

$$
    \frac{d}{dt} \int_V \rho(\mathbf{r}, t) d \mathbf{r} = \int_V \frac{\partial}{\partial t} \rho(\mathbf{r}, t) d \mathbf{r}
$$

Now, the term on the right hand side can be rewritten according to the divergence theorem,

$$
    -\oint_S \rho(\mathbf{r}, t) v(\mathbf{r}, t) \cdot \mathbf{n}(\mathbf{r}) dS = \int_V \nabla \cdot (\rho \mathbf{v}) d\mathbf{r}
$$

which after plugging into our original expression and rearranging under the integral we obtain,

$$
    \int_V \frac{\partial \rho}{\partial t} + \nabla \cdot (\rho \mathbf{v}) d\mathbf{r} = 0
$$

But since this holds for any $V$, we must have, 

$$
    \frac{\partial \rho}{\partial t} + \nabla \cdot (\rho \mathbf{v}) = 0
$$

This is an expression for the equation of continuity in continuum mechanics. By analogy, in phase space we have a control volume in 2$f$-coordinates $(q_1, ..., q_f, p_1, ..., p_f)$ and velocities $(\dot{q}_1, ..., \dot{q}_f, \dot{p}_1, ..., \dot{p}_f)$ with a total number density of $\mathcal{N}\rho$. Plugging these into the equation of continuity gives,

$$
    \frac{\partial \mathcal{N}\rho}{\partial t} + \sum_{i=1}^f \left[\frac{\partial (\mathcal{N}\rho \dot q_i)}{\partial q_i}+\frac{\partial (\mathcal{N}\rho \dot p_i)}{\partial p_i}\right] = 0
$$

We note that $\mathcal{N}$ is a constant and apply Hamilton's equations of motion to find,

$$
    \frac{\partial\rho}{\partial t} + \sum_{i=1}^f  \left[ \frac{\partial}{\partial q_i}\bigg(\rho\frac{\partial\mathcal{H}}{\partial p_i}\bigg) - \frac{\partial}{\partial p_i} \bigg(\rho \frac{\partial \mathcal{H}}{\partial q_i}\bigg)\right] = 0
$$

which implies that,

$$
    \frac{d \rho}{d t} = \frac{\partial \rho}{\partial t} + \{\rho,H\} = 0
$$

or in other words, that $\rho$ is a constant of motion. This means that the number of copies in a statistical ensemble is conserved. This is a statement that holds whether or not the system is in statistical equilibrium or not. However, we now require that the probability be a constant of motion with respect to the Hamiltonian and that it not depend explicitly on time in order for the system to be in statistical equilibrium.

### The Canonical Ensemble

So now the question becomes: how do we express $\rho$ in a productive way? What functional form does it take? We first make an assumption that $\rho = \rho(H)$ only. Now, we proceed to hypothesize that $\rho$ takes the following form,

$$
    \rho(q^f,p^f) = \frac{1}{C}e^{-\beta H(q^f,p^f)}
$$

where C is determined by the normalization condition such that,

$$
    1 = \int \rho (q^f,p^f) dq^fdp^f = \int\frac{1}{C}e^{-\beta H(q^f,p^f)}dq^fdp^f 
$$

The statistical ensemble characterized by a $\rho$ of this form is referred to as the canonical ensemble. The ensemble average of the energy H is called the internal energy ($U$), and is given by,

$$
    U \equiv \langle H \rangle = \int H \rho(q^f,p^f) dq^fdp^f
$$

where all we have done is used new notation for the same integral we introduced earlier when we discussed ensemble averages,

$$
    \langle A \rangle = \int A(q^f, p^f) \rho(q^f, p^f) dq^f dp^f = \frac{1}{C}\int A(q^f, p^f) e^{-\beta H(q^f, p^f)} dq^f dp^f
$$

for the given form of $\rho$. We now have an expression for $U$ in terms of the microscopic quantities from statistical mechanics. However, we also have an expression for $U$ in thermodynamics; namely, 

$$
    dU = TdS - PdV
$$

which will allow us to relate the thermodynamic concepts of temperature, entropy, and work to the microscopic expression for $U$. To do this, we let $\Theta = \beta^{-1}$ and rewrite the canonical ensemble probability density in terms of $H$,

$$
    H = -\Theta log(\rho) - \Theta log(C)
$$

Taking the ensemble average of these quantities gives,

$$
    U = \Theta \eta + \alpha
$$

where we have defined two new variables given by,

$$
    \eta = -\langle log(\rho) \rangle
$$

$$
    \alpha = -\Theta log(C)
$$

Taking the total derivative of $U$ we find that we can express dU as,

$$
    dU = \eta d\Theta + \Theta d\eta + d\alpha
$$

We now need to expand the $d\alpha$ term in a systematic way so that we can compare this expression with the one we are familiar with from thermodynamics. To this end, we consider an example system of particles confined to a piston cylinder device. How do we write $H$ for this system? $H$ is a function of the particle velocities, interactions, and piston position (since it imparts an external force on the system), which we can write as,

$$
    H = \sum_{i=1}^N \frac{||\mathbf{p_i}||^2}{2m_i} + \phi(\mathbf{r}^N) + \psi(\mathbf{r}^N, \lambda)
$$

where $\lambda$ is the position of the piston and is common to all particles in the system. The point here is that we can perform work on the system by changing $\lambda$ and that the Hamiltonian is a function of $\lambda$. From the normalization condition we have that $C=C(\Theta, \lambda)$. The total derivative of $C$ is then,

$$
    dC = \bigg(\frac{\partial C}{\partial \Theta}\bigg) d\Theta + \bigg(\frac{\partial C}{\partial \lambda}\bigg) d\lambda
$$

and we also know from our definition of $\alpha$ that,

$$
    d \alpha = -\Theta d \log{C} - \log{C} d\Theta = -\Theta \frac{dC}{C} - \log{C} d\Theta
$$

and rewriting this expression by plugging in for $dC$ and $\log{C} = -\alpha/\Theta$ gives,

$$
    d\alpha = \bigg[\frac{\alpha}{\Theta} - \frac{\Theta}{C}\bigg(\frac{\partial C}{\partial \Theta}\bigg) \bigg] d \Theta - \frac{\Theta}{C}\bigg(\frac{\partial C}{\partial \lambda}\bigg) d\lambda
$$

Now, let's rewrite these partial derivatives with respect to the integral of the probability density function. This gives,

$$
    \frac{1}{C}\bigg(\frac{\partial C}{\partial \Theta}\bigg)_\lambda = \frac{1}{C} \frac{\partial}{\partial \Theta} \int e^{-H/\Theta}dq^fdp^f = \frac{1}{C} \int \frac{\partial}{\partial \Theta} e^{-H/\Theta}dq^fdp^f
$$

and taking the derivative of the inside gives,

$$
    = \frac{1}{C} \int \frac{H}{\Theta^2} e^{-H/\Theta}dq^fdp^f = \frac{U}{\Theta^2}
$$

Similarly,

$$
    \frac{1}{C}\bigg(\frac{\partial C}{\partial \lambda}\bigg)_\Theta = \frac{1}{C} \frac{\partial}{\partial \lambda} \int e^{-H/\Theta}dq^fdp^f = \frac{1}{C} \int \frac{\partial}{\partial \lambda} e^{-H/\Theta}dq^fdp^f
$$

which is just,

$$
    = \frac{1}{C} \int -\frac{1}{\Theta}\frac{\partial H}{\partial \lambda} e^{-H/\Theta}dq^fdp^f =  -\frac{1}{\Theta} \bigg\langle \frac{\partial H}{\partial \lambda} \bigg\rangle
$$

Combining these expressions into our expression for $d\alpha$,

$$
    d\alpha = \bigg[\frac{\alpha}{\Theta} - \Theta \frac{U}{\Theta^2} \bigg] d \Theta + \Theta \frac{1}{\Theta} \bigg\langle \frac{\partial H}{\partial \lambda} \bigg\rangle d\lambda = \frac{1}{\Theta}(\alpha - U)d\Theta + \bigg\langle \frac{\partial H}{\partial \lambda} \bigg\rangle d\lambda
$$

and finally substituting in our original expression for $U = \Theta \eta + \alpha$ we obtain,

$$
    dU = \Theta d\eta +\bigg \langle \frac{\partial H}{\partial \lambda}\bigg \rangle d\lambda
$$

Thus, we find that the first term is related to $TdS$ and the second term is related to the work done on the system. The fact that $TdS = \Theta d\eta$ means that,

$$
    \Theta \propto T
$$

$$
    d \eta \propto dS
$$

We choose the constant of proportionality as the Boltzmann constant, $k_B$, so that,

$$
    d \eta = d\bigg(\frac{S}{k_B}\bigg)
$$

which implies that a functional form for the entropy in terms of classical statistical mechanical variables is,

$$
    S = -k_B\langle log(\rho)\rangle 
$$

Also note that we have the relation for $\alpha$ given by,

$$
    \alpha = U - \Theta \eta = U - TS = F
$$

which you may recognize as just the Helmholtz free energy, F, from classical thermodynamics. This gives us an approximate form for the Helmholtz free energy as,

$$
    F = -k_BTlog(C)
$$

## Physical Motivation for the Canonical Ensemble

{{< youtube aFEovHmSvQk >}}

The previous section gave a definition for $\beta$ as,

$$
    \beta = \frac{1}{k_BT}
$$

In the canonical ensemble definition for the probability of observing a particle in some volume element around the point $(q^f,p^f)$, we now have,

$$
    \rho (q^f,p^f) = \frac{1}{C}e^{-H(q^f,p^f)/k_BT}
$$

But this means that the temperature of the system must be specified to determine $\rho$. To do this in practice, we need to allow for transfer of energy with a system and its surroundings. In fact, we now show that the canonical ensemble is the only possible ensemble that can account for a system in thermal contact with its surroundings. Let $\mathcal{T}$ be an isolated system containing a subsystem $\mathcal{S}$ enclosed in a rigid, impermeable wall, surrounded by subsystem $\mathcal{L}$ called the surroundings. The Hamiltonian of the system can be written as,

$$
    H_\mathcal{T}(q^{m+n},p^{m+n}) = H_\mathcal{S}(q^m,p^m) + H_\mathcal{L}(q^{n},p^{n}) + H_{int}(q^{m+n},p^{m+n})
$$

The last term arises from the interactions between the subsystem $\mathcal{S}$ and the surroundings $\mathcal{L}$. m,n are the mechanical degrees of freedom of $\mathcal{S}$ and $\mathcal{L}$, respectively. We need to assume that the internal interaction Hamiltonian is negligible in magnitude compared to the subsystem and surroundings Hamiltonian's; meaning,

$$
    H_\mathcal{T}(q^{m+n},p^{m+n}) \approx H_\mathcal{S}(q^m,p^m) + H_\mathcal{L}(q^{n},p^{n}) 
$$

This implies that the interaction between $\mathcal{S}$ and $\mathcal{L}$ is weak, but still sufficient to allow for a transfer of energy between the two systems over a long period of time. This transfer of energy is sufficient to maintain a constant temperature without contributing significantly to the total Hamiltonian. 

We now split the subsystem $\mathcal{S}$ into two sub-subsystems A and B, with mechanical degrees of freedom $m_A$ and $m_B$, such that $m =m_A+m_B$. We now suppose the interactions between these two are sufficiently weak so that,

$$
    H_\mathcal{S}(q^{m},p^{m}) \approx H_A(q^{m_a},p^{m_a}) + H_B(q^{m_b},p^{m_b}) 
$$

This approximate independence implies that,

$$
    \rho_{\mathcal{S}} \approx \rho_A\rho_B
$$

since independent probabilities can be multiplied together to give the total probability. Taking the logarithm of both sides gives,

$$
    log(\rho_\mathcal{S}) \approx log(\rho_A) + log(\rho_B)
$$

However, we know from Liouville's Theorem that $\rho$ is a function of constants of motion. We also now know that the logarithm of $\rho$ is additive. This necessarily implies that $log(\rho)$ is a linear function of constants of motion that are additive. If we assume that $\rho = \rho(H)$, we will obtain the following expression,

$$
    log(\rho) = mH + b
$$

$$
    \rho = e^be^{mH}
$$

which is precisely the form of the canonical distribution function supposed earlier. You may wonder why we can still apply Liouville's theorem here since the system in thermal contact is not isolated. The reason for this is that over a small time interval, if the interactions between systems are sufficiently weak, then the system will behave approximately isothermally over that time. If we stitch together a large number of these time intervals, we expect to find the canonical distribution.

## Applications of the Canonical Ensemble

{{< youtube uoieTQ3Qb3M>}}

We can use the canonical probability distribution to explore many properties of a statistical mechanical system. 

### The Maxwell-Boltzmann Distribution

One application is to find the distribution of momentum of a particle in a system of $N$ particles held in thermal equilibrium with its surroundings. In the absence of an external field, we can write the Hamiltonian for such as a system as,

$$
    H(\mathbf{r}^N, \mathbf{p}^N) = \sum_{i = 1}^N \frac{||\mathbf{p}_i||^2}{2m_i} + \phi(\mathbf{r}^N)
$$

where $\phi(\mathbf{r}^N$) is recognized as the particle interaction potential energy contribution. To find the probability distribution on the velocity of a single particle, we can proceed to integrate out all position and momentum coordinates except for a single arbitray particle to obtain,

$$
    \rho(\mathbf{p}_1)d\mathbf{p}_1
$$

which is just the momentum probability density function for a single particle. Proceeding in this way, let's start with the partition function in the canonical ensemble,

$$
    \rho d\mathbf{r}^N d\mathbf{p}^N = \frac{1}{C}\int e^{-\beta H} d\mathbf{r}^N d\mathbf{p}^N
$$

and substituting $H$ into the equation we get,

$$
    \rho d\mathbf{r}^N d\mathbf{p}^N = \frac{e^{-\beta \bigg(\sum_{i = 1}^N \frac{||\mathbf{p_i}||^2}{2m_i} + \phi(\mathbf{r}^N)\bigg)}}{\int e^{-\beta \bigg(\sum_{i = 1}^N \frac{||\mathbf{p}_i||^2}{2m_i} + \phi(\mathbf{r}^N)\bigg)} d\mathbf{r}^N d\mathbf{p}^N} 
$$

We can begin by solving for $C$ to obtain,

$$
    C = \int e^{-\beta \bigg(\sum_{i = 1}^N \frac{||\mathbf{p_i}||^2}{2m_i} + \phi(\mathbf{r}^N)\bigg)} d\mathbf{r}^N d\mathbf{p}^N = \int \prod_{i=1}^N e^{-\beta \frac{||\mathbf{p}_i||^2}{2m_i}} d\mathbf{p}^N \int e^{-\beta \phi(\mathbf{r}^N)} d\mathbf{r}^N
$$

which is equal to,

$$
    C = \prod_{i=1}^N \bigg(\frac{2 \pi m_i}{\beta}\bigg)^{3/2} \int e^{-\beta \phi(\mathbf{r}^N)} d\mathbf{r}^N
$$

Recognizing that we now just need to take the integral over $\rho d\mathbf{r}^N d\mathbf{p}^N$ with respect to all variables but a single momentum, we obtain,

$$
   C \int \rho d\mathbf{r}^N d\mathbf{p}^{N-1} = \int e^{-\beta \bigg(\sum_{i = 1}^N \frac{||\mathbf{p}_i||^2}{2m_i} + \phi(\mathbf{r}^N)\bigg)} d\mathbf{r}^N d\mathbf{p}^{N-1}
$$

which gives,

$$
    C \rho(\mathbf{p}_1) d\mathbf{p}_1 = \prod _{i=1}^{N-1} \bigg(\frac{2 \pi m_i}{\beta}\bigg)^{3/2} e^{-\beta \frac{||\mathbf{p}_1||^2}{2m_1}} d \mathbf{p}_1 \int e^{-\beta \phi(\mathbf{r}^N)} d\mathbf{r}^N
$$

and finally dividing by $C$ on both sides,

$$
    \rho(\mathbf{p}_1) d\mathbf{p}_1 = \frac{\prod _{i=1}^{N-1} \bigg(\frac{2 \pi m_i}{\beta}\bigg)^{3/2} e^{-\beta \frac{||\mathbf{p}_1||^2}{2m_1}} d \mathbf{p}_1 \int e^{-\beta \phi(\mathbf{r}^N)} d\mathbf{r}^N}{\prod _{i=1}^{N} \bigg(\frac{2 \pi m_i}{\beta}\bigg)^{3/2} \int e^{-\beta \phi(\mathbf{r}^N)} d\mathbf{r}^N}
$$

or equivalently,

$$
    \rho(\mathbf{p}_1) d\mathbf{p}_1 = \bigg(\frac{1}{2 m_1 \pi k_B T}\bigg)^{3/2} e^{-\beta \frac{||\mathbf{p}_1||^2}{2m_1}} d \mathbf{p}_1
$$

This is known as the Maxwell-Boltzmann distribution.

### The Equipartition Theorem

You may have noticed in previous examples that each quadratic term in positions or momenta contribute a factor of $\beta^{-1/2}$ to the partition function. This implies that each quadratic term makes a contribution of $k_BT/2$ to the total energy. Let's generalize this observation here by writing our Hamiltonian in the following form,

$$
    H(q^f,p^f) = aq_1^2 + h(q_2, ..., q_f, p_1, ..., p_f)
$$

and computing the canonical ensemble average of $aq_1^2$. We proceed by writing,

$$
    \langle a q_1^2 \rangle = \frac{1}{C} \int a q_1^2 e^{-\beta a q_1^2} e^{-\beta h} d\mathbf{q}^f d\mathbf{p}^f = \frac{a}{C} \sqrt{\frac{\pi}{4(\beta a)^3}} \int e^{-\beta h} d\mathbf{q}^{f\neq 1} d\mathbf{p}^f
$$

but $C$ is equal to,

$$
    C = \int e^{-\beta a q_1^2} e^{-\beta h} d\mathbf{q}^f d\mathbf{p}^f = \sqrt{\frac{\pi}{\beta a}} \int e^{-\beta h} d\mathbf{q}^{f \neq 1} d\mathbf{p}^f 
$$

which means that,

$$
    \langle a q_1^2 \rangle = \frac{a \sqrt{\frac{\pi}{4(\beta a)^3}} \int e^{-\beta h} d\mathbf{q}^{f\neq 1} d\mathbf{p}^f}{\sqrt{\frac{\pi}{\beta a}} \int e^{-\beta h} d\mathbf{q}^{f \neq 1} d\mathbf{p}^f} = \frac{1}{2}\beta^{-1} = \frac{1}{2} k_BT
$$

Now, this result can be trivially generalized to Hamiltonian's of the form,

$$
    H(q^f, p^f) = \sum_{i=1}^f (a_iq_i^2 + b_ip_i^2)
$$

to show that $U = f k_B T$. This idea that the energy of a system is equally partitioned amongst each degree-of-freedom in the system is called the equipartition theorem.

## Corrections from Quantum Mechanics 

{{< youtube 2finZu0m6WM >}}

We derived an equation for the Helmholtz energy using classical statistical mechanics for a particle in a box. However, we need to extend this to a general argument and introduce quantum mechanical corrections to the determined equation. 

Suppose we have N identical particles ($m_i = m_j$) in a rectangular box of dimension $L_x,L_y,L_z$. The Hamiltonian is given by,

$$
    H(\mathbf{r^N},\mathbf{p^N}) = \sum_{i=1}^N \frac{||\mathbf{p_i}||^2}{2m} + \psi_w (\mathbf{r^N})
$$

such that $\psi_w$ represents the interactions of the particles with the walls of the box. We can determine C by integrating $e^{-\beta H}$ over all of phase space according to,

$$
    C = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} ... \int_{-\infty}^{\infty} e^{-\beta H}dx_1dy_1dz_1dx_2...dz_Ndpx_1dpy_1...dpz_N
$$

where the integrals span the 6N-dimensional phase space. Solving this integral we find that,

$$
    C = V^N\bigg(\frac{2\pi m}{\beta}\bigg)^{3N/2}
$$

When we apply this to our equation for the Helmholtz energy, we find that,

$$
    F = -k_BT\log(V^N\bigg(\frac{2\pi m}{\beta}\bigg)^{3N/2}) = -k_BT\bigg[N\log(V) + \frac{3N}{2}\log(2 \pi m k_B T)\bigg]
$$

Now, we need to look at this function and see if it makes sense according to classical thermodynamics. The first thing to check is if $F$ is extensive so that $F(T, \lambda V, \lambda N) = \lambda F(T,V,N)$. Begin by substituting $V$ and $N$ for $\lambda V$ and $\lambda N$ so that, 

$$
    F = -k_BT\bigg[\lambda N \log(\lambda V) + \frac{3 \lambda N}{2}\log(2 \pi m k_B T)\bigg]
$$

which gives,

$$
    F = -\lambda k_BT\bigg[ N \log(\lambda V) + \frac{3 N}{2}\log(2 \pi m k_B T)\bigg] \neq \lambda F(T,V,N)
$$

Therefore, we find that $F$ is not extensive! This means that the statistical mechanics that we have developed is inconsistent with thermodynamics. The problem isn't with what we did, but rather how we started; namely, with classical mechanics. Atoms and particles are governed by quantum mechanics, and therefore we must introduce some corrections.

### Indistinguishable Particles

In classical mechanics, every particle is distinguishable from every other particle. In fact, we reasoned that we can track the position and velocity of every particle in a system and see how those variables evolve according to Newton's equations of motion. According to quantum mechanics, however, this can't be done even in principle! In quantum mechanics, identical particles are fundamentally indistinguishable, and therefore no computation or experiment can ever be devised to distinguish between them. This means that when we perform the integral over phase space when we calculate $C$ that we are actually over counting the number of states. To adjust for this, we just need to divide by the number of ways of labeling the particles, which is just related to the factorial operator. We therefore divide C by this degeneracy factor so that,

$$
    C' = \frac{1}{N!}\int e^{-\beta H(q^f,p^f)}dq^fdp^f
$$

Let's now check if $F$ is extensive. We know that $F = -k_BT\log C'$, which is given by,

$$
    F = -k_BT\bigg[ N \log(V) + \frac{3 N}{2}\log(2 \pi m k_B T) - \log N! \bigg]
$$

for which we can apply Sterling's approximation, $\log N! = N \log N - N$ for sufficiently large $N$,

$$
    F = -k_BT\bigg[ N \log(V) + \frac{3 N}{2}\log(2 \pi m k_B T) - N \log N + N \bigg]
$$

We now make the substitution $V$ and $N$ for $\lambda V$ and $\lambda N$ so that,

$$
    F = -k_BT\bigg[ \lambda N \log(\lambda V) + \frac{3 \lambda N}{2}\log(2 \pi m k_B T) - \lambda N \log (\lambda N) + \lambda N \bigg]
$$

which is, 

$$
    F = -\lambda k_BT\bigg[N \log(V) + \frac{3 N}{2}\log(2 \pi m k_B T) - N \log (N) + N + \cancel{(\log \lambda - \log \lambda)} \bigg]
$$

showing that, 

$$
    F(T, \lambda V, \lambda N) = \lambda F(T,V,N)
$$

for our new expression $C'$.

### The Heisenberg Uncertainty Principle

To this point, we have taken integrals over infinitesimally small regions of the phase space in position and momenta, which violates the uncertainty principle. The uncertainty principle demands that a simultaneous measurement of position and momentum satisfies,

$$
    (\Delta q)(\Delta p) \geq h
$$

where $h$ is Planck's constant in units of action (distance times momentum or equivalently energy times time). To think about how the uncertainty principle influences our normalization factor $C$, consider what happens when we take a phase space integral in classical mechanics. The integral,

$$
    C = \int_{p} \int_q e^{-\beta H} dq dp
$$

assumes that all states inside the infinitesimal box $dq dp$ are distinguishable states and they all contribute to $C$. In reality, we only have distinguishable states up to the phase space volume $h$, so the integral should be written as,

$$
    C = \frac{1}{h}\int_{p} \int_q e^{-\beta H} dq dp. 
$$
    
For $f$ degrees-of-freedom, the integral then becomes,

$$
    C = \frac{1}{h^f}\int_{p^f} \int_{q^f} e^{-\beta H} dq^f dp^f
$$

which for $N$ particles in a three-dimensional space gives,

$$
    C = \frac{1}{h^{3N}}\int_{p^f} \int_{q^f} e^{-\beta H} dq^f dp^f
$$

Finally, combining our results from particle indistinguishability and the uncertainty principle gives the correct definition for the canonical partition function, 

$$
    Z = \frac{1}{h^{3N}N!} \int e^{-\beta H} dq^f dp^f
$$

These corrections essentially amount to preventing over-counting of true quantum states with classical mechanical integrals. 

## Other Statistical Ensembles

### Canonical Ensemble

A canonical ensemble is a collection of systems that have the same values of $N$, $V$, and $T$ and evolve according to the same Hamiltonian. It therefore represents a system at thermal equilibrium with its surroundings. In the canonical ensemble, we then argued that the equilibrium probability density for a system of identical particles is, 

$$
    \rho(\mathbf{q}^f, \mathbf{p}^f) = \frac{1}{h^{3N}N!}\frac{1}{Z} e^{-\beta H}
$$

where $Z$ is the canonical partition function given by,

$$
    Z = \frac{1}{h^{3N}N!}\int e^{-\beta H} d\mathbf{q}^f d\mathbf{p}^f
$$

We then found that we could derive the free energy (Helmholtz for an $NVT$ system) in the following way,

$$
    F = U - TS = -k_B T \log Z
$$

and derive important relationships like, 

$$
    \langle H \rangle = U = -\bigg(\frac{\partial \log Z}{\partial \beta}\bigg)_V
$$

or,

$$
    P = k_B T \bigg(\frac{\partial \log Z}{\partial V}\bigg)_{T,N}
$$

The canonical ensemble describes systems that can exchange heat with the surroundings but not volume or matter. However, the canonical ensemble is just one type of system that is relevant to real systems. It doesn't take that much imagination to consider a system which can not only exchange heat (and thus equilibrate temperature with its surroundings) but also exchange volume or particles. These ensembles will have different probability density functions, free energies, and mathematical relationships.

### The Isothermal-Isobaric Ensemble

The isothermal-isobaric ensemble is the same as a canonical ensemble aside from the pressure being held constant instead of volume. Therefore, we refer to the isothermal-isobaric ensemble as the $NPT$ ensemble. The free energy for an $NPT$ system is the Gibbs free energy (as an exercise, perform a partial Legendre transform of internal energy $U$ to convert $S \to T$ and $V \to P$) such that,

$$
    G = U - TS + PV
$$

which can be related to statistical mechanics through the probability distribution function,

$$
    \rho(\mathbf{q}^f, \mathbf{p}^f; N) = \frac{1}{h^{3N}N!} \frac{1}{\Delta_N} e^{-\beta(H + PV)}
$$

where $\Delta_N$ is the isothermal-isobaric partition function,

$$
    \Delta_N = \frac{1}{h^{3N}N!V_0}\int^\infty_0 dV \int e^{-\beta(H + PV)} d\mathbf{q}^f d\mathbf{p}^f
$$

which can be interpreted as the volume average of canonical ensembles with weight $e^{-\beta PV}$. The Gibbs free energy is then,

$$
    G = -k_B T \log \Delta_N
$$

The isothermal-isobaric ensemble describes many experiments that are performed at constant temperature and pressure and is useful for determining the equation of state of fluids near atmospheric conditions.

### The Grand Canonical Ensemble

The thermodynamic state of a system that is open, or able to exchange particles with its surroundings, is characterized by the grand potential (as an exercise, try the partial Legendre transform $U$ exchanging $N \to \mu$ and $S \to T$),

$$
    \Omega = U - TS - N\mu
$$

An ensemble of systems having the same values of chemical potential, volume and temperature ($\mu VT$) is referred to as a grand canonical ensemble. The phase space of the grand canonical ensemble is essentially just the union of canonical ensembles for every possible value of $N$. In this way, the probability distribution function is written as,

$$
    \rho(\mathbf{q}^f, \mathbf{p}^f; N) = \frac{1}{h^{3N}N!} \frac{1}{\Xi} e^{-\beta(H - N \mu)}
$$

where $\Xi$ is the grand canonical partition function,

$$
    \Xi = \sum_{N = 0}^\infty \frac{e^{\beta N \mu}}{h^{3N}N!} \int e^{-\beta H} d\mathbf{q}^f d\mathbf{p}^f
$$

The grand canonical ensemble is used in molecular simulations for vapor-liquid equilibria and adsorption processes. 

### General Rules of Statistical Ensembles

The problem of statistical mechanics amounts to counting - or to find ways to avoid counting - the number of equally probable ways that a system can divide up its energy. The partition function is precisely this number, so if the partition function is known for a given ensemble, we can calculate the free energy and in principle have complete knowledge of system thermodynamics. Thus, if $Q$ is some partition function for a given ensemble, we can always compute the corresponding free energy using the relation,

$$
    FE = -k_B T \log Q
$$

Additionally, the probability distribution function for a given ensemble can allow us to calculate moments of some dynamic variable according to the equation,

$$
    \langle A \rangle = \frac{1}{Q h^{3N}N!} \int \rho A d\mathbf{q}^f d\mathbf{p}^f
$$

regardless of the ensemble. Although we will not explore any other ensembles in this class, there are many described in the literature that must be considered in certain cases. It is therefore crucial to analyze the physical system that you want to model and determine whether or not a certain ensemble is appropriate for the target application. 

References:

[1] Kusaka, Isamu. Statistical Mechanics for Engineers. Cham: Springer International Publishing, 2015.

[2] Hansen, Jean-Pierre, and I. R. McDonald. Theory of Simple Liquids: With Applications to Soft Matter. San Diego: Academic Press, 2013.

[3] Goodstein, David L. States of Matter. Courier Corporation, 2014.

