FROM jenkins/jenkins:2.222

ADD ./data /opt
WORKDIR /opt

# Install plugins
RUN /usr/local/bin/install-plugins.sh < /opt/plugins.txt

USER root

RUN apt-get -y update -y \
    && apt-get -y upgrade

# Install docker cli
RUN apt-get -y install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
RUN apt-key fingerprint ${docker-repo-fingerprint}
RUN add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
RUN apt-get -y update
RUN apt-get -y install docker-ce docker-ce-cli containerd.io

# Install docker-compose
RUN curl -L "https://github.com/docker/compose/releases/download/${docker-cli-version}/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
RUN chmod +x /usr/local/bin/docker-compose

USER jenkins
