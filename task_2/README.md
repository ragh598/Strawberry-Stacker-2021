## Task 2.1 : Waypoint Navigation in Auto Mission Mode

## Overview
- Getting started with px4 firmware
- Learning about various modes
- Sending Waypoints to px4 via mavros

## Learning resources

- We highly recommend you to go through [px4 official documentation](https://docs.px4.io/main/en/simulation/) (following till Modules & Commands will be enough for this task) and for mavros go through [mavros px4 documentation](https://docs.px4.io/master/en/ros/ros1.html) before proceeding with the actual task as the learning curve might be steap in the start.
- This task will require the knowledge of custom modes, custom messages and mavros integration
- A walkthrough video is shared at the bottom of this page for tips and tricks do watch the video for getting familiar with px4 and MAVROS


## Problem statement
- You need to make the drone in Gazebo to follow 4 waypoints in the mission mode of px4
- Create a rosnode named waypoint_Mission in a python script, which will set the waypoints to be sent to px4
- You need to call the rosservice /mavros/cmd/arming to arm and /mavros/set_mode to set mode of the drone to mission mode
- Then you have to call the rosservice /mavros/mission/push and /mavros/mission/pull to Request parameter from device (or internal cache) and send parameters from ROS to FCU respectively.
- The waypoints are as follows
    - Takeoff at the home position to 10 meters
    - Go to 19.134641, 72.911706, 10
    - Go to 19.134617, 72.911886, 10
    - Go to 19.134434, 72.911817, 10
    - Go to 19.134423, 72.911763, 10
    - Land at the last coordinate

- Launch the Gazebo world by typing the following command in a terminal
```bash
roslaunch task_2 task2_1.launch
```
- Once the simulation window launches, you should see a drone in the gazebo environment.
- Run your python script in a separate terminal to start sending the waypoints and navigate the drone.

## Simulation
[Screencast from 22-03-23 12:32:17 AM IST.webm](https://user-images.githubusercontent.com/82602485/226963747-e2d0ab20-fcae-4ec9-b22c-304e96b9d5b2.webm)

## Task 2.2 : Navigation in Offboard Mode
## Overview
- Offboard mode is primarily used to control vehicle movement and attitude, and it only supports a subset of MAVLink messages. This mode requires position or pose/attitude information - e.g. GPS, optical flow, visual-inertial odometry, mocap, etc.

- In this task, we will be learning the following:

    - Controlling drone in Offboard Mode
    - Navigation in Offboard mode using setpoints.
- In the previous task, we learned how to control and navigate drone in Auto.Mission mode. Now, we will be using Offboard mode for the same. In place of waypoints we will be sending setpoints. Offboard mode help us to use drone using limited mavros messages.

## Learning resources

- We highly recommend you to go through [px4 official documentation](https://docs.px4.io/master/en/flight_modes/offboard.html), to get details about offboard mode.

## Problem statement
- You need to put the drone in Offboard mode and make a square of 10m x 10m.
- Takeoff from the ground and give the first setpoint as 0m,0m,10m
- Give the next setpoint as 10m,0m,10m followed by 10m,10m,10m followed by 0m,10m,10m and then back to 0m,0m,10m
- Finally land at the home position and disarm
- Keep the velocity of drone 5 m/s

## Procedure

- Launch the Gazebo world by typing the following command in a terminal
```bash
roslaunch task_2 task2_2.launch
```
- Once the simulation window launches, you should see a drone in the gazebo environment.
- Run your python script in a separate terminal to start sending the setpoints and navigate the drone.
 ## Simulation
 [Screencast from 22-03-23 12:15:19 AM IST.webm](https://user-images.githubusercontent.com/82602485/226965455-292b448a-f572-40c0-961c-223d3800550a.webm)

 
