FROM jenkins/jenkins:latest

LABEL MAINTAINER="Thanh Nam <nam.tt@neo-lab.vn>"

USER root

RUN apt-get update && apt-get install -y \
    apt-transport-https \
    software-properties-common

RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
RUN add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable"

RUN apt-get update && apt-get install -y \
    docker-ce \
    vim

# Insall nodejs
RUN curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -; \
    apt-get install -y nodejs

# Install yarn
RUN curl -o- -L https://yarnpkg.com/install.sh | bash

RUN usermod -aG docker,staff jenkins

# RUN mkdir -p /var/www/sod; \
#     chown -R jenkins:jenkins /var/www/sod

USER jenkins

# Install Jenkins plugins
RUN install-plugins.sh \
    blueocean \
    docker-workflow \
    locale \
    workflow-aggregator \
    pipeline-stage-view \
    git \
    cloudbees-bitbucket-branch-source \
    github-organization-folder

# Install NodeJS
# ENV NODE_VERSION 8.11
# ENV NVM_DIR $JENKINS_HOME/.nvm

# RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash \
#     && . $NVM_DIR/nvm.sh \
#     && nvm install ${NODE_VERSION} \
#     && nvm use ${NODE_VERSION} \
#     && nvm alias ${NODE_VERSION}

# # Wouldn't execute when added to the RUN statement in the above block
# # Source NVM when loading bash since ~/.profile isn't loaded on non-login shell
# RUN echo "" >> ~/.bashrc && \
#     echo 'export NVM_DIR="$HOME/.nvm"' >> ~/.bashrc && \
#     echo '[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"  # This loads nvm' >> ~/.bashrc

# VOLUME [ "/var/www/sod" ]
