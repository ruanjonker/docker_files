FROM debian:testing

RUN echo "deb-src http://httpredir.debian.org/debian/ testing main" >> /etc/apt/sources.list \
    && apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get build-dep --no-install-recommends -y erlang

ADD http://www.erlang.org/download/otp_src_17.4.tar.gz /root/otp_src_17.4.tar.gz

RUN cd /root \
    && tar -xzf otp_src_17.4.tar.gz \
    && cd /root/otp_src_17.4 \
    && ./configure && make && make install \
    && rm -fr /root/otp_src* \
    && apt-cache showsrc erlang | grep "Build-Depends:" | awk -F":|," 'END {for (i=1; i < NF; i++) {print $i;} }' | awk '{print $1" "}' | grep -v "Build-Depends" | tr -d '\n' | xargs apt-get remove --purge -y \
    && apt-get autoremove --purge -y \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/man/* /usr/src/*

CMD erl
