cmake_minimum_required(VERSION 2.8.3)
project(bramblebee_base)

find_package(catkin REQUIRED COMPONENTS controller_manager hardware_interface husky_msgs
  diagnostic_updater roslaunch roslint roscpp sensor_msgs)
find_package(Boost REQUIRED COMPONENTS chrono)

catkin_package(
  CATKIN_DEPENDS diagnostic_updater hardware_interface husky_msgs roscpp sensor_msgs
  DEPENDS Boost
)
set_directory_properties(PROPERTIES COMPILE_OPTIONS "-std=c++11;")
