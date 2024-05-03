# NOTE we recommend you tag this image as 'gunns_unloaded_or8', as the 'gunns_loaded_or8' image
# uses that as its base.
#
# Start with Oracle 8 image.  We use Oracle 8 as a substitute for RHEL8 since it is still 'RHEL-like', and free.
FROM oraclelinux:8

# Install optional latest repo
RUN yum install -y yum-utils
RUN dnf config-manager --set-enabled ol8_codeready_builder

# Reset repo list
RUN yum repolist

# Install the epel repository and Update yum
RUN yum install -y epel-release && yum update -y

# cd to /home
WORKDIR /home

# Use some cores
ENV MAKEFLAGS -j4

# Install all the packages!
# Note we're using tk-devel as a substitute for tkinter since tkinter is not currently available
# (or we don't know where to find it)
# RUN yum install -y \
 RUN yum install -y bison 
 RUN yum install -y clang-devel 
 RUN yum install -y cmake 
 RUN yum install -y curl-devel 
 RUN yum install -y firefox 
 RUN yum install -y flex 
 RUN yum install -y gcc 
 RUN yum install -y gcc-c++ 
 RUN yum install -y git 
 RUN yum install -y glibc-devel 
 RUN yum install -y gtest-devel 
#  https://github.com/jgraph/drawio-desktop/releases/download/v14.5.1/drawio-x86_64-14.5.1.rpm \
RUN yum install -y java-1.8.0-openjdk-devel 
 RUN yum install -y libX11-devel 
 RUN yum install -y libxml2-devel 
 RUN yum install -y libXi-devel 
 RUN yum install -y libXmu-devel 
 RUN yum install -y libXt-devel 
 RUN yum install -y llvm-devel 
 RUN yum install -y llvm-static 
 RUN yum install -y make 
 RUN yum install -y tcsh 
 RUN yum install -y csh 
 RUN yum install -y mesa-libGL-devel 
 RUN yum install -y mesa-libGLU-devel 
 RUN yum install -y maven 
 RUN yum install -y cppunit 
 RUN yum install -y cppunit-devel 
 RUN yum install -y lcov 
 RUN yum install -y valgrind 
 RUN yum install -y ncurses-devel 
 RUN yum install -y openmotif-devel 
 RUN yum install -y perl-Digest-MD5 
 RUN yum install -y protobuf-devel 
 RUN yum install -y python36-devel 
 RUN yum install -y sqlite-devel 
 RUN yum install -y swig 
 RUN yum install -y systemd-devel 
 RUN yum install -y python3-tkinter 
 RUN yum install -y udunits2-devel 
 RUN yum install -y which 
 RUN yum install -y zip 
RUN yum install -y zlib-devel
RUN yum install -y perl 
RUN yum install -y perl-Digest-MD5
# Clone Trick
RUN git clone https://github.com/nasa/trick.git

# Make Trick
WORKDIR trick
RUN ./configure && make
WORKDIR ..

# Set environment variables, assuming GUNNS will be cloned or mapped to /home/gunns.
ENV TRICK_HOME /home/trick
ENV GUNNS_TRICK_HOME /home/trick
ENV GUNNS_HOME /home/gunns
ENV PATH "$PATH:/home/trick/bin"
