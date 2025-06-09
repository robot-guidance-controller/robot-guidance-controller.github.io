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