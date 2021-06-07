cmake_minimum_required(VERSION 3.0.2)
project(self_driving)

find_package(catkin REQUIRED COMPONENTS
  prius_msgs
  message_generation 
)

add_service_files(
   FILES
   enable_driving.srv
   destination.srv
   destination_landmark.srv
)

## Generate added messages and services with any dependencies listed here
generate_messages(
  DEPENDENCIES
  #std_msgs  # Or other packages containing msgs
)

catkin_package(
 # INCLUDE_DIRS include
 # LIBRARIES gazebo_radar_plugin
 CATKIN_DEPENDS prius_msgs message_generation message_runtime
#  DEPENDS system_lib
)

include_directories(include ${catkin_INCLUDE_DIRS} ${GAZEBO_INCLUDE_DIRS} ${SDFormat_INCLUDE_DIRS})

catkin_install_python(PROGRAMS nodes/lanes
                      DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})

catkin_install_python(PROGRAMS nodes/steering
                      DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})

catkin_install_python(PROGRAMS nodes/obstacles
                      DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})

catkin_install_python(PROGRAMS nodes/obstacles_cv
                      DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})		

