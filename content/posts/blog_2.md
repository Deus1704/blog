---
title: "Blog 2: All Pieces Falling into place"
date: 2024-06-20T16:29:31+05:30
draft: false
toc: false
images:
tags:
  - gsoc
---

## Update On New Coalignment
The very first version of the new Coalignment API has been completely implemented, with all the test cases written! 
The architecture of the proposed co-alignment API closely mirrors the design principles found in SunPy's rotation module, where a decorator pattern is employed to register specific methods designated for executing co-alignment tasks. Detailed documentation and guidelines on utilizing the new API are available for review at [this](https://sunpy--207.org.readthedocs.build/projects/sunkit-image/en/207/how_to_guide/adding_a_coalignment_method.html) docs.

## Ideas regarding the Future of Coalignment & Major Concerns

We have received numerous comments concerning the new co-alignment API, with the majority emphasizing the revision of the coalignment methods rather than the API structure itself.
Consequently, I will be delving into the specific modifications occurring at the World Coordinate System (WCS) level throughout the coalignment process and the request of returning only the shifts and not applying the shift to the actual data.

Although we are afraid that the suggestiong might be aiming to reinvent the reproject but again the fundamentally the approach for the two is different and needs to be thought of in brief before taking any major steps. 
We might be discussing this issue in the next community meet once Stuart is back.

## Update on STARA

The STARA module and the examples are completely ready, after along time of resolving conflicts, planning testing. We have come a long way with these test figures.

| ![HMI Map](/images/test_hmi.png) | ![HMI Map with Sunspot Identified](/images/stara_hmi.png) |
|:---:|:---:|
| Test HMI Continuum Map | Sunspot identified by STARA on the Test Map |