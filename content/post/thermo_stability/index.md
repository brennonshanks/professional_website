---
title: Thermodynamic Stability Criterion
date: 2023-07-14T05:53:47.038Z
draft: false
featured: false
authors:
  - admin
tags:
  - thermodynamics
image:
  filename: ""
  focal_point: Smart
  preview_only: false
---

The thermodynamic requirement that the second derivative of energy be positive gives rise to some interesting results on thermodynamic system stability. To see this, let's first construct an intrinsic system and a complimentary subsystem from a composite, isolated system. The complimentary subsystem is assumed to be much larger than the intrinsic subsystem.  The fundamental relation is given by,

$$
    U' = X_t u (x_0, x_1, ..., x_{t-1}) + \tilde{X_t}  \tilde{u} (\tilde{x_0}, \tilde{x_1}, ..., \tilde{x_{t-1}})
$$

where $X_t$ represents some parameter of the fundamental relation that is being held constant. Furthermore, the smallness of the intrinsic system compared to the complementary system requires that,

$$
    |d\tilde{x}_i| << |dx_i|
$$

Now, any changes in the $x_i$ leads to a total change in energy. We can express the energy change in terms of a Taylor expansion such that, 

$$
   \Delta U' = X_t[du + d^2u + ...] + \tilde{X}_t d \tilde{u}
$$

where,

$$
    du = \sum_{i}\frac{\partial u}{\partial x_i}dx_i
$$

$$
    d^2u = \frac{1}{2!}\sum_{j}\sum_{i}\frac{\partial^2 u}{\partial x_i\partial x_j}dx_idx_j
$$

We can neglect higher order terms of $\tilde{u}$ since we are assuming that the changes in the independent variables are very small for the complimentary system. Now, since the composite system is isolated, the change in internal energy for the composite system vanishes,

$$
    0 = X_t\sum_{i}\frac{\partial u}{\partial x_i}dx_i + \tilde{X_t}\sum_{i}\frac{\partial \tilde{u}}{\partial \tilde{x_i}}d \tilde{x_i}
$$

This leads us to the usual results that all of the intensive parameters (T, P, $\mu_i$) are the same in each subsystem at equilibrium. In other words, the composite system is homogeneous. However, we now turn our attention to the second requirement; namely, 

$$
    d^2u = \frac{1}{2!}\left[\sum_{0}^{t-1}\sum_{0}^{t-1}\frac{\partial^2 u}{\partial x_i\partial x_j}dx_idx_j\right] > 0
$$

The quantity in brackets is known as the homogeneous quadratic form. The condition that the quadratic form be positive for all combinations of variables is referred to mathematically as the condition that the quadratic form be positive definite. Notice that we have numerous cross terms in the expression for $d^2u$. The presence of these cross terms make it difficult to determine what quantities must be positive, so we need to perform a linear transformation such that the quadratic form is a sum of squares. Sylvester's law of inertia guarantees that no matter which transformation we pick, the number of positive, negative, and zero coefficients will be the same.

For this discussion, we will proceed by considering terms that contain $dx_0$. We can thus express the equation as, 

$$
    d^2u = \frac{1}{2}\left[u_{00}^2(dx_0)^2 + +2\sum_{1}^{t-1}\frac{\partial^2 u}{\partial x_0\partial x_k}dx_0dx_k+ \sum_{1}^{t-1}\sum_{1}^{t-1}\frac{\partial^2 u}{\partial x_i\partial x_j}dx_idx_j\right] > 0
$$

We now eliminate the cross terms by introducing the new variable, $dP_0$.

$$
    dP_0 = u_{00}dx_0 + \sum_{1}^{t-1}u_{0k}dx_k
$$

$$
    (dP_0)^2 = u_{00}^2(dx_0)^2 + 2 u_{00}\sum_{1}^{t-1}u_{0k}dx_k+\sum_{1}^{t-1}\sum_{1}^{t-1}u_{0j}u_{0k}dx_jdx_k
$$

which allows us to express the second derivative of internal energy as, 

$$
    d^2u = \frac{1}{2}\left[\frac{1}{u_{00}}(dP_0)^2+ \sum_{1}^{t-1}\sum_{1}^{t-1}(u_{jk}-\frac{u_{0j}u_{0k}}{u_{00}})dx_jdx_k\right] > 0
$$

Now, notice that the previous equation can be rewritten as, 

$$
    d^2u = \frac{1}{2}\left[\frac{1}{u_{00}}(dP_0)^2+ \sum_{1}^{t-1}\sum_{1}^{t-1}(u_{jk})_{P_0, x_1, x_2, ...}dx_jdx_k\right] > 0
$$

We can rewrite this expression in a helpful way. Consider the following mathematical expression, 

$$
    \bigg(u_{jk}-\frac{u_{0j}u_{0k}}{u_{00}}\bigg) = \bigg(\frac{\partial^2 (u - P_0x_0)}{\partial x_j \partial x_k}\bigg)_{P_0, x_1, ...} = \frac{\partial^2 \psi^{(0)}}{\partial x_j \partial x_k}
$$

The function $\psi^{(0)}$ is the Legendre transform of u with respect to $P_0$. This allows us to now write the second derivative of u as, 

$$
    d^2u = \frac{1}{2}\left[\frac{1}{u_{00}}(dP_0)^2+ \sum_{1}^{t-1}\sum_{1}^{t-1}\psi_{jk}^{(0)}dx_jdx_k\right] > 0
$$

Proceeding in this way, for each of the $dx_i$, we arrive at a useful form given by,

$$
    d^2u = \frac{1}{2}\sum_{0}^{t-1}\frac{1}{\psi_{jj}^{(j-1)}}(dP_j^{(j-1)})^2 > 0
$$

Thus, we require that all of the $\psi_{jj}^{(j-1)}$ be positive such that,

$$
    \psi_{jj}^{(j-1)} = \bigg(\frac{\partial P_j}{\partial x_j}\bigg) > 0 
$$

at constant ${P_{0}, P_{1} ... P_{j-1},x_{j+1},x_{j+2}...x_{t-1}}$. So, what exactly does this mean? Common terms that must be positive according to this definition are,

$$
    -\bigg(\frac{\partial P}{\partial V}\bigg)_T > 0
$$

$$
     \bigg(\frac{\partial U}{\partial T}\bigg)_v = C_v > 0
$$

Of course, depending on the complexity of the system, we can have many more relations from this procedure. However, in fluid phase transitions, we are typically most concerned with the first of the two explicit equations and the second is just assumed to be true.
