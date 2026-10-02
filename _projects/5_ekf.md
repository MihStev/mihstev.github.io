---
layout: page
title: EKF localization with lidar features
description: ROS 2 · TurtleBot3 · own split-and-merge line extraction
importance: 5
category: coursework
---

**Autonomous Mobile Robots, ETF Belgrade, spring 2026.**
[Line extraction code](https://github.com/MihStev/ROS2/tree/main/TurtleBot3-Split-And-Merge)

A real-time ROS 2 **extended Kalman filter** that fuses wheel odometry with line features extracted from lidar scans. I implemented split-and-merge line extraction and Mahalanobis-gated data association. A waypoint-following loop runs on the estimate, evaluated against Gazebo ground truth.
