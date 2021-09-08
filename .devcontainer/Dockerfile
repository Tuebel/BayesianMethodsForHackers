# @license BSD-3 https://opensource.org/licenses/BSD-3-Clause
# Copyright (c) 2020, Tim Redick
# All rights reserved. 

FROM julia:buster

# dev tools
RUN apt-get update \
    && curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | bash \
    && apt-get install -y curl git git-lfs \
    && rm -rf /var/lib/apt/lists/*

# Miniconda for IJulia
ENV PATH="/root/miniconda3/bin:${PATH}"
RUN curl https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -o /tmp/miniconda.sh \
    && sh /tmp/miniconda.sh -b \
    && rm /tmp/miniconda.sh
RUN conda install -c conda-forge jupyterlab -y
COPY install_ijulia.jl /tmp/install_ijulia.jl

# Add IJulia to Project
RUN julia /tmp/install_ijulia.jl \
    && rm /tmp/install_ijulia.jl
