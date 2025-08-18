---
layout: post
title: Flow Models
description: A comprehensive guide to understanding flow-based generative models, from continuity equations to probability paths and velocity fields.
date: 2025-08-11 16:40:16
tags: ComputerVision GenerativeAI
image: img/postbanners/2024-08-07-convert-datetime2-bigint.png
---

# Flow-Based Generative Models: 




<div style="display: flex; justify-content: space-between; align-items: center;">
    <a href="https://drive.google.com/file/d/11Rmquzpulf07s06CG1OfKqNgLrnMjR6k/view?usp=sharing">
        <img src="https://drive.google.com/thumbnail?id=11Rmquzpulf07s06CG1OfKqNgLrnMjR6k&sz=w1000" 
             alt="Flow Animation Left" style="max-width: 100%; height: auto; width: 450px;">
    </a>
    <a href="https://drive.google.com/file/d/1x1nUElOeEfXv_6_Q2IulX-1HU7A54Gl8/view?usp=sharing">
        <img src="https://drive.google.com/thumbnail?id=1x1nUElOeEfXv_6_Q2IulX-1HU7A54Gl8&sz=w1000" 
             alt="Flow Animation Right" style="max-width: 100%; height: auto; width: 450px;">
    </a>
</div>





<!-- <div align="center">
    <a href="https://drive.google.com/file/d/1repEITw0AkNDYHVH489ikjR78YQ6QZXE/view?usp=sharing">
        <img src="https://drive.google.com/thumbnail?id=1repEITw0AkNDYHVH489ikjR78YQ6QZXE&sz=w1000" alt="ECCV Workshop Picture" style="max-width: 100%; height: auto;">
    </a>
</div>
 -->












Imagine a cloud of particles drifting through space. At first, this cloud looks like random Gaussian noise. As time flows, the cloud reshapes itself, stretching and bending, until finally it resembles the distribution of real-world data we want to generate.  

How can we describe this transformation mathematically? The answer begins with the **continuity equation**.

---

## The Continuity Equation: Conserving Probability

Probability mass behaves like an incompressible fluid — it cannot just vanish or be created from nothing. The way it moves is governed by the **continuity equation**:

$$
\frac{\partial}{\partial t} p_t(x) + \nabla_x \cdot \big( p_t(x) \, u_t(x) \big) = 0.
$$

Here:
- $p_t(x)$ is the probability density at time $t$,
- $u_t(x)$ is the **velocity field** describing how points at $x$ move,
- $\nabla_x \cdot$ is the divergence operator, capturing how mass flows in or out of a region.

👉 Intuitively, this says: *if probability density decreases at some point $x$, it must be because the density is flowing away, carried along by the velocity field $u_t(x)$.*  

This law of conservation is the backbone of all flow-based models.

---

## The Probability Path: Watching Distributions Evolve

Now let’s step back. We want to morph a simple distribution (like Gaussian noise) into a complicated data distribution (like natural images). To describe this morphing, we introduce the idea of a **probability path**:

$$
\{ p_t(x) \}_{t \in [0,1]}, \quad p_0(x) = p_\text{source}(x), \; p_1(x) = p_\text{target}(x).
$$

This path is just a smooth sequence of probability densities indexed by time $t$.  

- At $t=0$, the distribution is pure noise.  
- At $t=1$, it has become the target data distribution.  
- For values of $t$ in between, we see the intermediate “shapes” of the distribution.  

Think of it as a movie of the distribution continuously warping from one form into another.

---

## The Velocity Field: Moving Individual Particles

While the probability path describes how the whole distribution changes, we also want to describe how **individual particles** move inside this evolving cloud. That’s where the **velocity field** $u_t(x)$ comes in.

For a single particle trajectory $X_t$:

$$
\frac{d}{dt} X_t = u_t(X_t).
$$

This equation tells us that if a particle is at position $X_t$ at time $t$, its next step is determined by the velocity field at that point.  

👉 So, the velocity field is the “microscopic rule” that, when applied to all particles, produces the macroscopic evolution of the probability distribution.

---

## The Flow: A Global Transformation

If we follow each particle’s trajectory over time, we get a **flow map**:

$$
\Phi_t : x_0 \mapsto x_t,
$$

where $\Phi_t$ is the solution of the ODE:

$$
\frac{d}{dt} x_t = u_t(x_t), \quad x_0 \sim p_0.
$$

This map $\Phi_t$ tells us how to transport an initial sample $x_0$ (from the source distribution) into a new point $x_t$ at time $t$.  

- The **flow of particles** created by this map gives rise to  
- The **flow of probability densities** $p_t(x)$ described earlier.  

The continuity equation ensures the two views (microscopic particles and macroscopic densities) stay perfectly in sync.

---

## Putting It All Together

Here’s the full picture:

1. The **continuity equation** guarantees probability mass is conserved:
   $$
   \frac{\partial}{\partial t} p_t(x) = -\nabla_x \cdot \big(p_t(x) u_t(x)\big).
   $$

2. The **velocity field** $u_t(x)$ determines how individual samples move:
   $$
   \frac{d}{dt} X_t = u_t(X_t).
   $$

3. Following these trajectories defines the **flow** $\Phi_t$ that maps the source distribution into the target:
   $$
   \{X_t\}_{t \in [0,1]} \;\;\Rightarrow\;\; \{p_t(x)\}_{t \in [0,1]}.
   $$

In simple words:  
- The **probability path** shows how distributions change in time.  
- The **velocity field** shows how points move in time.  
- The **flow** is the overall transformation carrying one distribution into another.  
- And the **continuity equation** is the glue that ensures consistency between them.

---

With this story, we’ve built the mathematical foundation for flow-based generative models: they are nothing more than learning the right velocity field $u_t(x)$ so that the flow transforms Gaussian noise into real data.




## Code Part