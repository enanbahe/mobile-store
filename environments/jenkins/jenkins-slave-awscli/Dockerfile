FROM jenkinsci/jnlp-slave
MAINTAINER Enrique Bassallo <enanbahe@hotmail.com>

USER root
RUN apt-get update
RUN apt-get install -y python
RUN apt-get install -y python-pip

# Install app dependencies
RUN pip install --upgrade pip
RUN pip install awscli --upgrade
