FROM debian:testing

ENV DEBIAN_FRONTEND noninteractive

RUN echo "deb-src http://httpredir.debian.org/debian/ testing main" >> /etc/apt/sources.list

RUN apt-get update #2015-08-29

RUN apt-get upgrade -y

RUN apt-get build-dep -y erlang

ADD http://www.erlang.org/download/otp_src_18.0.tar.gz /root/otp_src_18.0.tar.gz

RUN cd /root && tar -xzf otp_src_18.0.tar.gz
RUN cd /root/otp_src_18.0 && ./configure
RUN cd /root/otp_src_18.0 && make
RUN cd /root/otp_src_18.0 && make install

RUN rm -fr /root/otp_src*

CMD erl
