#FROM pytorch/pytorch:1.7.0-cuda11.0-cudnn8-runtime
FROM anibali/pytorch:1.7.0-cuda11.0-ubuntu20.04

ARG DEBIAN_FRONTEND=noninteractive

SHELL ["/bin/bash", "-c"]

# set time zone
ENV TZ=UTC
RUN sudo ln -snf /usr/share/zoneinfo/$TZ /etc/localtime

# ------------------------
# ------- ROS CORE -------
# ------------------------
# setup timezone
RUN sudo apt-get update && \
    sudo apt-get install -q -y --no-install-recommends tzdata apt-utils

# install packages
RUN sudo apt-get update && sudo apt-get install -q -y --no-install-recommends \
    dirmngr \
    gnupg2

# setup sources.list
RUN echo "deb http://packages.ros.org/ros/ubuntu focal main" | sudo tee /etc/apt/sources.list.d/ros1-latest.list

# setup keys
RUN sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654

# setup environment
ENV LANG C.UTF-8
ENV LC_ALL C.UTF-8

ENV ROS_DISTRO noetic

# install ros packages
RUN sudo apt-get update && sudo apt-get install -y --no-install-recommends \
    ros-noetic-ros-core=1.5.0-1*

# ------------------------
# ------- ROS BASE -------
# ------------------------
# install bootstrap tools
RUN sudo apt-get update && sudo apt-get install --no-install-recommends -y \
    build-essential \
    python3-rosdep \
    python3-rosinstall \
    python3-vcstools

# bootstrap rosdep
RUN sudo rosdep init && \
  rosdep update --rosdistro $ROS_DISTRO

# install ros packages
RUN sudo apt-get update && sudo apt-get install -y --no-install-recommends \
    ros-noetic-ros-base=1.5.0-1*

RUN sudo apt update && \
    sudo apt install -y zip htop screen libgl1-mesa-glx vim

RUN pip install Cpython opencv-python tqdm scipy pycocotools pyyaml

# RUN pip install seaborn thop

# RUN cd /app && \
#     git clone https://github.com/JunnYu/mish-cuda && \
#     cd mish-cuda && \
#     python setup.py build install

# RUN cd /app && \
#     git clone https://github.com/fbcotter/pytorch_wavelets && \
#     cd pytorch_wavelets && \
#     pip install .

CMD ["bash"]
