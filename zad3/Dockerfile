# Use Jenkins official image
FROM jenkins/jenkins:lts

# Switch to root to install Docker, sudo, Node.js, and ESLint
USER root

# Install sudo
RUN apt-get update && apt-get install -y sudo

# Install Docker
RUN curl -fsSL https://get.docker.com -o get-docker.sh && \
    sh get-docker.sh

# Give Jenkins user permission to run Docker
RUN usermod -aG docker jenkins

# Allow Jenkins user to execute sudo commands without a password
RUN echo "jenkins ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

# Install Node.js, npm, and ESLint
RUN curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash - && \
    sudo apt-get install -y nodejs && \
    npm install -g eslint

# Switch back to the Jenkins user
USER jenkins
