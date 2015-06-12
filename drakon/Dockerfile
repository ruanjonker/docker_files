FROM debian:jessie

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update
RUN apt-get install -y unzip tcl8.6 tk8.6 tcllib libsqlite3-tcl libtk-img

ADD http://sourceforge.net/projects/drakon-editor/files/drakon_editor1.26.zip/download /opt/drakon_editor1.26.zip

RUN cd /opt/ && unzip drakon_editor1.26.zip

RUN apt-get clean
RUN rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN mkdir -p /workspace

WORKDIR /workspace
CMD /opt/drakon_editor.tcl
