# Self Driving code

This package contains all code to extract data from the car sensors (camera, sonar, position) and send commands to the car to drive the vehicle autonomously.

Description of nodes:
* `lanes`: processes image from front camera to identify and classify street lines and stop markers
* `obstacles_cv`: detects obstacles (pedestrians) by processing images from the front camera
* `obstacles`: detects obstacles by processing front sonar readings
* `steering`: uses sensor information to drive the car continuously or to a location of interest