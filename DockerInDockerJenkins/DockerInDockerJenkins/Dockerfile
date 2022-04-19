FROM jenkins/jenkins:lts
USER root

RUN uname -a && cat /etc/*release

#install docker
RUN curl -fsSL https://get.docker.com -o get-docker.sh && sh get-docker.sh

RUN apt-get update \
      && apt-get install -y sudo \
      && rm -rf /var/lib/apt/lists/*

RUN usermod -a -G root jenkins
RUN usermod -aG docker jenkins
# Good idea to switch back to the jenkins user.
USER jenkins



docker built -t jenkindocker .

docker images

docker run -it -v /var/run/docker.sock:/var/run/docker.sock -p 8080:8080 -p 50000:50000 -u root jenkinsdocker:latest