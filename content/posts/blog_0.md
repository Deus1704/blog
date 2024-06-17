---
title: "Blog 0: The First Two Weeks"
date: 2024-05-25T20:29:31+05:30
draft: false
toc: false
images:
tags:
  - gsoc
---

#### A summary of activities completed in the two weeks leading up to the start of the coding period.
## Table of Contents
- [Wrapping up the draft pull request](#draft_pr)
- [Incorporating suggestions for STARA & its examples](#issue1)
- [Fixing the doc failures](#fix_doc_fails)
- [First Meet with Mentors](#first_meet)

After completing my end-semester exams, I was overwhelmed by the outstanding tasks that I had let accumulate over time.
In order to address those, I tried resolving dependencies and package issues of the previous environments of
sunpy & sunkit-image but, ultimately gave up and initialised a new environment. After discussions with mentors, the project priorities were clarified, allowing me to efficiently plan & complete my tasks during the community bonding period. What follows is the detailed account of all the tasks completed during these two weeks.

## Incorporating suggestions for Sunspot Tracking and Recognition Algorithm (STARA)

Incorporated suggestions and made several changes to the STARA example. Attempted to create a mock HMI continuum data with an artificial "sunspot" at a chosen location with a certain radius. But it did not meet the exact requirements of the STARA, hence no regions could be identified. The written mock hmi map are demonstrated below,

| ![Mock HMI Map without Sunspot](/images/mock_wo.png) | ![Mock HMI Map with Sunspot](/images/mock_withspot.png) |
|:---:|:---:|
| Mock HMI Map without Sunspot | Mock HMI Map with Sunspot |

Discussed alternative approaches with mentor Nabil regarding the mock HMI map. According to his suggestion I tried the HMI continuum test data present in `sunpy/data/test` directory, but it had some issues with the WCS hence STARA couldn't properly find the sunspot regions.

## Wrapping up the draft pull request

I began working on the transformation of a vector field some time ago but encountered challenges in validating the approach. Using Astropy for the transformation confirmed the accuracy of the function I wrote. The next step is to seek feedback from mentors and the SunPy community. But I still feel a need to test this more rigorously which can validate that this would work with different frames too. I studied about different frames provided by the SPICE toolkit and tried to match the sunpy frames and the SPICE frames and have confirmed that the function works with the static frames.

## Fixing the doc failures

Two out of my three open pull requests encountered documentation failures due to incorrect referencing of functions or modules, or example galleries. After studying the conventions of Sphinx and SunPy, I resolved these issues. Additionally, I discovered how to set up GitHub CI actions on my forks.

## First Meet with Mentors

In our initial meeting, my mentor Will provided a brief overview of the purpose of sunkit-image, emphasizing its primary function: coalignment. He explained the fundamental concepts of coalignment, user expectations, and desired functionalities of the new API. We also reviewed the current coalignment API's shortcomings. We agreed that an improved API was necessary and discussed my proposed structure for this enhancement. We also drafted a plan for the entire rethinking and redesigning the new API over the span of 4 weeks.
