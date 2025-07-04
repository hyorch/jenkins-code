FROM jenkins/jenkins:lts
USER root
# Set docker group id to the same as the Docker host
RUN groupadd -f -g 1001 docker && usermod -aG docker jenkins

USER jenkins