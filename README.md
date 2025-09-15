# nvidia-egl-desktop-ros2

## Introduction

This is a Dockerfile to use ROS 2 on KDE Plasma Desktop container with NVIDIA GPU.  
This Dockerfile is based on [selkies-project/docker-nvidia-egl-desktop](https://github.com/selkies-project/docker-nvidia-egl-desktop).

![](nvidia-egl-desktop-ros2-screenshot.png)

If you are interested in ROS 1 version, please check [atinfinity/nvidia-egl-desktop-ros](https://github.com/atinfinity/nvidia-egl-desktop-ros).

## Requirements

- NVIDIA graphics driver 450.80.02+ [^1]
- Docker
- NVIDIA Container Toolkit

## Build docker image

### ROS 2 Foxy

```bash
cd foxy
docker build -t nvidia-egl-desktop-ros2:foxy .
```

### ROS 2 Galactic

```bash
cd galactic
docker build -t nvidia-egl-desktop-ros2:galactic .
```

### ROS 2 Humble

```bash
cd humble
docker build -t nvidia-egl-desktop-ros2:humble .
```

### ROS 2 Jazzy

```bash
cd jazzy
docker build -t nvidia-egl-desktop-ros2:jazzy .
```

## Launch docker container

Execute the command described below.  
If you customize setting, please read <https://github.com/selkies-project/docker-nvidia-egl-desktop/blob/main/README.md>.

### ROS 2 Foxy

> [!NOTE]
> In this docker container, default account is `user`.  
> You can set password via `PASSWD` and `BASIC_AUTH_PASSWORD` when you execute `docker run`. The default password is `mypasswd`.  

```bash
docker run --gpus 1 -it --shm-size=1024m --pid=host -e SIZEW=1920 -e SIZEH=1080 -e PASSWD=mypasswd -e BASIC_AUTH_PASSWORD=mypasswd -e NOVNC_ENABLE=true -p 6080:8080 nvidia-egl-desktop-ros2:foxy
```

### ROS 2 Galactic

> [!NOTE]
> In this docker container, default account is `user`.  
> You can set password via `PASSWD` and `BASIC_AUTH_PASSWORD` when you execute `docker run`. The default password is `mypasswd`.  

```bash
docker run --gpus 1 -it --shm-size=1024m --pid=host -e SIZEW=1920 -e SIZEH=1080 -e PASSWD=mypasswd -e BASIC_AUTH_PASSWORD=mypasswd -e NOVNC_ENABLE=true -p 6080:8080 nvidia-egl-desktop-ros2:galactic
```

### ROS 2 Humble

> [!NOTE]
> In this docker container, default account is `user`.  
> You can set password via `PASSWD` and `BASIC_AUTH_PASSWORD` when you execute `docker run`. The default password is `mypasswd`.  

```bash
docker run --gpus 1 -it --shm-size=1024m --pid=host -e SIZEW=1920 -e SIZEH=1080 -e PASSWD=mypasswd -e BASIC_AUTH_PASSWORD=mypasswd -e NOVNC_ENABLE=true -p 6080:8080 nvidia-egl-desktop-ros2:humble
```

### ROS 2 Jazzy

> [!NOTE]
> In this docker container, default account is `ubuntu`.  
> You can set password via `PASSWD` and `SELKIES_BASIC_AUTH_PASSWORD` when you execute `docker run`. The default password is `mypasswd`.  

```bash
docker run --gpus 1 -it --shm-size=1024m --pid=host -e DISPLAY_SIZEW=1920 -e DISPLAY_SIZEH=1080 -e PASSWD=mypasswd -e SELKIES_BASIC_AUTH_PASSWORD=mypasswd -e SELKIES_ENABLE_RESIZE=true -e KASMVNC_ENABLE=true -p 6080:8080 nvidia-egl-desktop-ros2:jazzy
```

### Access KDE Plasma Desktop via web browser

Browse <http://127.0.0.1:6080/>.  

[^1]: <https://github.com/selkies-project/docker-nvidia-egl-desktop/blob/main/README.md>
