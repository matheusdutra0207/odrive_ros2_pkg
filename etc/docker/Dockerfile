FROM arm64v8/ros:humble

RUN apt update
RUN apt install -y usbutils net-tools software-properties-common wget
RUN apt-get install -y libjpeg-dev libjpeg8-dev libfreetype6-dev vim

RUN wget https://bootstrap.pypa.io/get-pip.py && python3 get-pip.py
RUN python3 -m pip install --upgrade odrive

RUN apt-get install -y ros-humble-diagnostic-updater
RUN apt-get install -y ros-humble-tf-transformations

WORKDIR /workspace/ros2_ws/src
RUN git clone https://github.com/matheusdutra0207/odrive_ros2_pkg.git

WORKDIR /workspace/ros2_ws
RUN colcon build --packages-select odrive_ros2_pkg

SHELL [ "/bin/bash" , "-c" ]
RUN source install/setup.bash
WORKDIR /workspace/ros2_ws/src/odrive_ros2_pkg
RUN python3 -m pip install .

WORKDIR /workspace/ros2_ws


