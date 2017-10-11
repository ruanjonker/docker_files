FROM centos:7

RUN yum update -y
RUN yum install -y epel-release
RUN yum install -y gcc \
                   gcc-c++ \
                   glibc-devel \
                   make \
                   ncurses-devel \
                   openssl-devel \
                   autoconf \
                   java-1.8.0-openjdk-devel \
                   wxBase.x86_64

RUN yum install -y rpm-build

RUN rm -fr /var/cache/yum

RUN yum clean all
