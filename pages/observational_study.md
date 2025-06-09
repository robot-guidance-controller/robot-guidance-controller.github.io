---
layout: page
title: Obversational Study
permalink: /observational-study/
---

## Summary

<figure>
    <img src="/assets/images/figures/observational_study_summary.png" alt="Obersvational Study Summary" width="100%">
    <figcaption style="text-align: center;"><br/>Observational study design and key findings from expert-led demonstrations. Top row: Four experimental conditions used to isolate guidance modalities—reference trajectory (passive patient), verbal-only, physical-only, and combined guidance. Bottom row: Analysis reveals adaptive guidance patterns across compliance states. (a) Median physical force decreases as verbal and physical compliance together progressively increase. (b) Speaking frequency reduces from 1.77 to 0.36 words/second with higher verbal compliance. (c) Language content shifts from instructional (ratio 3.67) to encouraging (ratio 1.60) as verbal compliance improves. These patterns demonstrate how expert instructors naturally adapt both the intensity and nature of guidance based on learner compliance levels.</figcaption>
</figure>

## Trial Videos

<ol>
  <li>
    <strong>Reference Trajectory</strong><br><br>
    The therapist performed the exercise while the patient remained passive (neither actively complying nor resisting). This provided baseline data for learning reference trajectory ($x_{\text{ref}}, \dot{x}_{\text{ref}}$) and system dynamics parameters ($M, B$).
    <br>
    <br>
    <video class="video-js" style="display:block;width:100%;" controls preload="auto">
        <source src="/assets/videos/observational_study_trials/1_reference_trajectory.webm" type="video/webm">
    </video>
    <br>
  </li>

  <li>
    <strong>Verbal Guidance Only</strong><br><br>
    The therapist provided only verbal guidance without any physical contact as the patient attempted to follow the trajectory. During these trials, the patient varied their verbal compliance levels. This enabled learning verbal control gains ($K_v, B_v$).
    <br>
    <br>
    <video class="video-js" style="display:block;width:100%;" controls preload="auto">
        <source src="/assets/videos/observational_study_trials/2_verbal_only.webm" type="video/webm">
    </video>
    <br>
  </li>

  <li>
    <strong>Physical Guidance Only</strong><br><br>
    The therapist guided the patient using only physical guidance without verbal cues. During these trials, the patient varied their physical compliance levels. This enabled learning physical control gains ($K_p, B_p$).
    <br>
    <br>
    <video class="video-js" style="display:block;width:100%;" controls preload="auto">
        <source src="/assets/videos/observational_study_trials/3_physical_only.webm" type="video/webm">
    </video>
    <br>
  </li>

  <li>
    <strong>Combined Guidance</strong><br><br>
    The therapist used both physical and verbal guidance simultaneously. During these trials, the patient varied both physical and verbal compliance levels. This provided data for learning compliance estimation parameters.<br>
    This trial was conducted twice:
    <br>
    <br>
    <video class="video-js" style="display:block;width:100%;" controls preload="auto">
        <source src="/assets/videos/observational_study_trials/4_combined_guidance_1.webm" type="video/webm">
    </video>
    <br>
    <video class="video-js" style="display:block;width:100%;" controls preload="auto">
        <source src="/assets/videos/observational_study_trials/4_combined_guidance_2.webm" type="video/webm">
    </video>
    <br>
  </li>
</ol>

## Trial Sensor Data

For all trials we recorded a time series of patient wrist position, therapist force exertion, and a variety of other supplemental measurements using a coordinated deployment of sensors (MoCap, IMU, EMG, etc.). All data modalities are in CSV format, and have been synced up with each other and the videos on this page.

<a href="/assets/observational_study_trial_sensor_data.zip" download class="download-button">
    Download Data ⏬️
</a>