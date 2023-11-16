cmake_minimum_required(VERSION 2.8.3)
project(mav_msgs)

find_package(catkin REQUIRED message_generation std_msgs geometry_msgs trajectory_msgs nav_msgs)
include_directories(include ${catkin_INCLUDE_DIRS})

find_package(Eigen3)
set(EIGEN3_INCLUDE_DIRS ${EIGEN3_INCLUDE_DIR})

add_definitions(-std=c++11)

add_message_files(
  FILES
  Actuators.msg
  AttitudeThrust.msg
  RateThrust.msg
  RollPitchYawrateThrust.msg
  TorqueThrust.msg
  Status.msg
  FilteredSensorData.msg
  GpsWaypoint.msg
)

generate_messages(DEPENDENCIES std_msgs geometry_msgs nav_msgs)

catkin_package(
  INCLUDE_DIRS include ${EIGEN3_INCLUDE_DIRS}
  CATKIN_DEPENDS message_runtime std_msgs geometry_msgs trajectory_msgs nav_msgs
  CFG_EXTRAS export_flags.cmake
)

install(
  DIRECTORY include/${PROJECT_NAME}/
  DESTINATION include/${PROJECT_NAME}
  FILES_MATCHING PATTERN "*.h"
)
