---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page
title: Robot Guidance Controller
permalink: /
---

When human instructors guide learners through motor tasks, they seamlessly coordinate physical touch with verbal explanations - a dance teacher positions a student's arms while describing the movement, a therapist supports a patient's limb while offering encouragement. In contrast, a robot applying physical forces without verbal context can feel invasive or unsettling to humans. We present a robot guidance controller that learns to coordinate physical and verbal guidance as human instructors naturally do. Our system adaptively balances these modalities based on real-time estimation of human compliance: when learners struggle, it provides firmer physical corrections with explicit instructions; as they improve, it transitions to lighter touch with encouraging phrases. Our method  comprises three components: (1) an estimator that infers physical and verbal compliance from tracking errors, (2) an optimization method that dynamically allocates guidance between force and language, and (3) a force-to-language model that generates contextually appropriate utterances. User studies (N=12) demonstrate that adaptive coordination significantly outperforms single-modality and fixed-combination baselines: 32% reduction in tracking error, 28% improvement in movement smoothness, and 19\% faster task completion. While validated in rehabilitation therapy, our approach generalizes to any human-robot collaborative learning scenario.

## System Architecture

<figure>
    <img src="/assets/images/figures/main_figure.png" alt="Main Figure" width="100%">
    <figcaption style="text-align: center;"><br/>Visual summary of the Robot Guidance Controller for optimal physical and verbal guidance. Expert-led demonstrations generate reference trajectories, and inform module design and parameters. The Trajectory Planner outputs desired motion, while a Bayesian Compliance Estimator infers human receptiveness to different guidance modalities in real time. Based on these estimates, the Optimization Method dynamically allocates guidance effort between physical forces and verbal instructions. The Robot Guidance Controller enables a closed-loop feedback system that provides contextually appropriate, multimodal guidance, enabling real-time adaptive human-robot interaction.</figcaption>
</figure>

## Results

<strong>Our method achieves superior task completion than the simple baseline method:</strong>

<figure>
    <img src="/assets/images/figures/results_overall_B1_vs_ours.png" alt="Results Overall Baseline 1 vs. Our Method" width="100%">
    <figcaption style="text-align: center;"><br/></figcaption>
</figure>

<strong>We show multimodal (physical and verbal) guidance outperforms unimodal (physical or verbal) guidance:</strong>

<figure>
    <img src="/assets/images/figures/results_overall_B1.png" alt="Results Overall Single Mode vs. Multimodal Guidance" width="100%">
    <figcaption style="text-align: center;"><br/></figcaption>
</figure>

<strong>A snippet deep diving into the real-time interaction between a user and our method:</strong>

<figure>
    <img src="/assets/images/figures/example_ours.png" alt="Single User Using Our Method Deep Dive Example" width="100%">
    <figcaption style="text-align: center;"><br/></figcaption>
</figure>

## Code

Refer to the [Robot Guidance Controller repository](https://github.com/robot-guidance-controller/robot-guidance-controller) for the codebase of our controller.