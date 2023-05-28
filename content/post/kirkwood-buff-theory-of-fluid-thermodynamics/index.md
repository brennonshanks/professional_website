---
title: Kirkwood-Buff Theory of Fluid Thermodynamics
date: 2023-05-26T05:53:47.038Z
draft: true
featured: false
authors:
  - admin
tags:
  - statistical mechanics
image:
  filename: ""
  focal_point: Smart
  preview_only: false
---

The Kirkwood-Buff solution theory was presented in a landmark paper in 1951. The theory relates particle number fluctuations in the grand canonical ensemble to integrals of the radial distribution function. In this short introduction to the topic, we will introduce the statistical mechanics required to understand Kirkwood-Buff solution theory as well as provide details on the numerical computation of the Kirkwood-Buff integrals from experimental data. 

An ensemble of systems that have constant chemical potential, volume, and temperature belong to the so-called grand canonical ensemble. Recall that in the canonical ensemble (constant number of particles, volume, and temperature), the probability distribution function is given by the Boltzmann distribution,

$$
    p(\mathbf{r_N}, \mathbf{p_N}) = \frac{1}{h^{3N} N!} \frac{e^{-\beta \mathcal{H}}}{Z}
$$

where $Z$ is the canonical partition function,

$$
    Z = \frac{1}{h^{3N} N!} \int \int \exp (-\beta \mathcal{H}) d\mathbf{r} d\mathbf{p}
$$

that can be directly related to classical thermodynamics by its relation to the Helmholtz free energy,

$$
    F = -kT\log(Z)
$$

The grand canonical ensemble is just an expansion on the concept of the canonical ensemble; in fact, the grand canonical ensemble is just the union of canonical ensembles with different values for the number of particles $N$. Therefore the probability distribution function is just a Boltzmann distribution with an additional contribution from the number of particles and chemical potential,

$$
    p(\mathbf{r_N}, \mathbf{p_N}, N) = \frac{e^{-\beta (\mathcal{H} - N \mu)}}{\Xi}
$$

where the $\Xi$ is the grand partition function,

$$
    \Xi = \sum_{N = 0}^\infty \frac{\exp(N \beta \mu)}{h^{3N} N!} \int \int \exp(-\beta \mathcal{H}) d\mathbf{r}^N d\mathbf{p}^N
$$

where the sum spans over all possible numbers of particles that the constant $\mu V T$ system can exist in. Just as in the canonical ensemble, we can take averages of any quantity-of-interest with respect to the grand canonical ensemble by taking the product of the actual observable $A$ by its corresponding probability and integrating over the entire phase space,

$$
    \langle A \rangle = \sum_{N = 0}^\infty \frac{1}{h^{3N} N!} \int \int A(\mathbf{r_N}, \mathbf{p_N}) p(\mathbf{r_N}, \mathbf{p_N}, N) d\mathbf{r}^N d\mathbf{p}^N
$$

The final piece we need is a relation between the averages of the number of particles. Looking at the partition function $\Xi$, we can see that differentiation with respect to $\mu_i$ will give us the following expression,

$$
    \frac{\partial \Xi}{\partial \mu_i} = \sum_{N = 0}^\infty N_i \frac{\exp(N \beta \mu)}{h^{3N} N!} \int \int \exp(-\beta \mathcal{H}) d\mathbf{r}^N d\mathbf{p}^N = \beta \Xi \langle N_i \rangle
$$

Similarly,

$$
    \frac{\partial^2 \Xi}{\partial \mu_i \partial \mu_j} = \sum_{N = 0}^\infty N_i N_j \frac{\exp(N \beta \mu)}{h^{3N} N!} \int \int \exp(-\beta \mathcal{H}) d\mathbf{r}^N d\mathbf{p}^N = \beta^2 \Xi \langle N_i N_j \rangle
$$

But we can also consider the second derivative of the partition function in an equivalent way,

$$
    \frac{\partial^2 \Xi}{\partial \mu_i \partial \mu_j} = \frac{\partial}{\partial \mu_j} \beta \Xi \langle N_i \rangle = \beta\bigg(\langle N_i \rangle\frac{\partial \Xi}{\partial \mu_j} + \Xi \frac{\partial \langle N_i \rangle}{\partial \mu_j}\bigg)
$$

$$
    = \beta \bigg(\beta \langle N_i \rangle \langle N_j \rangle \Xi + \Xi \frac{\partial \langle N_i \rangle}{\partial \mu_j}\bigg) 
$$

Equating the two expressions gives,

$$
    \beta^2 \Xi \langle N_i N_j \rangle = \beta \bigg(\beta \langle N_i \rangle \langle N_j \rangle \Xi + \Xi \frac{\partial \langle N_i \rangle}{\partial \mu_j}\bigg) 
$$

$$
    \langle N_i N_j \rangle - \langle N_i \rangle \langle N_j \rangle  =  \beta^{-1} \frac{\partial \langle N_i \rangle}{\partial \mu_j} 
$$

Now, consider a region of some volume, $v$, which contains $N_1, ..., N_k$ molecules of $k$-species. First, define the single particle density functional for species $\alpha$ as,

$$
    \rho_\alpha^{(1)}(\mathbf{r_1}) = \sum^{N_\alpha}_{i_\alpha = 1} \delta(\mathbf{r_{i_\alpha}} - \mathbf{r_1})
$$

where the $\delta$ is understood as the Dirac-$\delta$ function. Let's consider the content of this equation fully before proceeding. The term $\rho_\alpha^{(1)}(\mathbf{r_1})$ is explicitly referring to the number density (in atoms/volume units) as a function of position ($\mathbf{r_1}$, also known as configuration space), of a specific species $\alpha$. We can evaluate this functional in the following way. Suppose we are given some vector $\mathbf{r}$, defined with respect to some pre-defined (and arbitrary) coordinate system. Then we just check if that vector points to (or corresponds with) the position of a particle with label $\alpha$. If it does, the functional returns a $\delta$ distribution at that vector, and if not, a zero. Then, the integral of the single particle density functional over the entire volume is just exactly equal to the number of particles of species $\alpha$ such that,

$$
    \int_v \rho_\alpha^{(1)}(\mathbf{r_1}) dv = N_\alpha
$$

which essentially just amounts to counting all of the atoms of species $\alpha$ in the given system. 

Now that we have introduced the singlet particle density functional, we will proceed to the pair density functional, which by a similar definition is given as,

$$
    \rho_{\alpha, \beta}^{(2)}(\mathbf{r_1}, \mathbf{r_2}) = \sum^{N_\alpha}_{i_\alpha = 1} \sum^{N_\beta}_{k_\beta = 1} \delta(\mathbf{r_{i_\alpha}} - \mathbf{r_1})\delta(\mathbf{r_{k_\beta}} - \mathbf{r_2})
$$

which can be understood in a similar way as the single particle density functional. First, give the functional two vectors and then determine if (1) vector 1 points to the position of a particle with label $\alpha$ and (2) vector 2 points to the position of a particle with label $\beta$. If both statements are true then the functional returns a $\delta$ distribution at that pair of vectors, and if not it returns a zero. As in the previous equation, the summation goes over all of the known positions of both particles. In this case, the integral over the entire space is,

$$
    \int_{v_1} \int_{v_2} \rho_{\alpha, \beta}^{(2)}(\mathbf{r_1}, \mathbf{r_2}) dv_1 dv_2 = N_\alpha N_\beta - N_\alpha \delta_{\alpha  \beta}
$$

since in the first integral we will find all particles of label $\beta$ given a specific vector for label $\alpha$, then the second integral will find $N_\beta$ particles for all positions of particles $\alpha$. Thus, the total number of counts where $\rho_{\alpha, \beta}^{(2)}(\mathbf{r_1}, \mathbf{r_2})$ is non-zero is $N_\alpha N_\beta$. However, if $\alpha = \beta$ then we will double count the vectors $N_\alpha$ times, so we need to subtract $N_\alpha \delta_{\alpha \beta}$ in this case.  

Note that to this point we have simply looked a system of particles with fixed positions. Of course, in real physical systems the particles are always moving and we observe the averages of the motions. Therefore, we need to consider an ensemble of systems that represent the average behavior of the system, which amounts to taking the ensemble average of the density functionals. \newline

We then need to evaluate the average of the density functionals in the grand canonical ensemble. Rather than write these explicitly, we just apply Equation \eqref{average} to the integrals of the singlet and pair density functionals to obtain,

$$
    \hat{(\rho)}_\alpha^{(1)}(\mathbf{r_1}) = \langle \rho_\alpha^{(1)}(\mathbf{r_1}) \rangle
$$

$$
    \hat{\rho}_{\alpha, \beta}^{(2)}(\mathbf{r_1}, \mathbf{r_2}) = \langle \rho_{\alpha, \beta}^{(2)}(\mathbf{r_1}, \mathbf{r_2}) \rangle
$$

which by linearity of the expectation gives,

$$
    \int_v \hat{\rho}_\alpha^{(1)}(\mathbf{r_1}) dv = \langle N_\alpha \rangle
$$

$$
    \int_{v_1} \int_{v_2} \hat{\rho}_{\alpha, \beta}^{(2)}(\mathbf{r_1}, \mathbf{r_2}) dv_1 dv_2 = \langle N_\alpha N_\beta \rangle - \langle N_\alpha \rangle \delta_{\alpha  \beta}
$$

Furthermore, by linearity of the expectation we can combine these two equations in the following clever way,

$$
        \int_{v_1} \int_{v_2} [\hat{\rho}_{\alpha, \beta}^{(2)}(\mathbf{r_1}, \mathbf{r_2}) - \hat{\rho}_\alpha^{(1)}(\mathbf{r_1}) \hat{\rho}_\beta^{(1)}(\mathbf{r_2})] dv_1 dv_2 = & \\ [\langle N_\alpha N_\beta \rangle - \langle N_\alpha \rangle \langle N_\beta \rangle]  - \langle N_\alpha \rangle \delta_{\alpha  \beta}
$$

We can further simplify this expression by noting that the means of the density functionals take on specific forms in fluids. For example, the mean of the single density functional of a species $\alpha$ is just the concentration (in atoms/volume) of that species $c_\alpha$. The mean of the pair density functional is given a special definition in terms of the radial distribution function, which is just,

$$
    \hat{\rho}_{\alpha, \beta}^{(2)}(\mathbf{r_1}, \mathbf{r_2}) = c_\alpha c_\beta g_{\alpha, \beta}(r)
$$

Plugging these definitions into our integral equation, we obtain,

$$
     \int_{v} [g_{\alpha, \beta}(r) - 1] dv = & \\ v\frac{\langle N_\alpha N_\beta \rangle - \langle N_\alpha \rangle \langle N_\beta \rangle}{\langle N_\alpha \rangle \langle N_\beta \rangle}  -  \frac{\delta_{\alpha  \beta}}{\langle N_\alpha \rangle}
$$

which is precisely the relationship needed to connect the integrals of the radial distribution function with thermodynamic properties from the grand canonical ensemble. Just take eq \eqref{kbintegral} and substitute in eq \eqref{gcpd} and we obtain,

\begin{equation}
    c_\alpha c_\beta G_{\alpha, \beta} + \delta_{\alpha, \beta}c_\alpha = \frac{\beta}{v}\bigg(\frac{\partial \mu_\alpha}{\partial N_\beta}\bigg)_{T, V, N_{i \neq \beta}}
\end{equation}

\noindent where we have defined,

\begin{equation}
    G_{\alpha, \beta} = \int_{v} [g_{\alpha, \beta}(r) - 1] dv
\end{equation}

\noindent From here, we can use thermodynamic relationships to derive a number of properties of multi-component systems in terms of the Kirkwood-Buff integrals since we know the relationship between thermodynamic derivatives and measurable thermodynamic properties.
