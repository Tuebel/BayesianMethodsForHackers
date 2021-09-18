# @license BSD-3 https://opensource.org/licenses/BSD-3-Clause
# Copyright (c) 2020, Tim Redick
# All rights reserved. 

FROM julia:buster

# dev tools
RUN apt-get update \
    && curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | bash \
    && apt-get install -y curl git git-lfs \
    && rm -rf /var/lib/apt/lists/*

# Non-root-user to avoid file permission problems
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME
USER $USERNAME

# IJUlia for non-root user
RUN curl https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -o /tmp/miniconda.sh \
    && sh /tmp/miniconda.sh -b -p /home/vscode/miniconda \
    && rm /tmp/miniconda.sh
ENV PATH="/home/vscode/miniconda/bin:${PATH}"
RUN conda init bash
RUN conda install -c conda-forge -y jupyterlab 
COPY install_ijulia.jl /tmp/install_ijulia.jl
RUN julia /tmp/install_ijulia.jl
