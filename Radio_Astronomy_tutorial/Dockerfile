FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive \
    LC_ALL=C.UTF-8 \
    LANG=C.UTF-8

RUN apt-get update && apt-get install -y \
    software-properties-common \
    gfortran \
    git \
    htop \
    cmake \
    build-essential \
    python3 \
    python3-dev \
    python3-pip \
    python3-venv \
    libfreetype6-dev \
    libhdf5-dev \
    pkg-config \
    openmpi-bin \
    libopenmpi-dev \
    mpi-default-bin \
    vim \
    vim-gtk3 \
    mpich \
    xvfb \
    tar \
    wget \
    libcanberra-gtk-module \
    libcanberra-gtk3-module && \
    apt-get clean

RUN add-apt-repository -s ppa:kernsuite/kern-9 && \
    apt-add-repository multiverse && \
    apt-add-repository restricted && \
    apt-get update && \
    apt-get install -y \
    python3-casacore \
    aoflagger-dev \
    casacore-dev g++ \
    libblas-dev \
    libboost-date-time-dev libboost-filesystem-dev \
    libboost-program-options-dev libboost-system-dev \
    libcfitsio-dev libfftw3-dev libgsl-dev \
    liblapack-dev libopenmpi-dev \
    libpython3-dev && \
    apt-get clean


RUN cd /opt && \
    wget https://gitlab.com/aroffringa/wsclean/-/package_files/140629243/download -O wsclean.tar.gz && \
    tar -xvf wsclean.tar.gz && \
    cd wsclean-v3.5 && \
    mkdir -p build && cd build && \
    cmake ../ && \
    make && \
    make install && \
    cd / && rm -rf /opt/wsclean* && \
    apt-get autoremove -y && apt-get clean

CMD ["/bin/sh"]

LABEL Author="Abhinav Narayan" \
      Version="1.0" \
      Description="Docker container with wsclean and other dependencies"