---
layout: page
title: research
permalink: /research/
description: What I work on, how I got here, and where I want to go next.
nav: true
nav_order: 2
---

<p class="lead-text">I'm interested in how robots can learn control from data rather than having it hand-tuned, through imitation and reinforcement learning, and world models that let them plan.</p>

## Background

I studied Electrical Engineering at the University of Belgrade (ETF), in the Signals and Systems track (GPA 9.11/10). That gave me a classical foundation for robotics: control systems, system identification, stochastic estimation, robotics and autonomous mobile robots, and neural networks. I'm now in the [MVA master's](https://www.master-mva.com/) at ENS Paris-Saclay as a French Government (BGF) scholar.

## Why robot learning

What pulled me into robot learning was seeing how controllers for precise tasks are tuned by hand: a slow, painstaking process that has to be repeated for every new task. A controller that is _learned_ from data instead, and that can generalize to long-horizon tasks and adapt from one task to the next, struck me as far more powerful. That is still the question behind my work.

## Learning a precise insertion task

At the [ETF Robotics Laboratory](https://robot.etf.bg.ac.rs/en-gb/team/) (advisor: Prof. Kosta Jovanović) I worked on our entry to the [Intrinsic AI for Industry Challenge](https://www.intrinsic.ai/events/ai-for-industry-challenge): teaching a UR5e arm to insert fiber-optic connectors. I developed imitation- and reinforcement-learning policies in NVIDIA Isaac Lab, built the scenes in OpenUSD, and set up a containerized ROS 2 / Gazebo environment to carry policies toward the real robot.

<a class="more-link" href="{{ '/projects/2_aic/' | relative_url }}">Project page →</a>

## What more data does, and doesn't, fix

My BSc thesis asked a simple question: how far can imitation learning go on a task that needs millimetre precision? I generated 30,290 expert demonstrations and trained ACT and Diffusion Policy at 1k, 10k and 30k demos.

- The main obstacle is **lateral error**: the sideways misalignment with the port.
- More data helps a lot: Diffusion Policy's median lateral error dropped **3.5×** (41.2 → 11.8 mm), but that is still far from the millimetre precision the insertion requires.

<a class="more-link" href="{{ '/projects/1_il_limits/' | relative_url }}">Project page →</a>

## A model that imagines the effect of actions

At PSIML 2026 I approached the problem from another side: instead of a policy, a **world model**. I fine-tuned a pretrained video diffusion model (Wan2.1, 1.3B) with LoRA so that it follows commanded robot actions on the BAIR dataset. On 256 held-out scenes it moves the arm in the commanded direction 84.8% of the time, and the action signal alone is worth +5.29 dB PSNR.

<a class="more-link" href="{{ '/projects/3_world_model/' | relative_url }}">Project page →</a>

## Model-based control

On the classical side, I'm working toward a Panda that plays with a ping-pong ball, starting with intercepting a thrown ball. A MoveIt baseline in Gazebo already reaches within 1–2 cm of the predicted contact point, but too slowly for the ball's flight, so I'm building a nonlinear MPC that times the paddle to the ball's arrival (in progress).

<a class="more-link" href="{{ '/projects/4_juggling/' | relative_url }}">Project page →</a>

## What's next

Two directions interest me most right now.

- **RL fine-tuning of imitation-learned policies.** My thesis showed that more demonstrations reduce lateral error, but not enough for insertion; that last stretch is exactly where interaction and reward should help.
- **World models for planning.** At PSIML I saw that a video model can learn to respect robot actions. The next step is to use such a model to imagine outcomes and plan before acting.

I'm looking for a **research internship starting in spring 2027** to work on these questions. Feel free to [reach out](mailto:mihastevanovic04@gmail.com).
