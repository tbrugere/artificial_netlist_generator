FROM ubuntu:20.04

# RUN apt-get update ; apt-get upgrade; true
ARG DEBIAN_FRONTEND=noninteractive 
ENV TZ=America/Los_Angeles
RUN apt-get update; true
RUN apt-get install -y build-essential git swig cmake tcl-dev tcl8.6-dev tcl-tclreadline bison flex zlib1g zlib1g-dev libboost-all-dev libspdlog-dev; true
RUN  useradd -m user
USER user
WORKDIR /home/user
# ENV REPO="https://github.com/daeyeon22/artificial_netlist_generator.git"
ENV REPO="https://github.com/tbrugere/artificial_netlist_generator.git"
RUN git clone $REPO
RUN mkdir -p artificial_netlist_generator/build
WORKDIR /home/user/artificial_netlist_generator/build
RUN git submodule update --init --recursive
RUN cmake CMakeLists.txt
RUN make
USER root
RUN make install
USER user
WORKDIR /home/user
