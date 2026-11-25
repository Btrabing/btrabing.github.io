---
layout: page
title: Storm Surge Observations
description: An objective dataset of tropical cyclone water levels for verification
img: assets/img/surge_obs_schematic.png
importance: 2
category: Storm Surge
giscus_comments: true
---

To know whether storm surge guidance is any good, we need to compare it against what actually happened. That sounds simple, but water level observations during hurricanes are messy. Gauges fail or stop reporting near the peak, rivers add fresh water on top of the surge, waves contaminate some sensors, and a storm can produce more than one peak at the same location.

NHC has kept a quality-controlled dataset of tropical cyclone water levels since 2018, with observations going back to 2008. Earlier versions of the dataset focused on capturing significant surge events. They did not consistently include stations where little or no surge occurred. For probabilistic guidance like [P-Surge]({{ '/projects/psurge/' | relative_url }}), those "null" observations matter: without them, we cannot measure false alarms or tell whether a wide forecast spread is justified.

## An objective, storm-relative approach

I rebuilt the dataset using an objective framework that treats every storm the same way:

1. **Select stations from the wind field.** Stations are kept if they fall within a swath built from the storm's radius of maximum wind and 34-kt wind radii along the best track, plus a buffer. This means the sample changes with each storm's size, structure, and motion, and it includes stations that saw little surge.
2. **Find the representative peak.** A peak-finding algorithm searches a storm-dependent time window around landfall for the wind-driven water level maximum. It records the peak water level, the surge above the initial water level, timing, and how long water stayed above flood thresholds.
3. **Describe the storm at the time of the peak.** Each observation records the storm-relative position (along- and cross-track distance, also normalized by storm size), intensity, RMW, translation speed, and nearby wind observations.
4. **Apply quality control.** Automated flags mark secondary peaks, likely freshwater flooding, missing data around the peak, and wave-affected sensors. Each storm is then reviewed to ensure it meets data quality standards.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/surge_obs_schematic.png" title="Storm-relative station selection" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Schematic of how stations are selected. Water level stations (stars) are kept (red) when they fall within the RMW and 34-kt wind swath, or its buffer, along the best track.
</div>

The updated dataset combines NOAA CO-OPS tide stations and USGS water level sensors from more than 54 tropical cyclones between 2008 and 2024. Organizing the observations relative to the storm makes it possible to look at where the highest water levels occur relative to the storm's center, size, and motion. It also gives a consistent sample for comparing versions of the storm surge guidance.

A manuscript describing the dataset is in preparation. The same observations are used in the storm surge verification at NHC.
