---
title: "Time-optimal trajectory generation and observer-based hierarchical sliding mode control for ballbots with system constraints"
authors: "D. C. Vu, <strong>M. D. Pham</strong>, T. T. H. Nguyen, T. V. A. Nguyen, T. L. Nguyen"
collection: publications
category: manuscripts
permalink: /publication/time_optimal
excerpt: 'This paper is about the number 2. The number 3 is left for future work.'
date: 2024-04-13
venue: 'International Journal of Robust and Nonlinear Control'
#slidesurl: 'http://academicpages.github.io/files/slides2.pdf'
paperurl: 'https://onlinelibrary.wiley.com/doi/10.1002/rnc.7358'
citation: '"D. C. Vu, <strong>M. D. Pham</strong>, T. T. H. Nguyen, T. V. A. Nguyen, and T. L. Nguyen, “Time-optimal trajectory generation and observer-based hierarchical sliding mode control for ballbots with system constraints," <i>International Journal of Robust and Nonlinear Control,</i> 2024."'
---

This paper introduces a comprehensive motion planning–tracking–safety constraint scheme for a 3D ballbot system. Due to the complexity and the underactuated property of the Ballbot, the dynamic model are separated into 3 three sub-model (2 of them are considered as the 2D Ballbot model) and we generate the virtual control signal in each sub-model. This approach can leverage previous results in controlling planar ballbot and can generate control signal easier based on simpler models. After that, the actual control signal are tranformed based on three above virtual signals. However, these sub-models are not independent, there are always the terms called coupling interactions between planar models and they are often neglected in the previous research. In this work, we estimate these terms by using Extended State Observer (ESO).

To overcome the complexity of nonlinear motion equations, flatness theory is used to construct the time-optimal trajectory through an optimization problem, facilitating smooth movement of the ballbot, and obstacle avoidance based on RRT* waypoints.

In this research, Exponential Control Barrier Function (ECBF) are applied on safe control by limiting the maximum body's deflection angle. Hierarchical Sliding Mode control are the nominal controller, which guarantees trajectory-tracking control and balancing control. Quadratic Programmimg will adjust the nominal control signal and ensure a safe set of safe constraints. 

<figure style="text-align: center;">
  <img src="/images/HSMC_approach.png" alt="Control structure for HSMC Approach" tiltle="Control structure for HSMC Approach" width="400" />
  <figcaption style="font-size: 0.9em; color: gray;">
    Control structure for HSMC Approach
  </figcaption>
</figure>