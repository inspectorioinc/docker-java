#
# This is a base image for OpenJDK
#

# Pull base image
FROM phusion/baseimage:latest

# Set maintainer
LABEL maintainer="devops@inspectorio.com"

# Set environment variables
ENV LANG="en_US.UTF-8" LANGUAGE="en_US.UTF-8" LC_ALL="en_US.UTF-8" TERM=xterm \
	JAVA_VERSION=8 \
	JAVA_HOME="/usr/lib/jvm/java-8-openjre-amd64"
	
	
# Configure system(charset and timezone) and install JDK
RUN locale-gen en_US.UTF-8 && \
  apt-get update && \
  apt-get install -y openjdk-8-jre curl htop iftop iotop iputils-ping iptraf lsof net-tools unzip wget \
		&& apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*