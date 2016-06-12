FROM ubuntu:trusty
MAINTAINER KIC

ENV HOME /root
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get install -y software-properties-common
RUN apt-add-repository ppa:webupd8team/java
RUN apt-get update
RUN echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | sudo /usr/bin/debconf-set-selections
RUN apt-get install -y oracle-java8-installer 
RUN apt-get install -y git libgmp-dev libgmp10 libgmp10-doc libgmp3-dev curl g++ vim unzip \
    libgmpxx4ldbl libmpc-dev libmpc3 libmpfr-dev libmpfr-doc libmpfr4 libmpfr4-dbg libmpfrc++-dev cmake autoconf

WORKDIR /opt
RUN git clone https://github.com/KIC/nestedvm.git #2
WORKDIR /opt/nestedvm/
RUN make 
RUN make test
RUN make stringtest

RUN make unix_runtime.jar
RUN make runtime.jar
RUN make compiler.jar
RUN make nestedvm.jar

# RUN apt-get install -y gnuplot
# RUN make pdf
# fails: "chart2.gnuplot", line 7: Unrecognized option.  See 'help set'.

# RUN make cxxtest
# fails make[7]: *** No rule to make target '../src/c++11/libc++11convenience.la', needed by `libstdc++.la'. Stop.

# RUN make compact_runtime_compiler.jar 
# fails invalid url and after fix still Error: Could not find or load main class com.brian_web.gcclass.GCClass

# RUN make compiletests 
# fails blank in some url: cd download && curl -LO http://www.ijg.org/files/jpegsrc.v7 .tar.gz

RUN make env.sh

RUN apt-get clean

