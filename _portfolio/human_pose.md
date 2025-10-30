---
title: "Control manipulator by mimicking human's pose"
#excerpt: "Short description of portfolio item number 1<br/><img src='/images/500x300.png'>"
collection: portfolio
category: minor
permalink: /portfolio/human_pose
# lab: "Computational Intelligence and Robotics Lab (CIR)"
# venue: "National Taiwan Normal University"
# supervisor: "Supervisors: Prof. Chen-Chien James Hsu"
---
This is the project for the course "Robotic Systems Architect" in my Master's. I use 2 cameras placed in perpendicular direction with each other. They use YOLOv8 model to detect real-time human shoulder, elbow and wrist in the video by pixels, undistort and tranform to cameras' frames and then triangulate the 3d position of 2d correspondences between 2 frames each iteration. After filtering and signal processing, Inverse Kinematic is used to calculate the joint angle for LBR KUKA iiwa 7 R800 manipulator, to mimic the elbow and wrist's movements (assumming that the end of joint 1 is shoulder, end of joint 3 is elbow and end effector is like human's wrist)

<figure style="margin: 0 auto; display: block; text-align: center;">
  <video style="width: 100%; height: auto;" autoplay loop muted>
    <source src="/videos/mimicking.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <figcaption style="font-size: 0.9em; color: gray; text-align: center;">
    Visualization with LBR KUKA iiwa 7 R800 in CoppeliaSim
  </figcaption>
</figure>

<figure style="margin: 0 auto; display: block; text-align: center;">
  <video style="width: 100%; height: auto;" autoplay loop muted>
    <source src="/videos/lock_ID.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <figcaption style="font-size: 0.9em; color: gray; text-align: center;">
    Lock ID and find new ID after losting current target ID
  </figcaption>
</figure>