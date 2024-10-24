---
title: The Ornstein-Zernike Equation
date: 2023-07-20T05:53:47.038Z
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

## Introduction

In Ornstein and Zernike's seminal work, \textit{Accidental deviations of density and opalescence at the critical point of a single substance, in: KNAW, Proceedings, 17 II, 1914, pp. 793-806}, it was shown that the total correlation between molecules in a statistical mechanical system must obey an integral equation of the form, 

$$
    h(r_{12}) = c(r_{12}) + n\int d\mathbf{r_3} c(r_{13})h(r_{23})
$$

where $h(r_{ij})$ is the total correlation function between particles $i$ and $j$ (note that $h(r_{ij}) = g(r_{ij}) - 1$, where $g(r_{ij})$ is the more familiar radial distribution function) and $c(r_{ij})$ is the 'direct' correlation between particles $i$ and $j$. In this article, I will try and demystify this equation using physical arguments from Ornstein and Zernike's original paper as well as the more recent formulations described in \textit{Liquid State Theory} from Hansen and McDonald as well as Santos' \textit{A Concise Course on the Theory of Classical Liquids}.

## Ornstein and Zernike's Original Derivation

The motivation for Ornstein and Zernike's work was from an original paper on critical behavior of statistical mechanical systems from Smoluchowski, with the main problem being that his volume elements, of which he used to partition up a system of particles, were assumed to be mutually independent of one another. At this stage, the whole premise might already sound a little fishy. We know that liquids interact with each other strongly, so of course this mutual independence assumption must be a problem. Why are we even talking about volume elements in the first place? And what is meant by their mutual independence? 

Ornstein and Zernike implore us to consider a statistical mechanical system composed of a finite set of volume elements containing a finite number of particles so that the total volume $V$ is,

$$
    V = v_1 + v_2 + ...
$$

and the total number of particles $N$ is,

$$
    N = n_1 + n_2 + ...
$$

Nice! Intuitively, all we have done is taken a system of particles and discretized the position space into finite volume elements which contain a finite set of particles. Of course, in an atomic systems the particles are always moving, and indeed, always passing from one volume element to another. In general, we will say that the mean square deviation of the number of particles in a given volume element $v_i$ based on the atomic motion is, $\overline{(n_i - \bar{n_i})^2}$. If the number of particles in the element of volume is large, then this mean square deviation is approximately equal to the variance of the number of particles in the volume element. If we consider that our atomic system is a subsystem of some larger collection of particles, then we can express the mean number of particles in our system $\bar{N}$ as the sum of the mean number of particles in each volume element so that,

$$
    \bar{N} = \bar{n_1} + \bar{n_2} + ...
$$

and therefore the mean square deviation of the number of particles in our system is,

$$
    \overline{(N-\bar{N})^2} = \overline{[n_1 + n_2 + ... - (\bar{n_1} + \bar{n_2} + ...)]^2} = \overline{[(n_1 - \bar{n_1}) + (n_2 - \bar{n_2}) + ...]^2}
$$

which has a complicated expansion given by,

$$
    = \overline{(n_1 - \bar{n_1})^2 + (n_2 - \bar{n_2})^2 + ... + (n_1 - \bar{n_1})(n_2 - \bar{n_2}) +  (n_1 - \bar{n_1})(n_3 - \bar{n_3}) + ...}
$$

and, assuming that the cross correlations are not related and that the number of particles are equal across all of the volume elements (in which we will say there are $p$ in total) gives,

$$
    =p\overline{(n-\bar{n})^2}
$$

The biggest problem here is the cross terms which appear in our expansion (eq \eqref{expansion}), are at odds with a mutual independence approximation. Indeed, if the system were truly independent, then there would be no contribution to the mean square deviation from pairs of different volume elements. This forms the key difference between Ornstein and Zernike's formulation and that of Smulochowski.

### The Ornstein-Zernike Equation

Now, consider that we take our system and subdivide into an infinite number of volume elements and select one to be our reference, $dv_0$. We want to ask how fluctuations in our local volume element $dv_0$ influence the densities of all other volume elements in the system, which is of course related to how much the particles in our reference volume interact with all the other particles. On average, we claim that the average density in our volume element, $\bar{\mathbf{v}_0}$, is linearly related to the density in all other volume elements so that,

$$
    \bar{\mathbf{v}_0} = f_1\mathbf{v}_1dv_1 + f_2\mathbf{v}_2dv_2 + ...
$$

where $f_i$ are coefficients of the linear equation relating the local density to that of the other volume elements. Generally, we could write this expression as a Taylor expansion over terms of increasing order, although Ornstein and Zernike claim that the linear term is sufficient for their purposes. Although we will table this for now, it is an interesting question as to whether such an expansion is truly sufficient for statistical mechanics of liquids and whether or not this causes issues with the OZ relation methods. Moving on, we assume that this function is continuous and well-behaved over the so-called 'sphere of attraction' of the system, so we can rewrite this sum as an integral of continuous functions such that,

$$
     \bar{\mathbf{v}_0} = \int f(\mathbf{r})\mathbf{v}(\mathbf{r})d\mathbf{r}.
$$

where the integral is understood to go over all of $\mathbf{r}$. Note that the 'sphere of attraction' simply refers to the range of direct influence of the particles of $dv_0$ on the other particles in the system. We would expect such a sphere to be finite, since the direct influence of particles in our reference volume is an interatomic potential that is at its strongest Coulombic with $\propto 1/r$ dependence. However, note that this assumption leads to difficulties with the Fourier transform (see section \ref{FT}). More generally however, the function $\mathbf{v}(\mathbf{r})$ is not actually continuous if we consider that the particles are point particles, the reason being that if we create an infinite number of volume elements for the system that there will be some volume elements with particles and others with none. Such a problem is avoided by rewriting the expressions in terms of a new function which will be introduced later. However, in Ornstein and Zernike's original work, there is not a satisfactory discussion of why such a function should be continuous at all, which would require further nuance and discussion found in the free energy functional approach discussed later.

Let us now suppose that the density in our volume element is known to be $\mathbf{v_0}$ and write the average density at any other point in space as,

$$
    \bar{\mathbf{v}}(\mathbf{r}) = g(\mathbf{r}, \mathbf{v_0}d\mathbf{r_0})
$$

the function $g$ being dependent on, of course, the position in the system and choice of reference. What then is $g$ given that we know $f$? Selecting a known value of $\mathbf{v}_1$ at $\mathbf{r_1}$ would give us a $g$ of,

$$
     \bar{\mathbf{v}}(\mathbf{r}) = g(\mathbf{r} - \mathbf{r_1}, \mathbf{v_1}d\mathbf{r_1})
$$

which is just the definition of $g$ selected at a point shifted in space from our original reference. The average value at $\mathbf{r_0}$ is then simply,

$$
    \bar{\mathbf{v_0}}(\mathbf{r}) = g(\mathbf{r_1}, \mathbf{v_1}d\mathbf{r_1})
$$

Applying the original integral with an assumed known $f$ is then,

$$
     g(\mathbf{r_1}, \mathbf{v_1}d\mathbf{r_1}) = \int_{\mathbf{r} \neq \mathbf{r_1}} f(\mathbf{r})g(\mathbf{r} - \mathbf{r_1}, \mathbf{v_1}d\mathbf{r_1})d\mathbf{r} + f(\mathbf{r_1})\mathbf{v_1}d\mathbf{r_1}.
$$

where the integral contribution at the selected particle position $\mathbf{r_1}$ is written explicitly outside of the integral (known from the linear approximation to the Taylor expansion above) since $g$ is not defined there. Finally, note that this must be true for any choice of $\mathbf{v_1}d\mathbf{r_1}$ and that $g$ is linear in $\mathbf{v_i}d\mathbf{r_i}$ (eq \eqref{linear}), meaning that we can pull out a factor of $\mathbf{v_1}d\mathbf{r_1}$ for both instances of $g$ so that,

$$
     g(\mathbf{r_1}) = \int_{\mathbf{r} \neq \mathbf{r_1}} f(\mathbf{r})g(\mathbf{r} - \mathbf{r_1})d\mathbf{r} + f(\mathbf{r_1}).
$$

In modern symbols, the $g$ is actually just the total correlation between densities in volume elements of the system, which we write as $h$, and $f$ represents the direct coupling between volume elements, which we write as $c$. In modern symbols, the Ornstein-Zernike equation emerges,

$$ 
     h(\mathbf{r_1}) = \int_{\mathbf{r} \neq \mathbf{r_1}} c(\mathbf{r})h(\mathbf{r} - \mathbf{r_1})d\mathbf{r} + c(\mathbf{r_1}).
$$

### Physical Interpretation

What exactly does this equation mean? Starting with the total correlation function $h(\mathbf{r_1})$, we notice that this function is simply the average particle density of the system at position $\mathbf{r_1}$ within a spherical coordinate system,

\begin{figure}[H]
    \centering
    \includegraphics[width=0.5\linewidth]{geometry.png}
    \caption{The total correlation function, $h(\mathbf{r_1})$, is just the average density at any point in space away from the origin, $\mathcal{O}$.}
\end{figure}

According to the Ornstein-Zernike equation, this total correlation function is fully described by three functions: the direct correlation function $c(\mathbf{r_1})$, the direct correlation function $c(\mathbf{r})$, and the total correlation function $h(\mathbf{r - r_1})$. These functions only make sense when we consider that the integral will go over all of the other volume elements of the system, specifically for all $\mathbf{r} \neq \mathbf{r_1}$. Our new picture is then,

\begin{figure}[H]
    \centering
    \includegraphics[width=0.5\linewidth]{integral_geometry.png}
    \caption{The new vector $\mathbf{r}$ is of course integrated over all values of $\mathbf{r}$.}
\end{figure}

Now let's consider each of the terms. The direct correlation function $c(\mathbf{r_1})$ is a function of linear coupling constants which relate the particle density at the origin to all other volume elements in the system. There are no cross terms in the expansion, so this function only keeps track of the 'direct' coupling between volume elements, hence the name. $c(\mathbf{r_1})$ is therefore the direct coupling between the reference origin and some other volume element. The other direct correlation function $c(\mathbf{r})$ has the same interpretation, but now it represents the direct coupling between the reference and a different volume element not centered at $\mathbf{r_1}$. Finally, the total correlation $h(\mathbf{r - r_1})$ is just the density of a volume element from the reference volume element between the difference in the vectors $\mathbf{r - r_1}$. 

### Finite $f(\mathbf{r})$ Leads to Nonphysical Fourier Transforms

There are some problems with the mathematical development presented by Ornstein and Zernike. In a short phone call with Harry W. Sullivan, who just traveled to University of Minnesota to start a doctoral program, it was noted that the assumption of a cut-off in $c(\mathbf{r})$ may actually be at odds with Fourier representations of the total correlation function. To see this, consider that the modified Henkel transform (or spherical Bessel transform) of the real-space total correlation function is directly related to the total structure factor, a quantity  which is observable experimentally via scattering experiments. Thus, assuming that the total correlation function is isotropic, we can write the modified Henkel transform of the total correlation function as, 

$$
    \hat{h}(q) = \int_0^\infty h(r) J_r(qr)rdr
$$

where $J_r$ is the Bessel function of the first kind of order $r$. If there is a point at which the total correlation abruptly becomes zero at some $r_{max}$, then, expanding $h(r)$ in a Fourier Bessel series gives,

$$
    \hat{h}(q) = \int_0^{r_{max}} \sum_{n=1}^\infty c_n J_r\bigg(\frac{U_{r,n}}{r_{max}r}\bigg) J_r(qr)rdr
$$

where $c_n$ are constants and $U_{r,n}$ is the $n^{th}$ root of the Bessel function. The sum and integral can be exchanged since they are linear, giving the following,

$$
    \hat{h}(q) = \sum_{n=1}^\infty c_n \int_0^{r_{max}} J_r\bigg(\frac{U_{r,n}}{r_{max}r}\bigg) J_r(qr)rdr
$$

which has as a solution a delta-train,

$$
    \hat{h}(q) = \sum_{n=1}^\infty c_n \delta\bigg(\frac{U_{r,n}}{r_{max}} - q\bigg)\frac{r_{max}}{U_{r,n}}
$$

This result, of course, is at odds with experimental measurement of the total structure factor and with physical intuition of the problem. Hence, the abrupt sending of the function $c(\mathbf{r})$ to zero is not a mathematically reasonable assumption to describe the theory of liquids.

### Conclusions from Ornstein and Zernike's Original Work

In summary, Ornstein and Zernike's original paper is a work of genius that resulted in an integral relation that has remained relevant to liquid state physics for over a century. Indeed, reading this manuscript one gets the sense that the authors did not understand how monumental this work would become in the development of modern physics. However, the mathematical development in their manuscript is not rigorous and therefore encounters some potential pitfalls, but nonetheless was later verified to be correct anyway without the shaky assumptions that derail the extensibility of their method. 

## The Gibbs Interpretation

One of the great issues with Ornstein and Zernike's original derivation is that the direct correlation function is constructed with non-rigorous assumptions and doesn't have a physical interpretation. However, these deficiencies can be addressed with the statistical mechanics methods of Gibbs. First, recall that the phase space probability density, $f^{[N]}(\mathbf{r^N}, \mathbf{p^N}; t)$, is a function so that $f^{[N]}(\mathbf{r^N}, \mathbf{p^N}) d\mathbf{r^N}\mathbf{p^N}$ is the probability at time $t$ that the system will be in the $6N$-dimensional phase space element $d\mathbf{r^N}\mathbf{p^N}$. By defining a specific physical system, we can ascribe a functional form to this probability distribution. For instance, if  we take a collection of particles at equilibrium with a heat bath of fixed temperature but that cannot exchange particles, we obtain the canonical probability distribution,

$$
    f^{[N]}_0(\mathbf{r^N}, \mathbf{p^N}) \propto \frac{\exp(-\beta \mathcal{H})}{Q_N}
$$

where $Q_N$ is the familiar $N$-particle canonical partition function and the subscript of 0 for $f$ indicates that the system is at equilibrium and therefore does not depend on time. 

Generally, the $N$-particle phase space probability density function contains unnecessary information that can be integrated out to obtain so-called reduced phase space distribution functions in the following way,

$$
    f^{[n]}(\mathbf{r^n}, \mathbf{p^n}; t) = \frac{N!}{(N-n)!}\iint f^{[N]}(\mathbf{r^N}, \mathbf{p^N}) d\mathbf{r^{(N-n)}}d\mathbf{p^{(N-n)}}
$$

which has an obvious physical interpretation: $f^{[n]}(\mathbf{r^n}, \mathbf{p^n}; t)d\mathbf{r^{(N-n)}}d\mathbf{p^{(N-n)}}$ gives the probability of finding the system in a reduced phase space element $d\mathbf{r^{(N-n)}}d\mathbf{p^{(N-n)}}$ irrespective of all other particle positions and momenta. Now, in general this reduced phase space probability density at equilibrium is separable into kinetic and potential parts ($\mathcal{H} = \mathcal{K} + \mathcal{P}$) so that,

$$
    f^{[n]}(\mathbf{r^n}, \mathbf{p^n}) = \rho_N^{[n]}(\mathbf{r^n})f_M^{[n]}(\mathbf{p^n})
$$

where the $\rho_N^{[n]}(\mathbf{r^n})$ is the equilibrium $n$-particle density function so that  $\rho_N^{[n]}(\mathbf{r^n})d\mathbf{r^n}$ is the probability of finding a set of $n$ particles in reduced phase space volume element $d\mathbf{r^n}$ irrespective of the positions of all other particles and irrespective of all momenta. 

### Direct Correlations as Derivatives of Free Energy

The Gibbs interpretation offers us more mathematical rigor and precision that resolves many of the issues we have seen in Ornstein and Zernike's original manuscript. First, we will discuss the physical interpretation of the total correlation function in the Gibbs interpretation. Intuitively, the total correlation function, $h^{(2)}(\mathbf{r,r'})$, which appears in the OZ equation, describes the ensemble average distribution function of any two particle densities in the system. However, this quantity is defined in terms of the equilibrium $n$-particle density function in the following way,

$$
    g_N^{[n]}(\mathbf{r^N}) = \frac{\rho_N^{[n]}(\mathbf{r^n})}{\prod_{i=1}^n\rho_N^{[1]}(\mathbf{r_i})}
$$

which, for a reduced 2-particle density function, can be written as,

$$
    g_N^{[2]}(\mathbf{r_1},\mathbf{r_2}) = \frac{\rho_N^{[2]}(\mathbf{r_1},\mathbf{r_2})}{\rho_N^{[1]}(\mathbf{r_1})\rho_N^{[1]}(\mathbf{r_2})}
$$

and finally as our function,

$$
    h_N^{[2]}(\mathbf{r_1},\mathbf{r_2}) = g_N^{[2]}(\mathbf{r_1},\mathbf{r_2}) - 1
$$

Notice that this function is defined in terms of a 2-particle density function, which contains contributions from both individual particle densities and the intermediate particles as in our original picture from the Ornstein-Zernike manuscript. Notice we have completely avoided the difficulties of assuming that the density function is continuous (when in fact, it is not), since $h_N^{[2]}(\mathbf{r_1},\mathbf{r_2})$ is equally described by an ensemble average that is continuous for liquids at equilibrium.

So what of Ornstein and Zernike's coupling constant function, $f$, under the Gibbs interpretation? Perhaps surprisingly, $f$ is exactly equal to a second partial functional derivative of the excess free energy functional, $\mathcal{F}_{ex}[\rho^{(1)}]$ (recall that the excess part of the intrinsic free energy is just the contribution to the free energy due to particle interactions), so that,

$$
    c(\mathbf{r},\mathbf{r'}) = -\beta \frac{\delta^2 \mathcal{F}_{ex}[\rho^{(1)}]}{\delta \rho^{(1)}(\mathbf{r}) \delta \rho^{(1)}(\mathbf{r'})}
$$

Such a physical interpretation of the direct correlation is extremely satisfying for the following reasons. First, we see that indeed the direct correlation does not involve reduced particle density distributions higher than order 1, meaning that there is no contribution from intermediate particles (we had the same situation in Ornstein and Zernike's picture previously). However, now $c(\mathbf{r},\mathbf{r'})$ can be thought of as a response of the excess intrinisic free energy to changes in the single particle density distributions, rather than just the linear coupling terms of a truncated Taylor expansion. Such a construction does not require $c(\mathbf{r},\mathbf{r'})$ to abruptly vanish, resolving the issue with the modified Henkel transform in section \ref{FT}. Finally, we now see how $c(\mathbf{r},\mathbf{r'})$ could even be used to approximate the intrinsic free energy functional and hence describe entirely the thermodynamics of a model fluid. 

### The OZ Equation in the Gibbs Interpretation

See Section 3.5 of \textit{Theory of Simple Liquids} by Hansen and McDonald. 

## Numerical Implementations

### The Isotropic OZ Relation and the Bridge Function

In practice, we usually consider liquids to be isotropic, allowing us to reduce the vector quantities introduced earlier into just the distance between particles, $r$, to give an isotropic Ornstein-Zernike relation,

$$
    h(r) = c(r) + \rho \int c(|\mathbf{r} - \mathbf{r'}|)h(r')d \mathbf{r'}
$$

which you may notice is just a convolution of $h(r')$ with $c(|\mathbf{r} - \mathbf{r'}|)$,

$$
    h(r) = c(r) + \rho [h(r')*c(|\mathbf{r} - \mathbf{r'}|)]\mathbf{r}
$$

which under Fourier transform is simply,

$$
    \hat{h}(q) = \hat{c}(q) + \rho \hat{h}(k) \hat{c}(k)
$$

or rearranging, 

$$
    \hat{h}(q) = \frac{\hat{c}(q)}{1-\rho \hat{c}(q)}
$$

Finally, diagrammatic techniques (see \textit{A Concise Course on the Theory of Classical Liquids} by Santos and Section \ref{diagrams}) and the introduction of the indirect correlation function ($\gamma(r) = h(r) - c(r)$), allow us to write the radial distribution as,

$$
    g(r) = \exp[-\beta u(r) + h(r) - c(r) + b(r)]
$$

where $b(r)$ is the so-called, and unkown to us, bridge function arising from elementary diagrams in the integral expansion of $g(r)$. Using the definition of the indirect correlation, we find that,

$$
    g(r) = \exp[-\beta u(r) + \gamma(r) + b(r)]
$$

Noting that $h(r) = g(r) - 1$, we can subtract the direct correlation $c(r)$ from both sides of the equation to obtain,

$$
    h(r) - c(r) = g(r) - 1 - c(r)
$$

and using the definition of the indirect correlation and the diagram expansion of $g(r)$,

$$
    \gamma(r) = \exp[-\beta u(r) + \gamma(r) + b(r)] - 1 - c(r)
$$

which, upon rearranging, gives,

$$
    c(r) = \exp[-\beta u(r) + \gamma(r) + b(r)] - \gamma(r) - 1
$$

Here a closure relation is introduced to write $b(r)$ in terms of the indirect correlation function. Specific examples will be provided in section \ref{numerical}.

#### OZ Fourier Transform in Terms of the Indirect Correlation

In terms of the indirect correlation, the OZ equation becomes,

$$
    \gamma(r) = \rho [(\gamma(r) + c(r))*c(|\mathbf{r} - \mathbf{r'}|)] \mathbf{r}
$$

which, upon taking the Fourier transform, gives,

$$
    \hat{\gamma}(q) = \rho (\hat{\gamma}(q) + \hat{c}(q))(\hat{c}(q)) = \rho \hat{\gamma}(q) \hat{c}(q) + \rho \hat{c}^2(q)
$$

and rearranging,

$$
    \hat{\gamma}(q) = \frac{\rho \hat{c}^2(q)}{1 - \rho \hat{c}(q)}
$$

### Iterative Numerical Solvers

We now have everything we need to solve for the pair correlation function $h(r)$, given a potential. The steps we use are:

\begin{enumerate}
    \item Guess the indirect correlation function $\gamma(r)$.
    \item Compute the direct correlation function, $c(r)$, using eq \eqref{diagdirect} and a suitable closure relation for the bridge function.
    \item Fourier transform $c(q)$.
    \item Compute Fourier transform of the indirect correlation, $\hat{\gamma}(q)$, using eq \eqref{indirectOZ}.
    \item Fourier transform $\hat{\gamma}(q)$ to get a new guess for $\gamma(r)$.
    \item Repeat until convergence.
\end{enumerate}

Now, what if we have the total correlation function from experiment but do not know the potential? In this case, we change the algorithm as follows:

\begin{enumerate}
    \item Guess the pair potential $\beta u^{(0)}(r)$.
    \item Compute the direct correlation function, $c(r)$, using eq \eqref{diagdirect} and a suitable closure relation for the bridge function.
    \item Fourier transform $c(r)$.
    \item Compute Fourier transform of the total correlation, $\hat{h}(q)$, using eq \eqref{OZFT}.
    \item Fourier transform $\hat{h}(q)$ to get $h(r)$.
    \item Perform iterative refinement scheme to update potential to $\beta u^{(1)}(r)$.
    \item Repeat until the computed $h(r)$ matches the experimental data.
\end{enumerate}
