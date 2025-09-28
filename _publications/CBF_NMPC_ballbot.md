---
title: "CBFs-Based Model Predictive Control for Obstacle Avoidance With Tilt Angle Limitation for Ball-Balancing Robots"
authors: "<strong>M. D. Pham</strong>, D. C. Vu, T. T. H. Nguyen, T. V. A. Nguyen, T. L. Nguyen"
collection: publications
category: manuscripts
permalink: /publication/CBF_NMPC_ballbot
excerpt: 'This paper is about the number 3. The number 4 is left for future work.'
date: 2025-05-06
venue: 'IEEE Access'
#slidesurl: 'http://academicpages.github.io/files/slides3.pdf'
paperurl: 'https://ieeexplore.ieee.org/abstract/document/10988790'
citation: '"<strong>M. D. Pham</strong>, D. C. Vu, T. T. H. Nguyen, T. V. A. Nguyen, and T. L. Nguyen, “CBFs-based Model Predictive Control for obstacles avoidance with tilt angle limitation for ball-balancing robots,” <i>IEEE Access</i>, 2025."'
---

This research use Nonlinear Model Predictive Control (NMPC) as the main controller for the 3D-Ballbot system. A significant advantage of NMPC in comparison with Hierarchical Sliding Mode Control in [time-optimal HSMC](/publication/time_optimal) is that NMPC can control directly in the dynamic 3D model without model decomposing method like HSMC. 

This optimal control allows applying several constraints such as safe constraints or obstacle avoidance directly inside optimization problem. Inheriting [NMPC_CBF_2](/publication/NMPC_JST_hust), we use Control Barrier Function as the model-based distance contraint between ballbot and obstacles (with the assumption that the movement of obstacles are known). Instead of directly implementing tilt angle limitations on the main NMPC, another Quadratic Programming Optimizer based on CBF is designed outside the main controller to reduce the constraint complexity of optimization.

The complex-shaped obstacles are also considered. An elliptic-bounded generation method is used to simplify the object boundary, especially concave obstacles definition in NMPC constraints, while Extended State Observer is used for observing, compensating the uncertainty terms, and estimating the velocities of the ballbot. 

In general, by combining this CBF-based NMPC and Quadratic Programming, this research addresses simultaneously high-quality observer, tracking control, balancing control, complex motion planning and safe-angle constraints for the 3D-ballbot system.

<figure style="text-align: center;">
  <img src="/images/NMPC_approach.png" alt="Control structure for NMPC Approach" tiltle="Control structure for NMPC Approach" width="400" />
  <figcaption style="font-size: 0.9em; color: gray;">
    Control structure for NMPC Approach
  </figcaption>
</figure>