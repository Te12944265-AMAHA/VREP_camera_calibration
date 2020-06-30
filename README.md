# VREP Camera Calibration

This is a VREP scene driven by Lua script to automatically calibrate vision sensors using a robot arm.
## Prerequisits
1. Ubuntu 18.04
2. ROS Melodic
3. CoppeliaSim (VREP)

## Installation
1. Clone [vrep_comman](https://github.com/jocacace/vrep_common.git) and [vrep_plugin](https://github.com/jocacace/vrep_plugin.git) to catkin_ws and do catkin_make. Make sure to add link_directories in CMakeLists.txt in vrep_plugin, so that catkin_make works for ROS Melodic. Then copy devel/lib/libv_repExtRos.so to the main CoppeliaSim folder.

2. Put table_save_load.lua in the main CoppeliaSim folder.

3. Install camera_calibration package using

```bash
rosdep install camera_calibration
```

## Usage
[Demo video](https://drive.google.com/file/d/1uytOtvPoK4TTkAG8JTddCYmRFIGdj-49/view?usp=sharing)
1. Change the path variable in the scripts associate to Plane and LBR_iiwa_7_R800. It's where you want to save table of waypoints. To use pre-recorded waypoints which are enough for the calibration, change the path to the location of test-tbl.lua

2. Run calibrate_camera.ttt. To adjust joint angles, use the slide bars. To load, record, save, or play waypoints, use the buttons. Make sure to save the waypoints before playing.

3. Follow the [camera_calibration tutorial](http://wiki.ros.org/camera_calibration/Tutorials/MonocularCalibration) and run 

```bash
rosrun camera_calibration cameracalibrator.py --size 8x6 --square 0.0969 image:=/camera/image_raw camera:=/camera --no-service-check
```
