---
title: "Blog 3: Side Quests Week"
date: 2024-07-03T17:29:31+05:30
draft: false
toc: false
images:
tags:
  - gsoc
---

While the mentors are waiting for community reviews on the new coalignment API, I've been diving into some fun side quests.


## Side Quest 1: [ASDA Example](https://github.com/sunpy/sunkit-image/pull/218)
The long-needed [Automated Swirl Detection Algorithm (ASDA)](https://doi.org/10.3847/1538-4357/aabd34) gallery example in the sunkit-image is now ready. The ASDA module is for identifying the swirls or vortices in the 2D flow field of the solar atmosphere. ASDA offers a robust tool for detecting and analyzing the vortices in the solar atmosphere.

Swirls in the solar atmosphere provide insights into dynamic solar processes such as solar flares and coronal mass ejections. Detecting and analyzing these swirls helps understand the mechanisms driving these solar activities.

The Gamma(Γ1 & Γ2) values are used for identifying the vortex center and the vortex edges respectively. 
- Gamma1 (Γ1): Identifies vortex centers by quantifying rotational motion.
- Gamma2 (Γ2): Detects vortex edges by measuring the coherence of swirling motion.

These can be visualised as;

| ![Gamma Visualization](/images/gammas.png)  |
|:---:|
|  Gamma values (Γ1 & Γ2) |

Using these, the final map with the swirls identified looks like:

| ![Swirl Map ](/images/detected_swirls.png)  |
|:---:|
|  Swirl Map with Velocity Field |

The swirl map is crucial for visualizing fluid flow dynamics in the solar atmosphere, helping to identify the distribution, size, and characteristics of vortices.


Magnifying a particular section of these for better understanding of the streamlines:
| ![Magnified Swirl Map ](/images/magnified_swirls.png)  |
|:---:|
|  Magnified Swirl Map Region with Streamlines |

Magnifying a specific region and overlaying streamlines allows for detailed analysis of flow patterns around swirls, aiding in understanding solar atmospheric dynamics and the interactions between different vortices.


## Side Quest 2: [Rotation Matrix](https://github.com/sunpy/sunpy/pull/7452)

One of my very first pull requests in SunPy received reviews after a long hiatus. The feedback highlighted some implementation issues with the way the SpicePy API was being used. For instance, the sxform function only accepts a single ephemeris time, which required a workaround to obtain the correct state transformation matrix. 
With the invaluable help of Albert, these issues have been resolved and the test cases have been updated accordingly.