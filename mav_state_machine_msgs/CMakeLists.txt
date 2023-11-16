cmake_minimum_required(VERSION 3.5)
project(mav_state_machine_msgs)

find_package(rosidl_default_generators REQUIRED)
find_package(ament_cmake REQUIRED)
find_package(std_msgs REQUIRED)
set(CMAKE_CXX_STANDARD 14)
rosidl_generate_interfaces(
    ${PROJECT_NAME}
        srv/RunTaskService.srv
        msg/StartStopTask.msg
    DEPENDENCIES
        
)
include_directories(include)

ament_package()
