# Self driving car simulation

This repo contains code to drive a Toyota Prius autonomously using the lanes and stop markers detected in the image from the car's front camera, stopping if obstacles are detected, and navigating to a user-set goal.

## Setup

`cd ~/catkin_ws/src`

`git clone https://github.com/erundeddu/self_driving_cars`

`cd ~/catkin_ws`

`catkin_make`

Resource the workspace (in The Construct Sim, close the terminal window and open a new terminal window)

## Standard use

### Launch all nodes

`roslaunch self_driving self_driving.launch follow_lanes:=true pedestrians_img_detect:=false`

Open Gazebo and Desktop Viewer.

### Go to Landmarks

* `rosservice call destination_landmark x` can be used to move the vehicle autonomously to a landmark, only taking right turns
    * `x = 1`: house
    * `x = 2`: law office
    * `x = 3`: construction cone
    * `x = 4`: school
    * `x = 5`: suv

## Other available services

* `rosservice call enable_driving 1` can be used to start moving the vehicle autonomously and drive continuously by always taking right turns

* `rosservice call enable_driving 0` puts the vehicle in braking and stops autonomous motion

* `rosservice call destination -- x y` navigate autonomously toward the destination at (x, y) coordinates expressed in the Gazebo reference frame, only taking right turns
    * This command will work correctly if (x,y) is a point on the road that can be reached 
    * if (x,y) is at an intersection, calling the service a second time may be unsuccessful
    * the `--` is needed in case x or y are negative numbers


## Other launchfile options

Enable detection of pedestrians with front camera, currently this sometimes gives false positives at the landmarks

`roslaunch self_driving self_driving.launch follow_lanes:=true pedestrians_img_detect:=true`


To move the Prius manually (can be used to test image processing algorithms in various locations of the world):

`roslaunch self_driving self_driving.launch follow_lanes:=false pedestrians_img_detect:=false`

In a new terminal window:

`roslaunch prius_teleop prius_teleop.launch`

This launches the `prius_teleop` node. The user can control the car by pressing keys in the second terminal window.

## Packages used and included in this repo

https://github.com/osrf/car_demo, accessed June 7, 2021
* prius_description: commented some Gazebo plugins to improve fps
* prius_msgs: included as is
* prius_plugins: restructured into its own ROS package

