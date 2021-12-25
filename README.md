### How to create Docker Container for SoyNet test

This section describes the process of creating a docker container image using Dockerfile for x86 (Ubuntu 18.04) and Jetson Nano (JetPack 4.4) to configure the environment required to run the AI model demo using SoyNet. However, since SoyNet demo is not included in this docker container, refer to the following link.

- SoyNet demo repo: [https://github.com/soynet-support/demo_yolo](https://github.com/soynet-support/demo_yolo)

### Needs

### Pre-requisite packages

- docker
- nvidia-docker2

### Ubuntu 18.04

1.Download and run Dockerfile

$ git clone [https://github.com/zaiin4050/demo_docker](https://github.com/zaiin4050/demo_docker)
$ cd demo_docker

### 1.dockerfile download and executre

# for x86 ubuntu 18.04, 

$ docker build -t trt20.12-py:demo -f Dockerfile.x86 .
$ docker images

### 2. docker to host display setting

# This part is to visually check the results of inference in docker.

$ xhost +local:docker

### 3.Run docker container

# For x86 ubuntu 18.04,

$ sudo docker run -ti -e DISPLAY=$DISPLAY \
-v /tmp/.X11-unix:/tmp/.X11-unix \
-e USER=$USER \
--runtime=nvidia \
--gpus all \
--name demo \
trt20.12-py:demo bash
