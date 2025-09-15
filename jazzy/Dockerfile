FROM ghcr.io/selkies-project/nvidia-egl-desktop:24.04

SHELL ["/bin/bash", "-c"]
ENV DEBIAN_FRONTEND noninteractive
RUN sudo apt-get update && sudo apt-get install -y --no-install-recommends \
        curl \
        gnupg \
        lsb-release \
        less \
        emacs \
        tmux \
        bash-completion \
        command-not-found \
        software-properties-common \
        xdg-user-dirs \
        && \
    sudo apt-get clean && \
    sudo rm -rf /var/lib/apt/lists/*

# install ROS2 Jazzy
RUN export ROS_APT_SOURCE_VERSION=$(curl -s https://api.github.com/repos/ros-infrastructure/ros-apt-source/releases/latest | grep -F "tag_name" | awk -F\" '{print $4}') && \
    curl -L -o /tmp/ros2-apt-source.deb "https://github.com/ros-infrastructure/ros-apt-source/releases/download/${ROS_APT_SOURCE_VERSION}/ros2-apt-source_${ROS_APT_SOURCE_VERSION}.$(. /etc/os-release && echo $VERSION_CODENAME)_all.deb"  && \
    sudo dpkg -i /tmp/ros2-apt-source.deb

RUN sudo apt-get update && sudo apt-get install -y --no-install-recommends \
        ros-jazzy-desktop \
        ros-dev-tools \
        && \
    sudo apt-get clean && \
    sudo rm -rf /var/lib/apt/lists/*

# install colcon and rosdep
RUN sudo apt-get update && sudo apt-get install -y --no-install-recommends \
        python3-colcon-common-extensions \
        python3-rosdep \
        && \
    sudo apt-get clean && \
    sudo rm -rf /var/lib/apt/lists/*

# initialize rosdep
RUN sudo rosdep init && \
    rosdep update

RUN sudo-root rm /usr/bin/sudo && \ 
    sudo-root ln -snf /usr/bin/sudo-root /usr/bin/sudo && \
    sudo mandb

RUN echo "source /opt/ros/jazzy/setup.bash" >> ~/.bashrc

# disabled beep sound
RUN echo "set bell-style none" >> ~/.inputrc

RUN sudo rm /etc/apt/apt.conf.d/docker-clean
