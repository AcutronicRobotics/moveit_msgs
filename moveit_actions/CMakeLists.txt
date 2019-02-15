cmake_minimum_required(VERSION 3.5)
project(moveit_actions)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wextra -Wpedantic")
endif()

find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(action_msgs REQUIRED)
find_package(moveit_msgs REQUIRED)

set(action_files
  "action/ExecuteTrajectory.action"
  "action/MoveGroup.action"
  "action/Pickup.action"
  "action/Place.action"
)

rosidl_generate_interfaces(${PROJECT_NAME}
  ${action_files}
  DEPENDENCIES
    action_msgs
    moveit_msgs
)

ament_package()
