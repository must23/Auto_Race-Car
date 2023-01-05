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
- `move_base.launch`: dir: my_robot_name_2dnav/launch/, To run move base default navigation stack from ROS and TEB local path planner 
- `dataset.py`: A helper class for training takes images and targets dataset, then provides pair-batches of the dataset during the training process.
- `models.py`: This file contains an implementation of the U-Net modified version.
- `prediction.py`: This file applies the saved trained semantic segmentation model to a video. It generates a new video with the segmentation results. 
- `imageprocessing.py`: This file generates semantic segmentation masks given a label segmentation image. The masks are provided in separated folders based on the class name.

## Procedure to replicate experiment
<!-- ## Experiment (1): One-Class Semantic Segmentation.
In this experiment, a semantic segmentation for one class is done by approaching cars as a target class. The training is only applied on 5K~8K images and 1.2~1.5K images as a validation dataset. The experiement code is provided in `vehicle-segmentation` folder. The pixel accuracy reachs to 87%. The trained model is applied on a video recorded in Dubai, UAE.


## Experiment (2): Multi-Classes Semantic Segmentation.
In this experiment, we consider five classes: road, sidewalk, curb, crosswalk, and lane line. The experiement code is provided in `sidewalk-segmentation` folder. The accuracy reaches 95% pixel accuracy. 
![alt text]([https://user-images.githubusercontent.com/20774864/147135092-ecad45f3-a57a-4abe-a918-adecd7c193c2.PNG](https://github.com/must23/Auto_Race-Car/blob/main/docs/rosgraph_.png)) -->
