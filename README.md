# Wildcat SLAM

This is an unofficial demonstrative implentation of Wildcat SLAM which is described in the following paper:  
```
@article{ramezani2022wildcat,
  title={Wildcat: Online continuous-time 3d lidar-inertial slam},
  author={Ramezani, Milad and Khosoussi, Kasra and Catt, Gavin and Moghadam, Peyman and Williams, Jason and Borges, Paulo and Pauling, Fred and Kottege, Navinda},
  journal={arXiv preprint arXiv:2205.12595},
  year={2022}
}
```

![pic1](pics/surfels_in_sliding_window.jpg)
![pic2](pics/point_cloud_accumulated.jpg)

## 1. Prerequisites
### 1.1 **Ubuntu** and **ROS**
Recommend: Ubuntu 20.04 and [ROS Noetic](http://wiki.ros.org/ROS/Installation).

### 1.2. Dependencies
**Ceres Solver**
```shell
sudo apt install libceres-dev
```
**PCL**
```shell
sudo apt install libpcl-dev
```
**fmt**
```shell
sudo apt install libfmt-dev
```
**libbenchmark-dev**
```shell
sudo apt install libbenchmark-dev
```
**protobuf**
```shell
sudo apt install protobuf-compiler
```

## 2. Build Wildcat SLAM
Clone the repository and catkin_make.

## 3. License
GPLv3.

## Build Docker Image and run Docker container
docker build -t wildcat-slam:noetic .

docker run -it --rm -v C:\Users\YourName\data:/shared wildcat-slam:noetic

## 5. Run & Visualize in Rviz
Run RViz on Windows: Use an X server (like VcXsrv), set $env:DISPLAY, and run rviz inside the container.

roslaunch wildcat_slam run.launch

Summary of Active Topics
/scan_in_imu_frame (PointCloud2) – Enabled
/initialpose (used by the 2D Pose Estimate tool)
/move_base_simple/goal (used by the 2D Nav Goal tool)
/clicked_point (used by the Publish Point tool)
Disabled by Default (would need to be enabled in RViz):

/hesai/pandar (PointCloud2) – disabled in the config
/current_planes (MarkerArray) – disabled in the config