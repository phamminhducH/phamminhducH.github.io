---
title: "Adaptive Sliding Mode Control for Lower-limb Exoskeleton with nonlinear Spring Mechanism"
#excerpt: "Short description of portfolio item number 1<br/><img src='/images/500x300.png'>"
collection: portfolio
category: minor
permalink: /portfolio/exo
# lab: "Computational Intelligence and Robotics Lab (CIR)"
# venue: "National Taiwan Normal University"
# supervisor: "Supervisors: Prof. Chen-Chien James Hsu"
---
This is the research project for M2 program. This project designs the adaptive controller for Exo-skeleton system to handle the nonlinearity of spring and uncertainties in human’s usage. When humans use exoskeleton, different users have
different leg’s mass and inertia. It can make uncertain parameters to the model. Moreover, stiffness factor of spring can be changed over time or actively by human; and the on/off spring mechanism cause complex term on model. My approaches is using Extended State Observer (ESO) to estimate the total disturbance term and using Sliding Mode Control with the estimation of ESO to ensure stability of system with unknown human leg’s parameters or spring parameters. The evaluation are implemented using Simscape 2-DoF lower-limb exoskeleton model. 

This project is developed for a lower-limb exoskeleton system. The control trajectories are generated via human skill transfer, where motion data captured from sensors on one limb is utilized to produce corresponding movements for the contralateral limb. This methodology is applicable to gait rehabilitation for patients with unilateral impairments.

<figure style="margin: 0 auto; display: block; text-align: center;">
  <iframe src="/files/slides/Poster_Research_Project_PhamMinhDuc_.pdf" 
          width="100%" 
          height="600px" 
          style="border: 1px solid #ccc; border-radius: 8px;">
    <p>Your browser does not support PDFs. 
       <a href="/files/slides/Poster_Research_Project_PhamMinhDuc_.pdf">Download the PDF</a>.
    </p>
  </iframe>
  <figcaption style="font-size: 0.9em; color: gray; text-align: center;">
    Adaptive Sliding Mode Control for Exoskeleton
  </figcaption>
</figure>

