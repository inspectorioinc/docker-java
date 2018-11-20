#
# This is a base image for OpenJDK
#

# Pull base image
FROM phusion/baseimage:latest

# Set maintainer
LABEL maintainer="devops@inspectorio.com"

# Set environment variables
ENV LANG="en_US.UTF-8" LANGUAGE="en_US.UTF-8" LC_ALL="en_US.UTF-8" TERM=xterm \
	JAVA_VERSION=8 
	
	
# Configure system(charset and timezone) and install JDK
RUN locale-gen en_US.UTF-8 \
			&& echo $'\n\
					 #!/bin/bash\n\
					 set -e\n\
					 echo "$(date +"%Y-%m-%d %H:%M:%S.%N") OOM killer activated! PID=$PID, PPID=$PPID"\n\
					 ps -auxef\n\
					 for pid in $(ps ax | grep \'"\'"\'[[:space:]]java[[:space:]]\'"\'"\' | awk \'"\'"\'{print $1}\'"\'"\'); do kill -9 $pid || true; done\n' > /usr/bin/oom_killer \
			&& chmod a+x /usr/bin/oom_killer && \
  apt-get update && \
  apt-get install -y openjdk-8-jre curl htop iftop iotop iputils-ping iptraf lsof net-tools unzip wget \
		&& apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
