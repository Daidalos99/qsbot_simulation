cmake_minimum_required(VERSION 3.0.2)
project(qs_bot)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  rviz
  std_msgs
  sensor_msgs
  geometry_msgs
  nav_msgs
  urdf
  xacro
  tf
  tf2
  gazebo_ros
  gazebo
)

find_package(gazebo REQUIRED)
link_directories(${GAZEBO_LIBRARY_DIRS})
include_directories(
  include
  ${Boost_INCLUDE_DIR}
  ${catkin_INCLUDE_DIRS}
  ${GAZEBO_INCLUDE_DIRS}
)
add_library(qs_bot_planar_move SHARED src/qs_bot_planar_move.cpp)
target_link_libraries(qs_bot_planar_move ${catkin_LIBRARIES} ${GAZEBO_LIBRARIES})
