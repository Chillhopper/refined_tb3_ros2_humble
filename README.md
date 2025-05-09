# refined_tb3_ros2_humble
ros2 launch my_map_cpp_package my_map.launch.py map:=/home/rosi/map.yaml

export TURTLEBOT3_MODEL=burger
source install/setup.bash
ros2 launch my_map_cpp_package my_map.launch.py 

source install/setup.bash
ros2 launch my_map_cpp_package carto.launch.py

export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_cartographer cartographer.launch.py use_sim_time:=True

export TURTLEBOT3_MODEL=burger
ros2 run turtlebot3_teleop teleop_keyboard

^^^^^^^^^^^^^MY PACKAGE^^^^^^^^^^^^^^^^
