cmake_minimum_required(VERSION 3.8)
project(my_map_cpp_package)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(nav2_map_server REQUIRED)
find_package(rviz2 REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(lifecycle_msgs REQUIRED)
find_package(behaviortree_cpp_v3 REQUIRED)
find_package(image_transport)
find_package(OpenCV REQUIRED)
find_package(cv_bridge)
find_package(geometry_msgs REQUIRED)

include_directories(
  include
  ${OpenCV_INCLUDE_DIRS}
)


# Add Executable
add_executable(nav_main_node 

  src/nav_main.cpp

)

target_link_libraries(nav_main_node
  ${OpenCV_LIBS}
)


ament_target_dependencies(nav_main_node rclcpp nav_msgs geometry_msgs   behaviortree_cpp_v3 image_transport cv_bridge)

install(DIRECTORY 
  launch
  configs
  DESTINATION share/${PROJECT_NAME})

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
