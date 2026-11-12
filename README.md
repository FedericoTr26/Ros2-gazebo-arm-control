# ROS 2 Manipulator Simulation and Joint Control

A ROS 2 and Gazebo Sim project that brings a manipulator from URDF/Xacro visualization to simulated joint position control and camera streaming.

[Technical report and demo screenshots](RL_HW1.pdf)

## What we built

- Adapted the course manipulator description and replaced detailed collision meshes with simpler primitives.
- Configured simulated joint position interfaces, a joint state broadcaster, and a position controller for four joints.
- Added a simulated camera and bridged its images to ROS 2.
- Implemented a C++ node that reads joint states and sends a single position command to the controller.

## Run the demos

Use ROS 2 Humble with Gazebo Sim, RViz 2, Xacro, and `ros2_control`. The simulation uses `ros_gz_sim`, `ros_ign_bridge`, and `ign_ros2_control`. Install `rqt_image_view` to inspect the camera stream.

From the `src` directory of your ROS 2 workspace, clone the repository.

```bash
git clone https://github.com/FedericoTr26/RL_Homework-1.git
```

Return to the workspace root to build and source the workspace.

```bash
rosdep install -i --from-path src --rosdistro humble -y
colcon build
source install/setup.bash
```

Source `install/setup.bash` from the workspace root in each new terminal.

### Inspect the robot in RViz

```bash
ros2 launch arm_description display.launch.py
```

### Move the arm in Gazebo

Start the simulation in the first terminal.

```bash
ros2 launch arm_gazebo arm_gazebo.launch.py
```

Once the position controller is active, run the command node in a second terminal.

```bash
ros2 run arm_controller arm_controller_node
```

The node prints joint positions from `/joint_states` and sends the position command after five seconds. To view the camera stream, open the image viewer in a separate terminal and select `/videocamera`.

```bash
ros2 run rqt_image_view rqt_image_view
```

## Results

The report shows the robot in RViz, the simplified collision geometry, the live camera feed, and the arm after the four-joint position command. See Figures 1.1–1.2 for the model, Figures 3.1–3.3 for the camera, and Figures 4.1–4.2 for the command demo.

## Attribution

Developed as a group project for Robotics Lab using the course starter manipulator description.
