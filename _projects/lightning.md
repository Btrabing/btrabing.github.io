---
layout: page
title: Lightning
description: Learning more about tropical cyclones from GLM
img: assets/img/2mar_cr6.png
importance: 3
category: Research
giscus_comments: true
---

I love watching lightning. Every flash is unique and lasts only a fraction of a second. Lightning is both beautiful and dangerous, causing an average of 28 deaths per year in the U.S.

The Geostationary Lightning Mapper (GLM) on the GOES-R series satellites has observed total lightning over the Americas and nearby oceans since 2017. Lightning helps show where thunderstorms are and how strong they are, and it is available over the ocean where radar coverage is sparse. We are using it to better understand when tropical cyclones form and intensify.

## Quality control of GLM

GLM data can contain artifacts that look like lightning but are not, including blooming events, spurious false flashes, "bar" effects, and sun glint. These artifacts are a particular problem for machine learning methods, which can learn the artifacts instead of the real signal. In [Trabing et al. (2024)](https://doi.org/10.1175/JTECH-D-23-0138.1) we developed simple quality control methods, using energy thresholds and the variance of lightning group area and energy, along with machine learning-based anomaly detection. The share of flagged lightning within 100 km of Atlantic tropical cyclones dropped from 70% in 2017 to 2% in 2021 as the GLM processing algorithm improved, but quality control is still needed for a consistent long-term record.

## Lightning before tropical cyclogenesis

Several studies have suggested that lightning could signal tropical cyclone intensification, while others have found the opposite. Differences in the large-scale thermodynamics and background aerosols could explain some of these mixed results. In [Mesa et al. (2026)](https://doi.org/10.1175/MWR-D-25-0270.1) we used an object-based approach to analyze lightning characteristics in the environments of tropical disturbances before they become tropical cyclones.

## A tropical cyclone lightning archive

Building on the quality control work, I am developing an archive of quality-controlled GLM lightning for every Atlantic, East Pacific, and Central Pacific tropical cyclone since 2018, built from public cloud data. The archive tracks lightning relative to the storm center and lets lightning in an active storm be compared with past storms in real time.

---

Mesa, N. A., B. C. Trabing, M. M. Bell, A. Brammer, P. Duran, P. J. Klotzbach, K. Musgrave, and S. Stevenson, 2026: An Object-Based Analysis of Lightning Characteristics in Pretropical Cyclogenesis Environments. Mon. Wea. Rev., 154, 1909–1930, https://doi.org/10.1175/MWR-D-25-0270.1.

Trabing, B. C., K. Hilburn, S. Stevenson, K. D. Musgrave, and M. DeMaria, 2024: Quality Control of Geostationary Lightning Mapper Observations for Tropical Cyclone Applications. J. Atmos. Oceanic Technol., 41, 889–901, https://doi.org/10.1175/JTECH-D-23-0138.1.
