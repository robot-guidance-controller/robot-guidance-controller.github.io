---
layout: page
title: Controller
permalink: /controller/
---

## Control Diagram

<figure>
    <img src="/assets/images/figures/guidance_controller_low_level_no_residual.png" alt="Block Diagram" width="100%">
    <figcaption style="text-align: center;"><br/>Control loop of our Robot Guidance Controller. The diagram illustrates how position and velocity tracking errors ($e$, $\dot{e}$) are processed through parallel physical and verbal PD controllers with dedicated gain parameters ($K_p$, $B_p$, $K_v$, $B_v$). The optimization method ($J$) uses compliance estimates to determine appropriate variable admittance gains ($A_p$, $A_v$) that modulate the physical guidance control input ($U_p$) and verbal guidance control input ($U_v$). These gains continuously adapt to the variable human impedance ($Z_h$) and human cognitive reaction ($\mathcal{H}$), with verbal inputs converted to instructional utterances ($\sigma$) through a Force-to-Language (F2L) model that accounts for varying levels of human receptiveness.</figcaption>
</figure>

## Algorithm

**Algorithm: Robot Guidance Controller**

**Inputs:**

$$
\gamma \quad \text{(Reference trajectory)}
$$

$$
(K_p, B_p, K_v, B_v) \quad \text{(Control gains)}
$$

$$
(M, B) \quad \text{(Robot dynamics)}
$$

**Outputs:**

$$
U_p \quad \text{(Physical guidance)}, \quad \sigma \quad \text{(Verbal utterance)}
$$

**Loop while task not complete:**

1. *Measurement Phase*

   $$
   x(t), \quad \dot{x}(t) \quad \text{(Measure pose and velocity)}
   $$

   $$
   F_h(t) \quad \text{(Measure human interaction force)}
   $$

2. *Reference Projection*

   $$
   s^*(t) \leftarrow \arg\min_s \|x(t) - \gamma(s)\|
   $$

   $$
   x_{\text{ref}}(t) \leftarrow \gamma(s^*(t))
   $$

   $$
   \dot{x}_{\text{ref}}(t) \leftarrow \gamma'(s^*(t))
   $$

3. *Tracking Error*

   $$
   e(t) \leftarrow x_{\text{ref}}(t) - x(t)
   $$

   $$
   \dot{e}(t) \leftarrow \dot{x}_{\text{ref}}(t) - \dot{x}(t)
   $$

4. *Compliance Estimation*

   $$
   z_t \leftarrow \begin{bmatrix} e(t) \\ \dot{e}(t) \end{bmatrix}
   $$

   Update belief $\pi_t$ via Bayesian filter

   $$
   \hat{P}_t \leftarrow \pi_{10,t} + \pi_{11,t}
   $$

   $$
   \hat{V}_t \leftarrow \pi_{01,t} + \pi_{11,t}
   $$

5. *Cost Computation*

   $$
   c_p(t) \leftarrow \frac{1}{2}(\hat{P}_t + \hat{V}_t)
   $$

   $$
   c_v(t) \leftarrow 1 - \hat{V}_t
   $$

6. *Weight Allocation*

   $$
   A_p^*(t) \leftarrow \frac{c_v(t)}{c_p(t) + c_v(t)}
   $$

   $$
   A_v^*(t) \leftarrow \frac{c_p(t)}{c_p(t) + c_v(t)}
   $$

7. *Control Laws*

   $$
   U_p(t) \leftarrow K_p e + B_p \dot{e} - A_p^* F_h
   $$

   $$
   U_v(t) \leftarrow K_v e + B_v \dot{e} - A_v^* F_h
   $$

8. *Force-to-Language*

   $$
   \mathbf{u}_v \quad \text{(Compute over horizon } T \text{)}
   $$

   $$
   \sigma \leftarrow \Psi(\mathbf{u}_v)
   $$

9. *Actuation*

   $$
   \text{Apply } U_p \text{ to robot}
   $$

   $$
   \text{Speak utterance } \sigma
   $$

   $$
   M \ddot{x} + B \dot{x} = U_p + F_h
   $$