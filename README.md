# Auto_Race-Car

<figure>
  <img
  src="https://github.com/must23/Auto_Race-Car/blob/main/docs/car_topview.png"
  alt="Figure 1 rqt graph showing the nodes used in the auto_race-car.">
</figure>

This project contains the necessary launch files and yaml parameters filets to run the navigation stack and TEB planner using RPLidar, Zed-camera for pose estimation and odometry, and PCA9685 motor drivers. The goal of this project is to transform a remote control car into an autonomous race car on jetson device as in F1TENTH Autonomous Racing build [Link](https://f1tenth.org/build.html). There are several tweaks from changing the PCA9656 driver address to designing propriate ROS move base parameters to fit with the physical parameter of the RC. Figures 1 the rqt graph for the setup nodes. The recorder rviz and actual implementation video can be seen in the following [Link](https://f1tenth.org/build.html).
<figure>
  <img
  src="https://github.com/must23/Auto_Race-Car/blob/main/docs/rosgraph_.png"
  alt="Figure 1 rqt graph showing the nodes used in the auto_race-car.">
  <figcaption>Figure 1 rqt graph showing the nodes used in the auto_race-car</figcaption>
</figure>


## Required packages
- [ROS navigation stack](https://github.com/ros-planning/navigation)
- [TEB local path planner](https://github.com/rst-tu-dortmund/teb_local_planner)
- [GMapping package](https://github.com/ros-perception/slam_gmapping)
- [Ackermann package](https://github.com/ros-drivers/ackermann_msgs)
- [PCA9685 motor driver](https://github.com/adafruit/Adafruit_CircuitPython_PCA9685)
- [Zed-2 camera driver](https://github.com/stereolabs/zed-ros-wrapper)

## Important files
- `my_robot_name_2dnav/launch/move_base.launch`: To run the move base default navigation stack from ROS and TEB local path planner 
- `my_robot_name_2dnav/config/base_local_planner_params.yaml`: This file contains parameter setting to run the ROS navigation stack 
- `ros_pca9685_drive/config/pca9685.yaml` : File contains parameters for the motor driver to set values such as published topic, the i2cbase address, and throttle range.
- `ros_pca9685_drive/launch/pca9685_drive.launch`: This file launches a ROS to execute pca9685_node.py"and run the motor driver. 
- `rplidar_ros/launch/view_rplidar.launch`: This file simultaneously runs SLAM gmapping, rplidar and Zed Camera as well as rviz visualization.

## Procedure to replicate experiment
1.	Clone the necessary packages into the src folder and build the packages using catkin_make command
2.	Add the important files mentioned above in the respective directories.
3.	Tweak the configuration and parameter values, especially the physical size of the car and the distance to the lidar/IMU (here, we use Zed camera’s odom topic)
4.	Construct mapping and save it to the local directory to use later.
5.	Launch pca9685_drive.launch, view_rplidar.launch, and move_base.launch respectively. If the laser_scan topic is not available, give permission to access the LiDAR port (e.g., sudo chmod 666 /dev/USBtty0) 
6.	Set the goal point on the rviz to run autonomous navigation. 
