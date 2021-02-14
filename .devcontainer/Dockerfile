# [Choice] Debian version: buster, stretch
ARG VARIANT=buster
FROM mcr.microsoft.com/vscode/devcontainers/base:${VARIANT}

# ** [Optional] Uncomment this section to install additional packages. **
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
        python2 \
        xz-utils \
        build-essential \
        file \
        gcc-arm-linux-gnueabihf \
        g++-8-arm-linux-gnueabihf \
        libdw-dev \
        libunwind8-dev \
        systemtap-sdt-dev \
        libaudit-dev
