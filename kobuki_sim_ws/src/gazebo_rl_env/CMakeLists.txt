cmake_minimum_required(VERSION 3.8)
project(gazebo_rl_env)

# Find dependencies
find_package(ament_cmake REQUIRED)
find_package(ament_cmake_python REQUIRED)
find_package(rclpy REQUIRED)

# Install files
install(DIRECTORY launch DESTINATION share/${PROJECT_NAME})

ament_package()
