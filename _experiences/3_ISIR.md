---
title: "M2 Internship - Resilient navigation on precarious terrain with a Ballbot"
collection: experiences
type: "On-site Internship"
permalink: /experiences/3_ISIR
venue: "Sorbonne Univesité"
department: "Institut des Systèmes Intelligents et de Robotique"
start_date: 2026-03-02
end_date: 2026-09-02
location: "Paris, France"
project: "Resilient navigation on precarious terrain with a Ballbot"
lab: "Institut des Systèmes Intelligents et de Robotique (ISIR)"
---

<h2 style="font-size: 1.2em;">Description</h2>

This internship proposal outlines a research project aimed at providing a ballbot with the capabilities of overcoming obstacles that it could encounter while navigating. The objective of this work is to define optimal control actions to overcome a fixed obstacle on the ground considering the robot velocity, the robot approaching angle w.r.t. the object, the robot inertia changes (e.g. through arms movement).

<figure style="margin: 0 auto; display: block; text-align: center;">
  <iframe src="/files/slides/stage-Navigation-resiliente-sur-terrains-precaires-avec-un-Ballbot.pdf" 
          width="100%" 
          height="600px" 
          style="border: 1px solid #ccc; border-radius: 8px;">
    <p>Your browser does not support PDFs. 
       <a href="/files/slides/stage-Navigation-resiliente-sur-terrains-precaires-avec-un-Ballbot.pdf">Download the PDF</a>.
    </p>
  </iframe>
  <figcaption style="font-size: 0.9em; color: gray; text-align: center;">
    Resilient navigation on precarious terrain with a Ballbot
  </figcaption>
</figure>

Currently, the objectives is adjusting the tilt angle to keep balancing when robot have a sudden collision with the obstacle in the ground (ex. the door bump at the height of 1cm to 3cm). The robot need to prepare before colliding, pass through the obstacle and keep balancing again after overcoming the obstacle. My approach is using Reinforcement Learning (RL) to generate the tilt angle trajectory for the contact phase.

<figure style="text-align: center; margin: 0 auto; display: block;">
  <img src="/images/phase.png" alt="Action phase divising by time-to-contact" tiltle="Action phase divising by time-to-contact" style="width: 80%; height: auto;" />
  <figcaption style="font-size: 0.9em; color: gray;">
    Action phase divising by time-to-contact
  </figcaption>
</figure>

However, sometimes the robot cannot have enough pre-contact velocity to climb over the obstacle, we need a acceleration phase before contact phase to get proper velocity (using normal Cacade PID), before switching to RL. In this control architecture, RL will be the high-level controller, which give the angle trajectory fot the low-level PID controller. I am using Proximal Policy Optimization (PPO) for training with MuJoCo physic engine due to its advantage of rigid contact. The simulation is done in both movement with arms and without arms. I am in the process of Sim-to-Real tranferring to use the trained policy from simulation in real robot platform (Mirokai from Enchanted Tools). There are some video on simulation: 

<figure style="margin: 0 auto; display: block; text-align: center;">
  <video style="width: 100%; height: auto;" autoplay loop muted>
    <source src="/videos/Ballbot_no_arms_RL.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <figcaption style="font-size: 0.9em; color: gray; text-align: center;">
    Mirokai overcomes the bump using pitch angle adjustment
  </figcaption>
</figure>

<figure style="margin: 0 auto; display: block; text-align: center;">
  <video style="width: 100%; height: auto;" autoplay loop muted>
    <source src="/videos/Ballbot_arms_RLandQP.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <figcaption style="font-size: 0.9em; color: gray; text-align: center;">
    Mirokai overcomes the bump using pitch angle and arms movement
  </figcaption>
</figure>

<h2 style="font-size: 1.2em;">References</h2>

<p style="font-size: 1em; line-height: 1.3; margin: 0;">
  <strong>Dr. Dario SANALITRO</strong><br>
  <i>Internship Supervisor</i><br>
  ISIR - Sorbonne Universite<br>
  Email: <a>sanalitro@isir.upmc.fr</a>
</p>

