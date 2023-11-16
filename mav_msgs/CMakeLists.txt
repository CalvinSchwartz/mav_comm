cmake_minimum_required(VERSION 3.5)
project(mav_msgs)

find_package(rosidl_default_generators REQUIRED)
find_package(ament_cmake REQUIRED)
find_package(geometry_msgs)

find_package(Eigen3)
set(CMAKE_CXX_STANDARD 14)
set(EIGEN3_INCLUDE_DIRS ${EIGEN3_INCLUDE_DIR})

add_definitions(-std=c++14)
rosidl_generate_interfaces(
    ${PROJECT_NAME}
        msg/Status.msg
        msg/TorqueThrust.msg
        msg/GpsWaypoint.msg
        msg/AttitudeThrust.msg
        msg/RateThrust.msg
        msg/FilteredSensorData.msg
        msg/Actuators.msg
        msg/RollPitchYawrateThrust.msg
    DEPENDENCIES
        geometry_msgs
)
include_directories(include)

ament_export_include_directories(include ${EIGEN3_INCLUDE_DIRS})
ament_export_dependencies(std_msgs geometry_msgs trajectory_msgs nav_msgs)
ament_package()

install(
  DIRECTORY include/${PROJECT_NAME}/
  DESTINATION include/${PROJECT_NAME}
  FILES_MATCHING PATTERN "*.h"
)
