FROM osrf/ros:humble-desktop-full

RUN apt-get update && apt-get install -y nano && rm -rf /var/lib/apt/lists/*

COPY config/ /site_config/

ARG USERNAME=ros
ARG USER_UID=1000
ARG USER_GID=$USER_UID

#creating a non-root user 

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd -s /bin/bash --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && mkdir /home/$USERNAME/.config && chown $USER_UID:$USER_GID /home/$USERNAME/.config


# USER ros

RUN apt-get update \
&& apt-get install -y sudo \
&& echo ${USERNAME} ALL=\(root\) NOPASSSWORD:ALL > etc/sudoers.d/${USERNAME}\
&& chmod 0440 /etc/sudoers.d/${USERNAME} \
&& rm -rf /var/lib/apt/lists/* 