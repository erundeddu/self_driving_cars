# Lane following and obstace-avoiding autonomous vehicle

This repo contains code to drive a Toyota Prius autonomously given the lanes detected in the image from the car's front camera.


`cd ~/catkin_ws/src`

`git clone https://github.com/erundeddu/self_driving_cars`

`cd ~/catkin_ws`

`catkin_make`

Resource the workspace

`roslaunch self_driving self_driving.launch follow_lanes:=true`

Open Gazebo and Desktop Viewer.

`rosservice call enable_driving 1` can be used to start moving the vehicle autonomously

`rosservice call enable_driving 0` puts the vehicle in braking and stops autonomous motion

To move the Prius manually (can be used to test image processing algorithms in various locations of the world):

`roslaunch self_driving self_driving.launch follow_lanes:=false`

This launches the `prius_teleop` node. The user can control the car by pressing keys in the terminal.