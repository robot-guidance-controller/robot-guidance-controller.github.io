---
layout: page
title: Results
permalink: /results/
---

## Evaluation Metrics

We evaluated our methods using the following metrics:

- **Position Error**  
  Mean absolute error (MAE) between the user's actual position and the reference position, calculated as  
  $$
  \text{MAE} = \frac{1}{N}\sum_{i=1}^{N}\|x_i - x_{ref,i}\|
  $$  
  where \( x_i \) is the user's position at time \( i \).

- **Velocity Error**  
  MAE between the user's velocity and the reference velocity, computed as  
  $$
  \text{MAE}_v = \frac{1}{N}\sum_{i=1}^{N}\|\dot{x}_i - \dot{x}_{ref,i}\|
  $$  
  capturing the temporal accuracy of movement execution.

- **Movement Smoothness**  
  Quantified using the standard deviation of the velocity magnitude over time. Calculated as:  
  $$
  S = \sqrt{\frac{1}{N-1}\sum_{i=1}^N(\|\dot{x}_i\|-\mu_v)^2}
  $$  
  where \( \mu_v \) is the mean velocity magnitude. Lower values indicate smoother motion.

- **Time to Completion**  
  Total time required to complete the task.

- **Frequency of Words Spoken**  
  Average number of words per second spoken during task execution, indicating the intensity of verbal guidance provided.

- **Ratio of Instructional to Encouraging Phrases**  
  Ratio of instructional phrases (e.g., “move left”, “push harder”) to encouraging phrases (e.g., “good job”, “keep going”), calculated by classifying each utterance and computing the ratio  
  $$
  R = \frac{N_{inst}}{N_{enc}}
  $$.

## Highlights

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