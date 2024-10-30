# Homework 1

## :hammer: Build

Clone this package in the `src` folder of your ROS 2 workspace. Check for missing dependencies
```
$ git clone https://github.com/FedericoTr26/RL_Homework-1.git
```
```
$ rosdep install -i --from-path src --rosdistro humble -y
```
Build your new package

```
$ colcon build --packages-select RL_Homework-1
```
Source the setup files

```
$ source install/setup.bash
```
## :white_check_mark: Usage

## Run RViz 
```
$ ros2 launch arm_description display.launch.py
```

## Run manipulator with activated controllers in Gazebo
```
$ ros2 launch arm_gazebo arm_gazebo.launch.py
```

## Run camera on RQT
```
$ ros2 run rqt_image_view rqt_image_view
```

## Run the node to read the joint states and send joint position commands
on the second terminal:
```
$ ros2 run arm_controller arm_controller_node
```
