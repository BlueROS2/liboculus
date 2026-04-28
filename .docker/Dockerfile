ARG UBUNTU_VERSION=noble

#====================================================================
# Preliminary image with dependencies
#====================================================================
#
## This should work on both amd64 and arm64 through the magic of multi-arch?
FROM ubuntu:${UBUNTU_VERSION} AS deps

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
      cmake \
      gcc \
      git \
      libasio-dev \
      libboost-system-dev \
      libfmt-dev \
      libspdlog-dev \
      python-is-python3 \
      python3 \
      python3-apt \
      python3-pip \
    && apt autoremove -y \
    && apt clean -y \
    && rm -rf /var/lib/apt/lists/*

#RUN pip3 install distutils

#====================================================================
# Intermediate image with prereq steps for running in CI
#====================================================================
FROM deps as ci

# On more recent Ubuntu base images, a non-root
# user "ubuntu" already exists
ARG USERNAME=ubuntu
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN apt-get update \
  && apt-get install -y sudo \
  && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
  && chmod 0440 /etc/sudoers.d/$USERNAME

USER $USERNAME
WORKDIR /home/$USERNAME

CMD ["/bin/bash"]

#====================================================================
# Intermediate image with cloned Git repos
#====================================================================
FROM ci as git_checkout

ARG WS_DIR=/home/$USERNAME
WORKDIR ${WS_DIR}

ARG LIBOCULUS_REPO=https://github.com/apl-ocean-engineering/liboculus.git
ARG LIBOCULUS_BRANCH=main
RUN echo "Cloning from ${LIBOCULUS_BRANCH} branch ${LIBOCULUS_ROS_REPO}"

RUN git clone --depth 1 -b ${LIBOCULUS_BRANCH} ${LIBOCULUS_REPO}
