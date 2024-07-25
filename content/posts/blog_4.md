---
title: "Blog 4: Testing the New Coalignment"
date: 2024-07-26T01:29:31+05:30
draft: false
toc: false
images:
tags:
  - gsoc
---

Now that we've agreed on the structure of the co-alignment API and also laid down its foundation, all that's left is to validate it through actual tests and generate some gallery examples.

## First try with coaligning EIS raster with AIA map
Let's take a closer look at the EIS raster first. I found an AIA image close to the `date_average` of the raster.

| ![EIS raster](/images/original_eis.jpeg)  | ![AIA Full-disc image](/images/aia_near_raster_avg.jpeg)  |
|:---:|:---:|
|  EIS raster | AIA Full-disc image|


| ![Updated EIS](/images/updated_eis.png)  |
|:---:|
|  Updated EIS |

At first glance, the results seemed promising, but a more detailed analysis revealed some discrepancies.

The updated WCS metadata looked fine at first, but on closer inspection, it wasn't entirely correct. We'll dive into the specifics later in this blog. For now, let's discuss why it might look correct at a glance. How does a common user check if the maps are aligned? By overlaying them and checking the overlaps!

| ![EIS overlaid on AIA](/images/eis_overlaid_aia.png)  | ![Zoomed](/images/eis_overlaid_aia_zoomed.png)  |
|:---:| :---:|
|  EIS overlaid on AIA | Zoomed|

This visual inspection might convince some that the method works, but it’s far from accurate. We proved this by highlighting the bright regions and focusing on the actual overlaps.

| ![EIS contours overlaid on AIA](/images/old_contours.png)  |
|:---:|
|  EIS contours overlaid on AIA |

This showed us that something was wrong with either the way we were updating the metadata or the co-alignment method. While discussing this, we realized that an assumption in the match_template method was that the maps should have the same type of WCS.


## The Celestial Fix

In our initial approach, we focused on adjusting the CRPIX values instead of the CRVAL values. CRPIX specifies the position of the reference pixel in the image, shifting the image in pixel space without correcting the world coordinates directly. This method led to apparent alignment issues because it didn't address the celestial coordinate system. After consultation, we realized that adjusting CRVAL, which defines the world coordinates of the reference pixel, is essential. This adjustment ensures that the reference points align correctly in world coordinate space, maintaining consistent mapping between pixel and celestial coordinates.

Furthermore, for accurate co-alignment, the observers (instruments) should be within a tolerable angular separation to minimize parallax effects. When observers are too far apart, solar features can appear differently due to relative positions, complicating alignment. By correcting CRVAL values and considering angular separation, we achieved precise co-alignment, as evidenced by the corrected overlay of EIS contours on the AIA image, allowing for reliable scientific analysis.

| ![EIS contours overlaid on AIA (corrected)](/images/fixed_eis.jpeg)  |
|:---:|
|  EIS contours overlaid on AIA (corrected) |
