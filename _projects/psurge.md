---
layout: page
title: Probabilistic Storm Surge
description: Improving P-Surge guidance for NHC's storm surge forecasts
img: assets/img/psurge_ian_gt6ft.png
importance: 1
category: Storm Surge
giscus_comments: true
---

Storm surge is often the deadliest hazard in a landfalling tropical cyclone. Small changes in a hurricane's track, intensity, or size can make a big difference in how much water reaches the coast, and these are the parts of the forecast that are hardest to get right. Because of this, the National Hurricane Center (NHC) bases its storm surge forecasts on probabilistic guidance instead of a single deterministic run.

The main guidance for this is the Probabilistic Tropical Storm Surge model (P-Surge). P-Surge takes the NHC official forecast and builds an ensemble of storms around it. The ensemble varies the cross-track position, forward speed, intensity, and size of the storm based on NHC's historical forecast errors. Each member is run through the SLOSH (Sea, Lake, and Overland Surges from Hurricanes) model, and the members are combined into the probability of exceeding different water levels and the water level at different exceedance thresholds.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/psurge_ian_gt6ft.png" title="Experimental P-Surge probability of storm surge greater than 6 ft for Hurricane Ian" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Probability of water levels greater than 6 ft above NAVD88 for Hurricane Ian (2022) from an experimental P-Surge configuration, initialized 18 UTC 27 September 2022.
</div>

## What I work on

**Storm size and intensity together.** The radius of maximum wind (RMW) controls where the strongest winds hit the coast, but NHC does not forecast it and numerical models have limited skill predicting it ([Trabing et al. 2024](https://doi.org/10.1029/2024GL109663)). P-Surge uses a statistical RMW forecast and varies the storm size in its ensemble. Errors in intensity and RMW are related: storms that come in stronger than forecast also tend to be smaller. In [Trabing et al. (2026)](https://doi.org/10.1175/WAF-D-26-0012.1) we added this relationship to the P-Surge ensemble so that its members represent more realistic combinations of intensity and size.

**Forecast error statistics.** The P-Surge ensemble is only as good as the forecast errors it is built from. I maintain the code that computes the along-track, cross-track, intensity, and size error distributions from recent NHC, Central Pacific Hurricane Center, and Joint Typhoon Warning Center forecasts. That code was written so the statistics can be updated each year and extended to new regions, including Hawaii, Guam, and American Samoa.

**Storm size forecasts.** I developed a set of statistical RMW models that use the official forecast intensity, latitude, and wind radii. The approach builds on [Penny et al. (2023)](https://doi.org/10.1175/WAF-D-22-0209.1) and on angular momentum methods from the literature. The models give P-Surge a size forecast that stays consistent with the official forecast.

**Initial water level.** The water level along the coast before a storm arrives matters as much as the surge itself. I built a workflow that turns real-time tide gauge observations into maps of the water level anomaly (observed minus predicted tide) for each forecast cycle, so the starting water level used by the model can be checked against observations.

**Verification and tools.** I wrote Python tools to read, plot, and compare P-Surge output from different model versions. These tools build retrospective databases and score experiments with reliability diagrams, ROC curves, and categorical scores like POD, FAR, and CSI. This lets us test changes on past storms before they go into operations. More recently I have been exploring how AI techniques could improve probabilistic storm surge guidance.

The observations used to verify P-Surge are described on the [storm surge observations]({{ '/projects/surge_obs/' | relative_url }}) page.

---

Penny, A. B., and Coauthors, 2023: Operational Storm Surge Forecasting at the National Hurricane Center: The Case for Probabilistic Guidance and the Evaluation of Improved Storm Size Forecasts Used to Define the Wind Forcing. Wea. Forecasting, 38, https://doi.org/10.1175/WAF-D-22-0209.1.

Trabing, B. C., A. B. Penny, J. Martinez, and C. Fritz, 2024: Are Forecasts of the Tropical Cyclone Radius of Maximum Wind Skillful? Geophys. Res. Lett., 51, e2024GL109663, https://doi.org/10.1029/2024GL109663.

Trabing, B. C., A. B. Penny, A. A. Taylor, and C. Fritz, 2026: Improving the P-Surge Ensemble System by Incorporating the Relationship between Tropical Cyclone Intensity and Radius of Maximum Wind Errors. Wea. Forecasting, 41, 1675–1688, https://doi.org/10.1175/WAF-D-26-0012.1.
