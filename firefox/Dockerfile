FROM debian:testing

ARG runasuser

RUN    echo "deb http://httpredir.debian.org/debian/ testing main contrib non-free" > /etc/apt/sources.list \
    && echo "deb http://security.debian.org/ testing/updates main" >> /etc/apt/sources.list \
    && echo "deb http://httpredir.debian.org/debian/ testing-updates main" >> /etc/apt/sources.list \
    && echo "deb http://www.deb-multimedia.org testing main non-free" >> /etc/apt/sources.list \
    && apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install --force-yes -y deb-multimedia-keyring \
    && apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install --no-install-recommends -y \
        libasound2  \
        libatk1.0-0 libc6  \
        libcairo2  \
        libdbus-1-3  \
        libdbus-glib-1-2  \
        libevent-2.0-5  \
        libffi6  \
        libfontconfig1  \
        libfreetype6  \
        libgcc1  \
        libgdk-pixbuf2.0-0  \
        libglib2.0-0  \
        libgtk2.0-0  \
        libhunspell-1.3-0  \
        libnspr4  \
        libnss3  \
        libpango-1.0-0  \
        libsqlite3-0  \
        libstartup-notification0  \
        libstdc++6  \
        libvpx2  \
        libx11-6  \
        libxcomposite1  \
        libxdamage1  \
        libxext6  \
        libxfixes3  \
        libxrender1  \
        libxt6  \
        zlib1g  \
        fontconfig  \
        procps  \
        debianutils \
        flashplugin-nonfree \
        flashplugin-nonfree-extrasound \
        bzip2

COPY firefox.tar.bz2 /opt/firefox.tar.bz2

RUN cd /opt/ && tar -xjf firefox.tar.bz2 \
    && ln -s /opt/firefox/firefox /usr/bin/firefox \
    && useradd -m -d /home/firefox --uid ${runasuser} -s /bin/bash firefox \
    && mkdir -p /home/firefox/.mozilla \
    && chown -R firefox:firefox /home/firefox \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* 

# Start Firefox
WORKDIR /home/firefox
ENTRYPOINT ["firefox"]
