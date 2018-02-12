Jenkins Agent Docker image

Docker Stars Docker Pulls Docker Automated build

This is a base image for Docker, which includes OpenJDK 8 and the Jenkins agent executable (slave.jar). This executable is an instance of the Jenkins Remoting library.
Usage

This image is used as the basis for the Docker JNLP Agent image. In that image, the container is launched externally and attaches to Jenkins.

This image may instead be used to launch an agent using the Launch method of Launch agent via execution of command on the master. Try for example

docker run -i --rm --name agent --init jenkinsci/slave:3.7-1 java -jar /usr/share/jenkins/slave.jar

after setting Remote root directory to /home/jenkins/agent.
Agent Work Directories

Starting from Remoting 3.8 there is a support of Work directories, which provides logging by default and change the JAR Caching behavior.

Call example:

docker run -i --rm --name agent1 --init -v agent1-workdir:/home/jenkins/agent jenkinsci/slave:3.10-1 java -jar /usr/share/jenkins/slave.jar -workDir /home/jenkins/agent

Configurations

The image has several supported configurations, which can be accessed via the following tags:

    latest: Latest version with the newest remoting (based on openjdk:8-jdk)
    alpine: Small image based on Alpine Linux (based on openjdk:8-jdk-alpine)
    2.62: This version bundles Remoting 2.x, which is compatible with Jenkins servers running on Java 6 (1.609.4 and below)
    2.62-alpine: Small image with Remoting 2.x
