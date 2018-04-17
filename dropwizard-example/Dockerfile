FROM ubuntu:16.04
LABEL MAINTAINER Mayank Agarwal <mayank.in@gmail.com>

ENV DEBIAN_FRONTEND noninteractive
ENV JAVA_HOME       /usr/lib/jvm/java-8-oracle
ENV LANG            en_US.UTF-8
ENV LC_ALL          en_US.UTF-8
ENV PROJ_HOME /opt/cloudnativelabs

RUN apt-get update && \
  apt-get install -y --no-install-recommends locales && \
  locale-gen en_US.UTF-8 && \
  apt-get dist-upgrade -y && \
  apt-get --purge remove openjdk* && \
  echo "oracle-java8-installer shared/accepted-oracle-license-v1-1 select true" | debconf-set-selections && \
  echo "deb http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main" > /etc/apt/sources.list.d/webupd8team-java-trusty.list && \
  apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886 && \
  apt-get update && \
  apt-get install -y --no-install-recommends oracle-java8-installer oracle-java8-set-default && \
  apt-get clean all

WORKDIR $PROJ_HOME
ADD target/dropwizard-example-1.0-SNAPSHOT.jar $PROJ_HOME/dropwizard-example.jar
ADD config.yml $PROJ_HOME/config.yml
 
EXPOSE 8080 8081

ENTRYPOINT ["java", "-jar", "dropwizard-example.jar", "server", "config.yml"]
