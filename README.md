# Distributionally Robust Stochastic Gatekeeper


Modern autonomous systems often rely on high-performance controllers and learned policies that can fail under uncertainty, model mismatch, or distributional shift. While existing safety filters can provide guarantees under idealized assumptions, many become overly conservative, computationally intractable, or unsafe when the true disturbance distribution differs from the nominal one.

This project introduces **Distributionally Robust Stochastic Gatekeeper (DRS-gatekeeper)**, a sampling-based safety filter designed to provide **probabilistic safety guarantees for any nonlinear systems under arbitrary uncertainty structure and uncertain distribution**.

Instead of enforcing safety through restrictive analytic assumptions or local approximations, DRS-gatekeeper evaluates the future behavior of a system through stochastic rollouts and computes a safe switching time between:

- a **high-performance nominal policy**, and
- a **pre-certified backup policy**.

The method explicitly accounts for **distribution shift** using Wasserstein ambiguity sets, enabling robust safety guarantees even when the observed disturbances differ from the true underlying environment.

---

## Key Features

- **Distributionally Robust Safety**
  - Handles uncertainty beyond the empirical data distribution using Wasserstein ambiguity sets.

- **Sampling-Based Verification**
  - Avoids expensive nonlinear optimization and supports arbitrary nonlinear dynamics.

- **Minimal Intervention**
  - Allows the nominal controller to operate whenever safely possible.

- **Scalable to Complex Systems**
  - Applicable to high-dimensional systems including autonomous racing and aircraft control.

- **Provable Guarantees**
  - Provides probabilistic safety guarantees with finite-sample confidence bounds.

---

## Method Summary

At every control step, DRS-gatekeeper:

1. Samples stochastic future rollouts under uncertainty.
2. Evaluates candidate switching times between the nominal and backup controller.
3. Estimates worst-case failure probabilities under distributional ambiguity.
4. Selects the latest safe switching time that satisfies the desired safety level.

This enables the system to remain both:
- **safe under uncertainty**, and
- **high-performance whenever possible**.

---

## Why This Matters

Safety-critical systems frequently operate in environments where:
- disturbances are difficult to model,
- sensor noise changes over time,
- dynamics are imperfectly known,
- and real-world conditions differ from training data.

DRS-gatekeeper is designed to remain reliable even when these assumptions fail.

This makes the framework particularly relevant for:
- autonomous driving,
- robotics,
- aerospace systems,
- learned control policies,
- and real-world deployment of AI-enabled autonomy.

---

## Simulation Environments

The framework has been evaluated across systems of increasing complexity, including:

- **Dubins Vehicle**
  - Obstacle avoidance under uncertain actuation and model mismatch.

- **Formula 1 Racecar**
  - High-speed autonomous racing under empirical disturbances and perception noise.
  - Nominal policy - uses Model Predictive Path Integral (MPPI) from the [paper](https://ieeexplore.ieee.org/document/8558663)


- **F-16 Fighter Jet**
  - Low-altitude canyon flight with nonlinear aircraft dynamics and aerodynamic uncertainty.

---

# Simulation Videos

> Videos will be added soon.

## Dubins Vehicle

<div style="display: flex; gap: 20px;">

<div style="text-align:center">
<b>mppi</b><br>
<video width="400" controls>
  <source src="mppi.mp4" type="video/mp4">
</video>
</div>

<div style="text-align:center">
<b>ours</b><br>
<video width="400" controls>
  <source src="ours.mp4" type="video/mp4">
</video>
</div>

</div>

---

## Formula 1 Racecar

<div style="display: flex; gap: 20px;">

<div style="text-align:center">
<b>MPPI</b><br>
  <img src="https://github.com/user-attachments/assets/53153f02-e6bb-4efa-af1d-6f0d17105df3"width="400">
</div>

<div style="text-align:center">
<b>Ours</b><br>
  <img src="https://github.com/user-attachments/assets/30c0d701-5119-4edb-b5e3-b4f55c6b385f"width="400">
</div>
</div>

---

## F-16 Fighter Jet

<div style="display: flex; gap: 20px;">

<div style="text-align:center">
<b>mppi</b><br>
<video width="400" controls>
  <source src="mppi.mp4" type="video/mp4">
</video>
</div>

<div style="text-align:center">
<b>ours</b><br>
<video width="400" controls>
  <source src="ours.mp4" type="video/mp4">
</video>
</div>

</div>

---

## Code
The codebase will be released publicly upon acceptance of the paper.

