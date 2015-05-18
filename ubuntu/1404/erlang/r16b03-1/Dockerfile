FROM ubuntu:14.04

ENV DEBIAN_FRONTEND noninteractive


RUN echo "deb http://archive.ubuntu.com/ubuntu/ trusty multiverse" >> /etc/apt/sources.list
RUN echo "deb http://archive.ubuntu.com/ubuntu/ trusty-security multiverse" >> /etc/apt/sources.list

RUN apt-get update

RUN apt-get install -y wget
RUN apt-get install -y git
RUN apt-get install -y vim
RUN apt-get install -y snmp
RUN apt-get install -y snmp-mibs-downloader
RUN apt-get install -y liblockfile1
RUN apt-get install -y db-util
RUN apt-get install -y libdb-dev
RUN apt-get install -y python
RUN apt-get install -y fakeroot
RUN apt-get install -y dput
RUN apt-get install -y ctags

RUN apt-get build-dep -y erlang

ADD http://www.erlang.org/download/otp_src_R16B03-1.tar.gz /root/otp_src_R16B03-1.tar.gz

RUN cd /root && tar -xzf otp_src_R16B03-1.tar.gz
RUN cd /root/otp_src_R16B03-1 && ./configure
RUN cd /root/otp_src_R16B03-1 && make
RUN cd /root/otp_src_R16B03-1 && make install

RUN rm -fr /root/otp_src*

RUN apt-get clean

RUN rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

