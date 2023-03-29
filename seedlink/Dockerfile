# -*- coding: utf-8 -*-
# Basic Dockerfile to run ringserver in a container
FROM ubuntu:20.04

# Install compiler
RUN apt-get update -y && apt install -y gcc make

# Build executable
WORKDIR /seedlink
#RUN mkdir /seedlink

COPY . /seedlink

RUN cd /seedlink && CFLAGS="-O2" make

RUN groupadd sysop

RUN useradd -rm -d /home/sysop -s /bin/bash -g sysop -G sudo -u 1001 sysop -p sysop

RUN passwd -d sysop

USER sysop
WORKDIR /home/sysop

# Expose default SeedLink and DataLink ports
EXPOSE 18000
#EXPOSE 16000

WORKDIR /seedlink

COPY ./protocols /etc/protocols



# Default command is "ringserver"
ENTRYPOINT [ "./ringserver" ]

# Default arguments
CMD [ "./ring.conf"]
