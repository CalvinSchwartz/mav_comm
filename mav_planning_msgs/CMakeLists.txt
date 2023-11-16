cmake_minimum_required(VERSION 3.5)
project(mav_planning_msgs)

find_package(rosidl_default_generators REQUIRED)
find_package(ament_cmake REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(std_msgs REQUIRED)
find_package(mav_msgs REQUIRED)
find_package(trajectory_msgs REQUIRED)

find_package(Eigen3 QUIET)
set(CMAKE_CXX_STANDARD 14)
rosidl_generate_interfaces(
    ${PROJECT_NAME}
        srv/PlannerService.srv
        srv/ChangeNameService.srv
        srv/PolygonService.srv
        msg/Point2D.msg
        msg/PolynomialTrajectory4D.msg
        msg/PolygonWithHoles.msg
        msg/PolygonWithHolesStamped.msg
        msg/PolynomialTrajectory.msg
        msg/Polygon2D.msg
        msg/PointCloudWithPose.msg
        msg/PolynomialSegment4D.msg
        msg/PolynomialSegment.msg
    DEPENDENCIES
        sensor_msgs
        geometry_msgs
        trajectory_msgs
)
include_directories(include)

ament_export_include_directories(include ${EIGEN3_INCLUDE_DIRS})
ament_export_dependencies(geometry_msgs sensor_msgs std_msgs mav_msgs trajectory_msgs)
ament_package()