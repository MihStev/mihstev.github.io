---
layout: page
title: Limits of imitation learning for high-precision insertion
description: BSc thesis · ACT and Diffusion Policy on 30k simulated demos (UR5e, Isaac Lab)
importance: 1
category: research
---

**BSc thesis, ETF Robotics Laboratory, University of Belgrade (2026). Advisor: Prof. Kosta Jovanović.**
[Code](https://github.com/etf-robotics/etf_robotics_aic) ·
[Policies on Hugging Face](https://huggingface.co/Mihajlo04/aic-port-insertion-policies) ·
[Eval results](https://huggingface.co/datasets/Mihajlo04/aic-port-insertion-eval)

How far can imitation learning go on a task that needs millimetre precision? I studied this on fiber-optic (SFP) connector insertion with a UR5e arm in NVIDIA Isaac Lab.

- Built the task environment (`AIC-Port-Insertion-v0`) and a scripted oracle that generated **30,290 successful expert demonstrations**.
- Trained **ACT** and **Diffusion Policy** (LeRobot) with an auxiliary phase-prediction head, at 1k, 10k and 30k demonstrations.
- Evaluated closed-loop over 150 episodes per policy, with automatic failure classification.

**Findings.** The main obstacle is **lateral error**, the sideways misalignment with the port. More data helps a lot: Diffusion Policy's median lateral error dropped **3.5×** (41.2 → 11.8 mm), but that is still far from the millimetre precision the insertion requires.

<div class="row justify-content-sm-center">
  <div class="col-sm-10 mt-3 mt-md-0">
    <div style="aspect-ratio: 16 / 9;">
      <iframe src="https://www.youtube-nocookie.com/embed/SS5MC-dcSX4" title="Successful Diffusion Policy episode" style="width:100%;height:100%;border:0;" allowfullscreen></iframe>
    </div>
  </div>
</div>
<div class="caption">A successful Diffusion Policy episode.</div>
