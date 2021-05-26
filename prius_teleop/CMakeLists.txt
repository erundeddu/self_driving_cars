cmake_minimum_required(VERSION 2.8.3)
project(prius_teleop)

find_package(catkin REQUIRED COMPONENTS
  prius_msgs
)

catkin_package(
 # INCLUDE_DIRS include
 # LIBRARIES gazebo_radar_plugin
 CATKIN_DEPENDS prius_msgs
#  DEPENDS system_lib
)

include_directories(include ${catkin_INCLUDE_DIRS} ${GAZEBO_INCLUDE_DIRS} ${SDFormat_INCLUDE_DIRS})

catkin_install_python(PROGRAMS nodes/prius_teleop
                      DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})