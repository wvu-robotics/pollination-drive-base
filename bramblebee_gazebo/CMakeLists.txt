cmake_minimum_required(VERSION 2.8.3)
project(bramblebee_gazebo)

find_package(catkin REQUIRED COMPONENTS
  roslaunch
  roscpp
  sensor_msgs
  tf
  gazebo_ros
)

find_package(gazebo REQUIRED)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${GAZEBO_CXX_FLAGS}")

catkin_package(
  INCLUDE_DIRS include
  LIBRARIES gazebo_ros_velodyne_laser
  CATKIN_DEPENDS roscpp sensor_msgs gazebo_ros
  DEPENDS GAZEBO
)

catkin_add_env_hooks(50.bramblebee_gazebo
  SHELLS sh DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/env-hooks)

roslaunch_add_file_check(launch)

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
  ${GAZEBO_INCLUDE_DIRS}
)

link_directories(
  ${GAZEBO_LIBRARY_DIRS}
)

add_library(gazebo_ros_velodyne_laser src/GazeboRosVelodyneLaser.cpp)
target_link_libraries(gazebo_ros_velodyne_laser
  ${catkin_LIBRARIES}
  ${GAZEBO_LIBRARIES}
  RayPlugin
)

install(TARGETS gazebo_ros_velodyne_laser
        LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
)

install(DIRECTORY include/${PROJECT_NAME}/
        DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
)

install(
  DIRECTORY launch urdf worlds
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)
