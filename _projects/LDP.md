---
layout: page
title: Landfall Distribution Product (LDP)
description: A probabilistic framework for hurricane landfall and intensity uncertainty
img: assets/img/publication_preview/VMAX_90_v3_Prototype_AL092021_2021082612_wcone_fromtxt.png
importance: 3
category: Forecasting
giscus_comments: true
---

The cone of uncertainty tells people where the center of a storm might go, but it says nothing about how strong the storm might be when it gets there. The Landfall Distribution Product (LDP) is designed to fill that gap by giving the probability of landfall in different coastal regions, along with the range of intensities to expect if landfall happens.

## How it works

The LDP uses the 1000 statistical realizations from NHC's Monte Carlo Wind Speed Probability model. Each realization is the official forecast perturbed by errors drawn from NHC's past track and intensity forecast performance. For each realization, the LDP uses a distance-to-land table to find where and when it first crosses the coast, then assigns that landfall to a region using shapefiles of states, islands, and countries. Some regions, such as the Florida coastline, are split into smaller pieces.

Adding up all the realizations gives:

* the probability of landfall in each region, and
* the conditional probability of each intensity category at landfall in that region.

Because the LDP comes from the same statistical model as NHC's wind speed probabilities, its message stays consistent with NHC's other operational products.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/publication_preview/VMAX_90_v3_Prototype_AL092021_2021082612_wcone_fromtxt.png" title="LDP prototype for Hurricane Ida" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    A prototype LDP graphic for Hurricane Ida (2021), showing the landfall intensity distribution together with the cone of uncertainty.
</div>

## Evaluation and communication

The development of the LDP and an evaluation of its landfall probabilities against observed landfalls are described in [Trabing et al. (2023)](https://doi.org/10.1175/WAF-D-22-0199.1). A product is only useful if people understand it, so we worked with social scientists to test prototype graphics with Florida residents and with NHC partners. Most respondents preferred having probabilistic intensity information over the current cone graphic alone, and nearly 90% wanted at least some percentages in their weather forecasts ([Eicher et al. 2025](https://doi.org/10.1002/met.70089)).

The same approach has since been extended to compute landfall probabilities along continuous coastline segments, where the size of each region changes with forecast lead time and uncertainty. However, this updated version is not publicly available at this time.

The code is available at <https://gitlab.com/Btrabing/ldp>.

---

Eicher, R., D. J. Halperin, B. C. Trabing, D. Lane, D. Sellnow, T. Sellnow, and M. Croker, 2025: Developing Experimental Probabilistic Intensity Forecast Products for Landfalling Tropical Cyclones. Meteor. Appl., 32, e70089, https://doi.org/10.1002/met.70089.

Trabing, B. C., K. D. Musgrave, M. DeMaria, B. C. Zachry, M. J. Brennan, and E. N. Rappaport, 2023: The Development and Evaluation of a Tropical Cyclone Probabilistic Landfall Forecast Product. Wea. Forecasting, 38, 1363–1374, https://doi.org/10.1175/WAF-D-22-0199.1.
