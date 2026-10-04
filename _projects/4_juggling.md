---
layout: page
title: "Robotic table tennis: intercepting a thrown ball with a Franka Panda"
description: In progress · MoveIt baseline in Gazebo, nonlinear MPC under development (ROS 1, CasADi, acados)
importance: 4
category: research
---

**ETF Robotics Laboratory, Aug 2026 – ongoing.** Franka Emika Panda (7-DoF), ROS 1 Noetic, Gazebo 11, MoveIt, `franka_ros`, CasADi, acados.

The long-term goal is a Panda that juggles a ping-pong ball. The current stage is the prerequisite: intercepting a thrown ball with a paddle.

- Built the Gazebo setup on the same `franka_ros` control interfaces as the real robot: a CAD-derived paddle end-effector, a ball model calibrated to real rebound (30 cm drop → 24.5 cm), and a ball launcher.
- A MoveIt-based interceptor reaches within 1–2 cm of the predicted contact point, but too slowly: execution takes 1.4–3.3 s against a ~0.5–1.8 s ball flight.
- That timing gap is why I'm now building a **nonlinear MPC** (CasADi/IPOPT, acados) that plans joint trajectories against the paddle's real striking surface and the ball's predicted arrival time.
