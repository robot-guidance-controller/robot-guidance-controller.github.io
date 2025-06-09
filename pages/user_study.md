---
layout: page
title: User Study
permalink: /user_study/
---

## Guidance Methods

Each user interacted with each of the following guidance methods through multiple trials, where each had them exhibit a specific compliance behavioral state.

- **Verbal Guidance Only**  
  A vision-based tracking system monitored the user's hand position via a camera and delivered spoken directional cues whenever the user deviated from the reference trajectory. No physical intervention was applied.

- **Physical Guidance Only**  
  A PD (Proportional–Derivative) controller applied corrective forces along the axis of deviation to physically guide users back to the reference trajectory. No verbal cues were given.

- **Combined Verbal and Physical Guidance**  
  A baseline system combining both modalities. The robot simultaneously provided corrective forces (as like the physical-only method) and spoken instructions triggered by deviations in position and velocity from the reference path (as like the verbal-only method).

- **Robot Guidance Controller (Our Method)**  
  An adaptive system that dynamically allocates verbal and physical guidance optimally based on real-time estimates of user compliance.

## Videos

(NOTE: Does not render correctly on Safari, please use Google Chrome.)

<!-- {% assign baselines = "1_language_only,2_physical_only,3_baseline,4_ours" | split: "," %}

{% for user_id in (0..11) %}
### User {{ user_id }}

{% assign user_id_str = user_id | append: "" %}

{% for baseline in baselines %}
**Baseline {{ baseline }}**

<div style="display: flex; flex-wrap: wrap; gap: 1rem; margin-bottom: 1.5rem;">
  {% assign baseline_path = "assets/videos/user_study/" | append: baseline %}
  
  {% for file in site.static_files %}
    {% if file.path contains baseline_path %}
      {% assign filename_parts = file.name | split: "_" %}
      {% assign file_user_id = filename_parts[0] %}
      
      {% if file_user_id == user_id_str %}
        <div style="flex: 1 1 300px;">
          <video style="width: 100%;" controls>
            <source src="{{ file.path }}" type="video/mp4">
          </video>
          <div style="text-align: center; font-size: 0.9em;">
            {{ file.name | remove: "_edited" | remove: ".mp4" }}
          </div>
        </div>
      {% endif %}
    {% endif %}
  {% endfor %}
</div>

{% endfor %}
<hr>
{% endfor %} -->

{% assign baselines_raw = "1_language_only,2_physical_only,3_baseline,4_ours" | split: "," %}
{% assign baseline_labels = "Language Only,Physical Only,Baseline Method,Our Method" | split: "," %}

{% for user_id in (0..11) %}
### User {{ user_id }}

{% assign user_id_str = user_id | append: "" %}

{% for baseline_index in (0..3) %}
  {% assign baseline = baselines_raw[baseline_index] %}
  {% assign baseline_label = baseline_labels[baseline_index] %}

**Baseline: {{ baseline_label }}**

<div style="display: flex; flex-wrap: wrap; gap: 1rem; margin-bottom: 1.5rem;">
  {% assign baseline_path = "assets/videos/user_study/" | append: baseline %}

  {% for file in site.static_files %}
    {% if file.path contains baseline_path %}
      {% assign filename_parts = file.name | split: "_" %}
      {% assign file_user_id = filename_parts[0] %}

      {% if file_user_id == user_id_str %}
        {% assign base_filename = file.name | remove: "_edited.mp4" %}
        {% assign label_raw = base_filename | split: "_" | slice: 1, 10 | join: "_" %}

        {% assign verbal = "" %}
        {% assign physical = "" %}

        {% if label_raw contains "V=1" %}
          {% assign verbal = "Full Verbal Compliance" %}
        {% elsif label_raw contains "V=0" %}
          {% assign verbal = "No Verbal Compliance" %}
        {% endif %}

        {% if label_raw contains "P=1" %}
          {% assign physical = "Full Physical Compliance" %}
        {% elsif label_raw contains "P=0" %}
          {% assign physical = "No Physical Compliance" %}
        {% endif %}

        {% assign label_parts = "" %}
        {% if verbal != "" and physical != "" %}
          {% assign label_parts = physical | append: " / " | append: verbal %}
        {% elsif verbal != "" %}
          {% assign label_parts = verbal %}
        {% elsif physical != "" %}
          {% assign label_parts = physical %}
        {% else %}
          {% assign label_parts = "Unlabeled Condition" %}
        {% endif %}

        <div style="flex: 1 1 300px;">
          <video style="width: 100%;" controls>
            <source src="{{ file.path }}" type="video/mp4">
          </video>
          <div style="text-align: center; font-size: 0.9em;">
            {{ label_parts }}
          </div>
        </div>
      {% endif %}
    {% endif %}
  {% endfor %}
</div>

{% endfor %}
<hr>
{% endfor %}