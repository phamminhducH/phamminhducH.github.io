---
title: "Robot Navigation and Deep Reinforcement Learning"
#excerpt: "Short description of portfolio item number 1<br/><img src='/images/500x300.png'>"
collection: portfolio
category: major
permalink: /portfolio/TEEP
lab: "Computational Intelligence and Robotics Lab (CIR)"
venue: "National Taiwan Normal University"
supervisor: "Supervisors: Prof. Chen-Chien James Hsu"
---

This is the project that I had implemented in the 4-month academic internship in NTNU. In this period, I focus on two main directions: Learing Robot Oprating System (ROS2) for Robot Navigation and Learning Reinforcement Learning.

<h2 style="font-size: 1.2em;">Robot Navigation using ROS2</h2>

Robot Oprating System (ROS/ROS2) is a robotics middleware designed for robot communication, control, and orchestration. It provides a framework for building and controlling real-time robot systems, which is quite different to MATLAB/Simulink for modeling and simulation control algorithms. I designed some obstacle avoidance algorithm based on different method: 



<h3>Dynamic obstacle avoidance Navigation using Lidar</h3>

The Differentive-drive Robot moves to the designed point on the ground and avoids collisions with other dynamic objects passing throught its trajectory. The robot only knows its start point, end point and the data read from Lidar. The obstacles' information is processed by clustering the point clound, line approximation (detecting the front obstacles' shape in range) and velocity estimation (for dynamic obstacles). I use PID for position control or trajectory control and Poterntial Field approach for avoiding collision.

<figure style="margin: 0 auto; display: block; text-align: center;">
  <video style="width: 80%; height: auto;" autoplay loop muted>
    <source src="/videos/DDRobot_Demo.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <figcaption style="font-size: 0.9em; color: gray; text-align: center;">
    Obstacle avoidance using Potential Field Approach 
  </figcaption>
</figure>



<h3>Optimizing trajectory for robot manipulator using PSO-based Inverse Kinematics</h3>

This is the combination between Robotics and Optimization. The object is the 7-DoF KUKA LBR iiwa 14 R820 Manipulartor with main objective is designing the obstacle-avoidance trajectory without the need of Inverse Kinematics. I use Particle Swarm Optimization, a simple algorithm, and its variants to minimize the cost function including distance constraint, terminal contraint, smoothness constraint, safe constraint and collision-avoiding contraint. Anyway, this concept can also be applied for other more superior optimization algorithm, or more complex robot manipulators. For more detail, you can check the slide below.

<figure style="margin: 0 auto; display: block; text-align: center;">
  <video style="width: 80%; height: auto;" autoplay loop muted>
    <source src="/videos/PSO_IK.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <figcaption style="font-size: 0.9em; color: gray; text-align: center;">
    PSO-based Inverse Kinematics from start position to the end position
  </figcaption>
</figure>

<figure style="margin: 0 auto; display: block; text-align: center;">
  <video style="width: 80%; height: auto;" autoplay loop muted>
    <source src="/videos/PSO_Obstacle_avoidance.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <figcaption style="font-size: 0.9em; color: gray; text-align: center;">
    PSO-based obstacle avoidance algorithm for robot manipulator 
  </figcaption>
</figure>



<h3>Robot navigation on grid based on Vision</h3>

This is another result with ROS2 in combination with Computer Vision. The objective of the Differentive-drive Robot is to navigate in the tile ground. The robot only use the information from its front camera and initial position. Image/Video Processing detects the gaps between tiles to find its position on the map.

<figure style="margin: 0 auto; display: block; text-align: center;">
  <video style="width: 80%; height: auto;" autoplay loop muted>
    <source src="/videos/Turtlebot3_grid_world.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <figcaption style="font-size: 0.9em; color: gray; text-align: center;">
    Robot navigation on tile ground
  </figcaption>
</figure>


<h2 style="font-size: 1.2em;">Deep Reinforcement Learning</h2>

Reinforcement Learning (RL) and Deep Reinforcement Learning (Deep RL) have shown great potential across many applications. During my internship, I began exploring these methods and implemented RL-based solutions in different environments.



<h3>Robot Navigation</h3>

First time with RL, I implemented both conventional Reinforcement Learning and Deep Reinforcement Learning across two types of systems: Discrete state–Discrete action and Continuous state–Continuous action. The objective is to navigate a robot from initial position to a target point while avoiding obstacles. Q-learning (including both Tabular Q-learning, Deep Q-learning) and SARSA served as the foundational algorithms, but they are limited to Discrete state–Discrete action environments. To address Continuous state–Continuous action scenarios, which are more common in real-world applications, I applied Proximal Policy Optimization (PPO) and Soft Actor-Critic (SAC).

<div style="display: flex; justify-content: space-between; gap: 5px;">
  <figure style="text-align: center; width: 34%; margin: 0; margin-bottom: 20px;">
    <img src="/images/robot_navigation_0.png" 
         alt="Discrete state–Discrete action" 
         title="Discrete state–Discrete action" 
         style="width: 100%; height: auto; display: block; margin: 0 auto;" />
  </figure>

  <figure style="text-align: center; width: 29.5%; margin: 0; margin-bottom: 20px;">
    <img src="/images/robot_navigation_1.png" 
         alt="Continuous state–Continuous action" 
         title="Continuous state–Continuous action" 
         style="width: 100%; height: auto; display: block; margin: 0 auto;" />
  </figure>

  <figure style="text-align: center; width: 30%; margin: 0; margin-bottom: 20px;">
    <img src="/images/robot_navigation_2.png" 
         alt="Continuous state–Continuous action" 
         title="Continuous state–Continuous action" 
         style="width: 100%; height: auto; display: block; margin: 0 auto;" />
  </figure>
</div>

<figcaption style="font-size: 0.9em; color: gray; text-align: center;">
  Designed environments
</figcaption>



<h3>Snake game</h3>

A strategy game requires the agent to learn from its surrounding environment. This means that not only the current and target positions, but also the movement process and strategy, are essential for effective learning. I consider the Snake game a simple form of strategy game, where the snake must eat apples while avoiding the walls and its own body.
For learing the moving process, I import entire grid map as the input and a Convolutional neural network (CNN) to extract feartures from this input. This approach, known as CNN-based Reinforcement Learning, allows the agent to learn both the structural features of the map and effective movement strategies, rather than simply minimizing the distance between the snake’s head and the apples.

<figure style="margin: 0 auto; display: block; text-align: center;">
  <video style="width: 80%; height: auto;" autoplay loop muted>
    <source src="/videos/snake_final.mp4" type="video/mp4">
  </video>
  <figcaption style="font-size: 0.9em; color: gray; text-align: center;">
    CNN-based Reinforcement Learning for Snake game
  </figcaption>
</figure>



<h3>Sokoban game</h3>

Another strategy game but more complex. The agent needs to push the all boxes to the targets to complete the game. The environment includes: empty cell(white), box(red), goal(yellow), wall(black), occupied goal(green) and agent(blue). 
<div style="display: flex; justify-content: space-between; gap: 5px;">
  <figure style="text-align: center; width: 30%; margin: 0; margin-bottom: 20px;">
    <img src="/images/sokoban_1.png" 
         alt="Initial configuration" 
         title="Initial configuration" 
         style="width: 100%; height: auto; display: block; margin: 0 auto;" />
  </figure>

  <figure style="text-align: center; width: 30%; margin: 0; margin-bottom: 20px;">
    <img src="/images/sokoban_2.png" 
         alt="Complete first box" 
         title="Complete first box" 
         style="width: 100%; height: auto; display: block; margin: 0 auto;" />
  </figure>

  <figure style="text-align: center; width: 30%; margin: 0; margin-bottom: 20px;">
    <img src="/images/sokoban_3.png" 
         alt="Complete second box" 
         title="Complete second box" 
         style="width: 100%; height: auto; display: block; margin: 0 auto;" />
  </figure>
</div>

<figcaption style="font-size: 0.9em; color: gray; text-align: center;">
  Sokoban game
</figcaption>

Sokoban game requires more precise and strategic moves and the agent need to learn strategy to handle different maps. By automatically generating the solvable maps with different entity configurations and training on it, the agent may learn more complicated strategies.

<figure style="margin: 0 auto; display: block; text-align: center;">
  <img src="/images/training_sokoban.png" alt="Training agent with different map configurations" tiltle="Training agent with different map configurations" style="width: 70%; height: auto;"/>
  <figcaption style="font-size: 0.9em; color: gray;">
    Training agent with different map configurations
  </figcaption>
</figure>

I have combined CNN with some type of advanced Reinforcement learning Algorithm such as Proximal Policy Optimization (PPO), Soft Actor-Critic (SAC),... with different reward systems. However, due to the high complexity of the problem, the agent struggles to generalize and find effective strategies when operating in unseen maps.
<figure style="margin: 0 auto; display: block; text-align: center;">
  <video style="width: 80%; height: auto;" autoplay loop muted>
    <source src="/videos/sokoban_2b.mp4" type="video/mp4">
  </video>
  <figcaption style="font-size: 0.9em; color: gray; text-align: center;">
    Leaning process
  </figcaption>
</figure>