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

<strong>We show multimodal (physical and verbal) guidance outperforms unimodal (physical or verbal) guidance:</strong>

<figure>
    <img src="/assets/images/figures/results_overall_B1.png" alt="Results Overall Single Mode vs. Multimodal Guidance" width="100%">
    <figcaption style="text-align: center;"><br/>Performance of verbal-only (green), physical-only (blue), and combined guidance (orange) across varying compliance regimes. Each subplot shows a different evaluation metric: position error (top left), velocity error (top right), velocity smoothness (bottom left), and task completion time (bottom right). Bars are grouped by compliance condition: single-modality conditions (first and second clusters) and combined-modality conditions under all four combinations of physical (P) and verbal (V) compliance (third cluster). Error bars indicate 95\% confidence intervals. Statistically significant differences are marked with standard notation (* \(p < 0.05\), ** \(p < 0.01\), *** \(p < 0.001\), **** \(p < 0.0001\), ns = not significant). Results show that performance improves with compliance, and combining modalities helps most when one is ignored—allowing the other to compensate.</figcaption>
</figure>

<strong>Our method achieves superior task completion than the simple baseline method:</strong>

<figure>
    <img src="/assets/images/figures/results_overall_B1_vs_ours.png" alt="Results Overall Baseline 1 vs. Our Method" width="100%">
    <figcaption style="text-align: center;"><br/>Comparison between our adaptive Robot Guidance Controller (red) and the fixed-weight baseline controller (orange) across all four compliance regimes. Each subplot presents a separate evaluation metric: position error (top left), velocity error (top right), velocity smoothness (bottom left), and task completion time (bottom right). Bars are grouped by compliance condition: combinations of physical (P) and verbal (V) compliance ranging from full noncompliance (P=0, V=0) to full compliance (P=1, V=1). Error bars indicate 95\% confidence intervals. Statistical significance is marked above each pairwise comparison (* \(p < 0.05\), ** \(p < 0.01\), **** \(p < 0.0001\), ns = not significant). Our method outperforms the baseline in low-compliance regimes, where adaptive reallocation of guidance helps compensate for unattended modalities; differences taper under full compliance as both methods converge near ceiling performance.</figcaption>
</figure>

<strong>A snippet deep diving into the real-time interaction between a user and our method:</strong>

<figure>
    <img src="/assets/images/figures/example_ours.png" alt="Single User Using Our Method Deep Dive Example" width="100%">
    <figcaption style="text-align: center;"><br/>Examples of our Robot Guidance Controller adapting physical and verbal guidance across four compliance regimes. Each quadrant shows a time snippet of a single user trial under different combinations of physical ($P$) and verbal ($V$) compliance states. In the low compliance regime \((0,0)\), the controller increases speaking frequency and delivers strongly directive utterances while maintaining high corrective force. As verbal compliance increases \((0,1)\), speech becomes less frequent and language remains instructive, while force is moderated. In the reverse case \((1,0)\), physical guidance dominates, and verbal cues remain frequent but more redundant. Under full compliance \((1,1)\), the controller decreases both force and speaking frequency, and transitions toward encouraging feedback, matching expert therapist behavior observed. These examples highlight the system’s real-time adaptation in both intensity and content of guidance, driven by compliance estimation and optimization.</figcaption>
</figure>

## Code

Refer to the [Robot Guidance Controller repository](https://github.com/robot-guidance-controller/robot-guidance-controller) for the codebase of our controller.