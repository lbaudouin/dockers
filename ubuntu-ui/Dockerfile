FROM ubuntu:16.04

RUN apt-get update
RUN apt-get install -y x-window-system
RUN apt-get install -y binutils
RUN apt-get install -y mesa-utils
RUN apt-get install -y module-init-tools

ADD nvidia-driver.run /tmp/nvidia-driver.run
RUN sh /tmp/nvidia-driver.run -a -N --ui=none --no-kernel-module
RUN rm /tmp/nvidia-driver.run

RUN apt-get install -y libboost-thread1.58.0
RUN apt-get install -y libgomp1
RUN apt-get install -y udev libpulse-mainloop-glib0 libusb-1.0-0

RUN apt-get install -y software-properties-common
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3C2BED8A

RUN apt-get install -y nano

CMD /bin/bash

WORKDIR /sources
