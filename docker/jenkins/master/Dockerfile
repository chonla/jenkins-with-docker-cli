FROM jenkins/jenkins:2.222

ADD ./data /opt
WORKDIR /opt

# Install plugins
RUN /usr/local/bin/install-plugins.sh < /opt/plugins.txt

USER root

# Update
RUN apt-get -y update -y \
    && apt-get -y upgrade

USER jenkins
