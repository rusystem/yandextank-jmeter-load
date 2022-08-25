FROM ubuntu:20.04

WORKDIR home/loadtest

ARG JMETER=apache-jmeter-5.5

RUN apt-get update && apt-get install -y wget && apt-get install -y software-properties-common

RUN apt-get install -y openjdk-17-jdk

RUN wget http://www.gtlib.gatech.edu/pub/apache/jmeter/binaries/$JMETER.tgz \
    && tar -xf $JMETER.tgz \
    && rm -rf $JMETER.tgz

RUN apt-get install -y python3-pip build-essential python3-dev libffi-dev gfortran libssl-dev \
    && pip3 install --upgrade pip \
    && pip3 install --upgrade setuptools \
    && pip3 install https://api.github.com/repos/yandex/yandex-tank/tarball/master \
    && add-apt-repository ppa:yandex-load/main && apt-get update \
    && apt-get install phantom phantom-ssl

COPY resources .
COPY token.txt .