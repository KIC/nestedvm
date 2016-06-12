FROM ubuntu:trusty
MAINTAINER KIC

ENV HOME /root
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get install -y software-properties-common
RUN apt-add-repository ppa:webupd8team/java
RUN apt-get update
RUN echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | sudo /usr/bin/debconf-set-selections
# RUN apt-get install -y oracle-java8-installer git libgmp\* libmpc\* libmpfr\* cmake autoconf
RUN apt-get install -y oracle-java8-installer git libgmp-dev libgmp10 libgmp10-doc libgmp3-dev curl g++ \
    libgmpxx4ldbl libmpc-dev libmpc3 libmpfr-dev libmpfr-doc libmpfr4 libmpfr4-dbg libmpfrc++-dev cmake autoconf2.64
RUN apt-get install -y libisl10 libisl-dev libisl-dbg libcloog-isl-dev libcloog-isl4 cloog-isl vim unzip autogen
WORKDIR /opt
RUN git clone https://github.com/KIC/nestedvm.git
WORKDIR /opt/nestedvm/
RUN make -B all

RUN apt-get clean

