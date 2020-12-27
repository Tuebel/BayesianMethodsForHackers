# @license BSD-3 https://opensource.org/licenses/BSD-3-Clause
# Copyright (c) 2020, Tim Redick
# All rights reserved. 

# Multi Stage Build: First pull julia image and copy the artifacts to the cudagl image
FROM julia:buster AS julia_img

# CudaGL
FROM nvidia/cudagl:11.0-devel-ubuntu20.04
ENV JULIA_PATH /usr/local/julia
ENV PATH $JULIA_PATH/bin:$PATH
COPY --from=julia_img $JULIA_PATH $JULIA_PATH

# dev tools
RUN curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | bash
RUN apt-get update && apt-get install -y curl git git-lfs

# IJulia
RUN curl https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -o /tmp/miniconda.sh
RUN chmod +x /tmp/miniconda.sh && \
  /tmp/miniconda.sh -b && \
  rm /tmp/miniconda.sh
ENV PATH="/root/miniconda3/bin:${PATH}"
RUN conda install -c conda-forge jupyterlab -y
COPY install_ijulia.jl /tmp/install_ijulia.jl
RUN julia /tmp/install_ijulia.jl && \
  rm /tmp/install_ijulia.jl
