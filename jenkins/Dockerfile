FROM jenkins/jenkins:2.333-jdk11

COPY plugins/plugins.txt /usr/share/jenkins/ref/
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt

ENTRYPOINT ["bash", "/usr/local/bin/jenkins.sh"]
