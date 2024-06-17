---
title: "Blog 1: Rethinking Coalignment from Ground-up"
date: 2024-06-15T20:29:31+05:30
draft: false
toc: false
images:
tags:
  - gsoc
---

## The Very Essence of Coalignment

At its core, coalignment is all about making sure our solar images match up as best they can. It uses a few different techniques, like template matching and solar rotation correction, to get this done. This is really important when we're trying to accurately track and study what's happening on a part of sun over time. 
We re-thought the entire process of what our new API be providing to the users as well as its structure.

![Naive Refactor](/images/proposed_struct.png)

This was one of the idea that was very naive version, but focused entierly for the user's comfort in applying the coalignment methods.


## The Basic Structure we finally agreed Upon

![Internal Sturcture](/images/internal.png)

We agreed to have this as the very basic structure which we would be working/developing upwards. The following example demonstrates the way it would work. 

```python
aia_map1 = sunpy.map.Map(sunpy.data.sample.AIA_193_CUTOUT01_IMAGE)
aia_map2 = sunpy.map.Map(sunpy.data.sample.AIA_193_CUTOUT03_IMAGE)
### Creating a template from aia_map1
bottom_left = SkyCoord(600 * u.arcsec, -500 * u.arcsec, frame=aia_map1.coordinate_frame)
top_right = SkyCoord(800 * u.arcsec, -200 * u.arcsec, frame=aia_map1.coordinate_frame)
submap = aia_map1.submap(bottom_left, top_right=top_right)

coaligned_map = coalignment_interface("match_template",aia_map2, submap)
```

![combined image](/images/combined.png)

I am currently implementing the decorator structure for the sunkit-image, but that would be covered in another blog.