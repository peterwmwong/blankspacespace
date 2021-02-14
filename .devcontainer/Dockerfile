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

RUN cd /home/vscode/workspace \
    && mkdir kernel && cd kernel \
    && git clone --depth 1 git://git.kernel.org/pub/scm/linux/kernel/git/tip/tip.git \
    && cd tip/tools/perf \
    && make \
    && ln -s /home/vscode/workspace/kernel/tip/tools/perf/perf /usr/bin/perf

RUN cd /home/vscode/workspace \
    && git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git \
    && export PATH=/home/vscode/workspace/depot_tools:$PATH \
    && mkdir v8 && cd v8 \
    && fetch v8 \
    && cd v8 \
    && build/install-build-deps.sh
