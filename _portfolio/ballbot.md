---
title: "Advanced Controls for Ballbot system (Ball-balancing robot system)"
#excerpt: "Short description of portfolio item number 1<br/><img src='/images/500x300.png'>"
collection: portfolio
category: major
permalink: /portfolio/ballbot
lab: "Motion Control and Applied Robotics Laboratory (MoCAR)"
venue: "Hanoi University of Science and Technology"
supervisor: "Supervisors: Assoc. Prof. Nguyen Tung Lam, Dr. Thi-Van-Anh Nguyen"
---

This is the project that I had implemented since the second university year, it is also my main subject in my Bachelor's Thesis. At that time, ballbot was a new type of robot, there was still little in-depth research as well as application of this interesting robot in practice. That was also the reason that motivated me and my team to choose and research this topic.

Ballbot system
======
This is a mobile robot based on the concept of inverted pendulum with the ability to move in all directions on the ground. The robot is normally about the size of a person's chest, so it can easily interact with humans in working environments.
The general structure of the ballbot includes 3 main parts: the upper body, the spherical structure for multi-directional movement, and the transmission mechanism for the ball (in our scope of research, we focus on the the 3-omniwheel structure because of its more superior flexibility).

<figure style="text-align: center; margin: 0 auto; display: block;">
  <img src="/images/ballbot_figure.png" alt="Basic design of ballbot system with three main parts" tiltle="Basic design of ballbot system with three main parts" style="width: 50%; height: auto;" />
  <figcaption style="font-size: 0.9em; color: gray;">
    Basic design of ballbot system with three main parts
  </figcaption>
</figure>

Thus, with such a general structure, we can see some of the great advantages of this type of robot as follows:
- Moving/changing direction in narrow environments: Compared to conventional multi-wheel robots, the balanced design on only one ball helps Ballbot significantly reduce its size on ground. Moreover, due to the inherent flexibility of the sphere, ballbot can easily move in all directions without requiring a minimum turning radius.

<figure style="margin: 0 auto; display: block; text-align: center;">
  <img src="/images/advantage_1.png" alt="Comparison between the differential drive robot and the ballbot" tiltle="Comparison between the differential drive robot and the ballbot" style="width: 75%; height: auto;"/>
  <figcaption style="font-size: 0.9em; color: gray;">
    Comparison between the differential drive robot and the ballbot
  </figcaption>
</figure>

- Maintaining balance by adjust center of gravity of the body: In reality, mobile robots will have to perform complex tasks: moving on inclined surfaces, carrying asymmetrical loads, bearing the external forces,... With a high body design, these robots will easily tilt and deviate from the center of inertia outside the base area. Thanks to the separate design between the body and the ball, the ballbot can adjust the body angle to ensure that the center of gravity is almost coincident with the gravitational acceleration vector. On the contrary, in the case of conventional robots, the height will make them susceptible to the above impacts and there is no mechanism to ensure safety.

<figure style="margin: 0 auto; display: block; text-align: center;">
  <img src="/images/advantage_2.png" alt="Comparison the performance of the ballbot with other human-like robot" tiltle="Comparison the performance of the ballbot with other human-like robot" style="width: 75%; height: auto;"/>
  <figcaption style="font-size: 0.9em; color: gray;">
    Comparison the performance of the ballbot with other human-like robot
  </figcaption>
</figure>

Some recent interesting application of ballbot:
- Assistant robot: Taking advantage of the ability to move flexibly and the height equal to humans, the Ballbot is very suitable in narrow and crowded environments.
Refer to: [CMU_Application](https://www.youtube.com/watch?v=8BtDuzu2WeI)

- Self-balancing wheelchair: no need for manual control, this design takes advantage of the ability to self-balance when the user just needs to lean in the desired direction and the vehicle will move in that direction to bring the center of gravity under the base. 
Refer to: [Hand-free wheelchair](https://www.youtube.com/watch?v=DPmptZcZGVc)

Modeling
======
Three omniwheels in contact with the ball will create 3 moments making the ball perform 3 simultaneous movements: move along the x-axis, move along the y-axis and rotate around z-axis. Thus, to describe these movements separately, 3 actual moments will be converted into 3 virtual moments which are perpendicular with each other and parallel to the 3 coordinate axes respectively. After conversion, the 3D model can be separated into three 2D models in three planes, each model describes a part of the system's movement: model in Oxz describes the movement along Ox-axis, model in Oyz describes the movement along Oy-axis, and the Oxy represents the rotational movement.

<figure style="margin: 0 auto; display: block; text-align: center;">
  <img src="/images/decomposing.png" alt="Ballbot system decomposing concept" tiltle="Ballbot system decomposing concept" style="width: 100%; height: auto;"/>
  <figcaption style="font-size: 0.9em; color: gray;">
    Ballbot system decomposing concept
  </figcaption>
</figure>

Euler Lagrange equation are used to build the motion equation by calculating the total energy of the system through 3 main parts: rotational and translational kinetic energy of the ball, rotational and translational kinetic energy + potential energy of the body, rotational kinetic energy of the wheel. For the 2D model, the input is the virtual moment corresponding to the relevant plane, the output has 2 variables: the position of the ball and the deflection angle of the body. For the 3D system, the input is 3 actual moments of 3 wheels, the output is 5 variables, 2 for the position in ground and 3 for the Euler angles of the body.

Control structure
======
Ballbot is an underactuated system (the number of input variables is less than the number of output variables). The control objectives is ensuring the smooth movement of ballbot on the ground (trajectory tracking or position tracking or obstacle avoidance,...) while ensuring the balance state of the body on the ball during entire moving process. Thus, this system requires more complex control strategy and precise control parameters. Our research focus on nonlinear control structure to enhance model accuracy and avoid linearization. Currently, we have 2 approaches, aka core controllers for solving this problem: Hierarchical Sliding Mode Control (HSMC Approach) and Nonlinear Model Predictive Control (NMPC Approach). 
- HSMC Approach: This controller will take the responsibility for balancing control and tracking control. Based on the model decomposing concept, instead of applying directly HSMC to the 3D model, we implement HSMC on the simpler 2D Ballbot models. The reasons is that the complicated underactuated 3D model are extremely sensitive with control parameters (all of our simulations with HSMC for 3D model cannot guarentee the stability or converage to the low equipvelent point like the normal pendulum). We also apply Extended State Observer (ESO) are used to estimated the coupling interaction between 2D models, Control Barrier Function for safe control (limiting the deflection angle of body) and Flatness Theory for time-optimal trajactory generation. Foe more detailed, you can refer to [time-optimal HSMC](/publication/time_optimal) in Publications. 
- NMPC Approach: the main Benefits of NMPC, such as allowing prediction using nonlinear models,
optimizing system performance based on configurable goals, handling underactuated
systems, and especially the ability to manage and be developed based on constraints,
making it a viable and attractive option for complex and difficult-to-operate systems like
ballbot. By directing based on NMPC, the states of the ballbot are predicted then a
minimized problem is solved for an optimal trajectory and behavior of the ballbot.
Furthermore, the constraint in actuator capacities, maximum allowable tilt angles,
maximum velocities, obstacles, and maps can be added to the optimization problem to
achieve the optimal way. Comparing with HSMC, NMPC doesn't need the estimation of coupling components and pre-defined trajectory. You can find the detailed structure and combination with obstacle avoidance method in [NMPC_CBF_1](/publication/CBF_NMPC_ballbot).

Experiments
======
Beside working on research, my team has been applying control theory to the real Ballbot model. During my time at MoCAR Lab, we experimented with two versions of the Ballbot model.

The first version, which is relatively simpler, uses a DC servo motor with a 320 RPM, 24V, 60W, and a 13-pulse encoder. For data transmission and processing the main control algorithm, we used a C2000 MCU LaunchPad. Three pre-designed PID boards with H-bridge circuits were employed for speed control of DC motors, based on the control signals generated by the C2000. However, due to limitations in the design of the omniwheel system and its interaction with the ball, the performance of the three omniwheels was inconsistent, and they did not respond uniformly to the control signals."

<div style="display: flex; justify-content: space-between; gap: 10px;">
  <figure style="text-align: center; width: 45%; margin: 0; margin-bottom: 20px;">
    <img src="/images/real_ballbot_old_1.jpg" 
         alt="Basic design of ballbot system with three main parts" 
         title="Basic design of ballbot system with three main parts" 
         style="width: 100%; height: auto; display: block; margin: 0 auto;" />
  </figure>

  <figure style="text-align: center; width: 45%; margin: 0; margin-bottom: 20px;">
    <img src="/images/real_ballbot_old_2.jpg" 
         alt="Basic design of ballbot system with three main parts" 
         title="Basic design of ballbot system with three main parts" 
         style="width: 100%; height: auto; display: block; margin: 0 auto;" />
  </figure>
</div>
<figcaption style="font-size: 0.9em; color: gray; text-align: center;">
  Basic design of ballbot system with three main parts
</figcaption>

Version 2 has been improved in terms of mechanics, especially the omni-wheel structure, which is now more detailed and moves more smoothly when in contact with the ball.

<div style="display: flex; justify-content: space-between; gap: 10px;">
  <figure style="text-align: center; width: 45%; margin: 0; margin-bottom: 20px;">
    <img src="/images/real_ballbot_1.jpg" 
         alt="Basic design of ballbot system with three main parts" 
         title="Basic design of ballbot system with three main parts" 
         style="width: 100%; height: auto; display: block; margin: 0 auto;" />
  </figure>

  <figure style="text-align: center; width: 45%; margin: 0; margin-bottom: 20px;">
    <img src="/images/real_ballbot_2.jpg" 
         alt="Basic design of ballbot system with three main parts" 
         title="Basic design of ballbot system with three main parts" 
         style="width: 100%; height: auto; display: block; margin: 0 auto;" />
  </figure>
</div>
<figcaption style="font-size: 0.9em; color: gray; text-align: center;">
  Basic design of ballbot system with three main parts
</figcaption>

To address the shortcomings of the pre-designed PID board, we are using a more reliable control board, the MyRIO from National Instruments to control three AC Servo motors. Our control algorithm is designed in LabVIEW (including communication, signal filtering, calibration,...). Currently, the Ballbot project is still being developed and improved in terms of mechanical quality and controller.

<div style="display: flex; justify-content: space-between; gap: 10px;">
  <figure style="text-align: center; width: 45%; margin: 0; margin-bottom: 20px;">
    <img src="/images/real_ballbot_3.jpg" 
         alt="Basic design of ballbot system with three main parts" 
         title="Basic design of ballbot system with three main parts" 
         style="width: 100%; height: auto; display: block; margin: 0 auto;" />
  </figure>

  <figure style="text-align: center; width: 45%; margin: 0; margin-bottom: 20px;">
    <img src="/images/real_ballbot_4.png" 
         alt="Basic design of ballbot system with three main parts" 
         title="Basic design of ballbot system with three main parts" 
         style="width: 100%; height: auto; display: block; margin: 0 auto;" />
  </figure>
</div>

<figcaption style="font-size: 0.9em; color: gray; text-align: center;">
  Basic design of ballbot system with three main parts
</figcaption>
