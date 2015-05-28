FROM ubuntu:14.04

ENV DEBIAN_FRONTEND noninteractive

RUN echo "deb mirror://mirrors.ubuntu.com/mirrors.txt trusty main restricted universe multiverse" > /etc/apt/sources.list
RUN apt-get clean && apt-get update

RUN apt-get install -y curl
RUN apt-get install -y apt-transport-https

RUN echo "deb https://packagecloud.io/basho/riak/ubuntu/ trusty main" >> /etc/apt/sources.list
RUN echo "deb-src https://packagecloud.io/basho/riak/ubuntu/ trusty main" >> /etc/apt/sources.list

RUN curl https://packagecloud.io/gpg.key | apt-key add -

RUN apt-get update
RUN apt-get install -y riak

RUN cp /etc/riak/riak.conf /etc/riak/riak.conf.orig
#RUN sed -i 's/riak@127.0.0.1/riak@$IP/' /etc/riak/riak.conf 
RUN sed -i 's/127.0.0.1:8098/0.0.0.0:8098/' /etc/riak/riak.conf
RUN sed -i 's/127.0.0.1:8087/0.0.0.0:8087/' /etc/riak/riak.conf
RUN sed -i 's/storage_backend = bitcask/storage_backend = leveldb/' /etc/riak/riak.conf
RUN sed -i 's/riak_control = off/riak_control = on/' /etc/riak/riak.conf
RUN echo "erlang.distribution.port_range.minimum = 6000" >> /etc/riak/riak.conf
RUN echo "erlang.distribution.port_range.maximum = 7999" >> /etc/riak/riak.conf

ADD Dockerfile /Dockerfile

RUN apt-get clean
RUN rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

