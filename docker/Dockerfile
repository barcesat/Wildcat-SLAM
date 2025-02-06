# Start from the official ROS Noetic base (Ubuntu 20.04)
FROM ros:noetic-ros-base

# Avoid user interaction during package installation
ENV DEBIAN_FRONTEND=noninteractive

# Install required packages
#  - git for cloning
#  - tf for old transform library
#  - rviz if you want to visualize from inside the container
#  - other deps: ceres, pcl, fmt, etc.
RUN apt-get update && apt-get install -y \
    git \
    ros-noetic-tf \
    ros-noetic-rviz \
    ros-noetic-pcl-ros \
    ros-noetic-pcl-conversions \
    libceres-dev \
    libpcl-dev \
    libfmt-dev \
    libbenchmark-dev \
    protobuf-compiler \
    python3-catkin-tools \
    && rm -rf /var/lib/apt/lists/*

# Create a catkin workspace
RUN mkdir -p /catkin_ws/src
WORKDIR /catkin_ws/src

# Clone the Wildcat-SLAM repository with submodules
RUN git clone --recurse-submodules https://github.com/barcesat/Wildcat-SLAM.git

# Build Wildcat-SLAM
WORKDIR /catkin_ws
RUN /bin/bash -c "source /opt/ros/noetic/setup.bash && catkin_make"

# Source the workspace setup in every shell
RUN echo "source /catkin_ws/devel/setup.bash" >> /root/.bashrc

# Define a shared volume for data exchange (optional)
VOLUME ["/shared"]

# By default, launch a bash shell
CMD ["/bin/bash"]