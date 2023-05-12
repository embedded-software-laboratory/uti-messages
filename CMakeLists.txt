cmake_minimum_required(VERSION 3.8)
project(ula_msgs)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(geometry_msgs REQUIRED)

include_directories(include/ula_msgs)

rosidl_generate_interfaces(${PROJECT_NAME}
  "msg/Ready.msg"
  "msg/Speed.msg"
  "msg/VehicleID.msg"
  "msg/VehicleIDs.msg"
  "msg/VehicleState.msg"
  "msg/VehicleStateList.msg"
  "msg/TrajectoryPoint.msg"
  "msg/TrajectoryCommand.msg"
  "srv/CollectedVehicleStateList.srv"
  "srv/LabProperties.srv"
  "srv/MapDefinition.srv"
  "srv/MapRequest.srv"
  "srv/NeededVehicles.srv"
  "srv/ScaleRegistration.srv"
  "srv/StoredTrajectoryCommand.srv"
  "action/VehiclesRequest.action"
  DEPENDENCIES builtin_interfaces geometry_msgs
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # comment the line when a copyright and license is added to all source files
  set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # comment the line when this package is in a git repo and when
  # a copyright and license is added to all source files
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
