---
title: "Servo motors control using Linux kernel"
#excerpt: "Short description of portfolio item number 1<br/><img src='/images/500x300.png'>"
collection: portfolio
category: minor
permalink: /portfolio/linux_kernel
# lab: "Computational Intelligence and Robotics Lab (CIR)"
# venue: "National Taiwan Normal University"
# supervisor: "Supervisors: Prof. Chen-Chien James Hsu"
---
Unlike user-space controls based on the application layer, kernel-based control runs inside the kernel close to hardware, uses kernel modules, interrupt handlers, and real-time scheduling. The Linux kernel is ideal for real-time robotics control due to its low-latency response, precise timing, and direct hardware access. It delivers deterministic performance and minimal jitter—crucial for stable motor and sensor control. Its modular, open-source design also allows seamless integration of custom drivers and real-time tasks, making it a powerful and reliable foundation for high-performance robotic systems. 

<figure style="margin: 0 auto; display: block; text-align: center;">
  <video style="width: 80%; height: auto;" autoplay loop muted>
    <source src="/videos/kernel_2.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <figcaption style="font-size: 0.9em; color: gray; text-align: center;">
    Synchronising motors using linux kernel
  </figcaption>
</figure>

<figure style="margin: 0 auto; display: block; text-align: center;">
  <video style="width: 100%; height: auto;" autoplay loop muted>
    <source src="/videos/kernel_1.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <figcaption style="font-size: 0.9em; color: gray; text-align: center;">
    Synchronising motors using linux kernel
  </figcaption>
</figure>