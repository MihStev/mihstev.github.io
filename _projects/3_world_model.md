---
layout: page
title: Action-conditioned video world model
description: PSIML 2026 · teaching a video diffusion model to follow robot actions on BAIR
importance: 3
category: research
---

**PSIML — Practical Seminar in Machine Learning, Aug 2026.** [Code](https://github.com/MihStev/PSIML)

Given a few frames of a scene and a commanded gripper motion, can a pretrained video model predict the future **and** make the arm move the way it was told?

I fine-tuned **Wan2.1-T2V-1.3B** (via [minWM](https://github.com/shengshu-ai/minWM)) with **LoRA** and a learned action encoder on the BAIR robot-pushing dataset. The upstream model conditions on camera pose; conditioning on robot actions was the new part. It took 5 days on one shared A100.

**Results on 256 held-out scenes:**

- **84.8%** direction accuracy: in 84.8% of cases the gripper moves in the direction it was commanded.
- The action signal alone is worth **+5.29 dB PSNR** (real action vs. a learned null action). A deliberately wrong action scores below the null one, so the model really uses the action.
- Fine-tuning does not undo DMD distillation: 4-step sampling keeps the same direction accuracy as 24 steps.
