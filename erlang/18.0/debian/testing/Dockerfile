FROM debian:testing

ENV DEBIAN_FRONTEND noninteractive

RUN echo "deb-src http://httpredir.debian.org/debian/ testing main" >> /etc/apt/sources.list

RUN apt-get update #2015-08-30

RUN apt-get build-dep --no-install-recommends -y erlang

ADD http://www.erlang.org/download/otp_src_18.0.tar.gz /root/otp_src_18.0.tar.gz

RUN cd /root && tar -xzf otp_src_18.0.tar.gz
RUN cd /root/otp_src_18.0 && ./configure && make && make install

RUN rm -fr /root/otp_src*

RUN apt-cache showsrc erlang | grep "Build-Depends:" | awk -F":|," 'END {for (i=1; i < NF; i++) {print $i;} }' | awk '{print $1" "}' | grep -v "Build-Depends" | tr -d '\n' | xargs apt-get remove --purge -y

RUN apt-get autoremove --purge -y

RUN apt-get clean
RUN rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/man/* /usr/src/*

CMD erl
