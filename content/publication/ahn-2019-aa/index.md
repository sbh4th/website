---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: Improved Monte Carlo methods for estimating confidence intervals for eleven
  commonly used health disparity measures
subtitle: ''
summary: ''
authors:
- Jaeil Ahn
- sam-harper
- Mandi Yu
- Eric J Feuer
- Benmei Liu
tags: []
categories: []
date: '2019-01-01'
lastmod: 2020-09-25T09:07:35-04:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ''
  focal_point: ''
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
publishDate: '2020-09-25T13:07:34.837862Z'
publication_types:
- 2
abstract: 'Health disparities are commonplace and of broad interest to policy makers,
  but are also challenging to measure and communicate. The Health Disparity Calculator
  software (HD*Calc, v1.2.4) offers Monte Carlo simulation (MCS)-based confidence
  interval (CI) estimation of eleven disparity measures. The MCS approach provides
  accurate CI estimation, except when data are scarce (e.g., rare cancers). To address
  sparse data challenges to CI estimation, we propose two solutions: 1) employing
  the gamma distribution in the MCS and 2) utilizing a zero-inflated Poisson estimate
  for Poisson sampling in simulation experiments. We evaluate each solution through
  simulation studies using female breast, female brain, lung, and cervical cancer
  data from the Surveillance, Epidemiology, and End Results (SEER) program. We compare
  the coverage probabilities (CPs) of eleven health disparity measures based on simulated
  datasets. The truncated normal distribution implemented in the MCS with the standard
  Poisson samples (the default setting of HD*Calc) leads to less-than-optimal coverage
  probabilities (<95%). When both the gamma distribution and the estimated mean from
  the zero-inflated Poisson are used for the MCS, the coverage probabilities are close
  to the nominal level of 95%. Simulation studies also demonstrate that collapsing
  age categories for better CI estimation is not a pragmatic solution.'
publication: '*PLoS One*'
doi: 10.1371/journal.pone.0219542
# add Almetric adn dimensions badges
add_badge: true
---
