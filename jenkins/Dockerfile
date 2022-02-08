FROM jenkins/jenkins:2.333-jdk11

USER root

RUN apt-get update -qq && \
    apt-get upgrade -y --autoremove --purge && \
    apt-get install -y --no-install-recommends apt-transport-https && \ 
    apt-get install -y wget

RUN groupadd -g 996 docker && usermod -aG docker jenkins && usermod -aG root jenkins
SHELL ["/bin/bash", "-o", "pipefail", "-c"]
RUN wget -qO- https://get.docker.com/ | sh

RUN curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" \
    -o /usr/local/bin/docker-compose && chmod +x /usr/local/bin/docker-compose

USER jenkins 

COPY plugins/plugins.txt /usr/share/jenkins/ref/
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt

COPY jcasc/* /usr/share/jenkins/ref/casc_configs/
ENV CASC_JENKINS_CONFIG /usr/share/jenkins/ref/

ENTRYPOINT ["bash", "/usr/local/bin/jenkins.sh"]
