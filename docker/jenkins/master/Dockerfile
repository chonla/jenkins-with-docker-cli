FROM jenkins/jenkins:2.222

ADD ./data /opt
WORKDIR /opt

# Bypass unlock
RUN mkdir /var/jenkins_home/init.groovy.d && cp bypass.groovy /var/jenkins_home/init.groovy.d/bypass.groovy

# Install plugins
RUN /usr/local/bin/install-plugins.sh < /opt/plugins.txt

# Update
USER root
RUN apt-get -y update -y \
    && apt-get -y upgrade
USER jenkins
