# Start with the official Jenkins Long Term Support image
FROM jenkins/jenkins:lts

# Switch to root to install our custom build tools
USER root

# 1. Install prerequisites and Maven
RUN apt-get update && apt-get install -y lsb-release curl wget apt-transport-https ca-certificates gnupg2 maven

# 2. Install Docker CLI
RUN curl -fsSLo /usr/share/keyrings/docker-archive-keyring.asc https://download.docker.com/linux/debian/gpg
RUN echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.asc] https://download.docker.com/linux/debian $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list
RUN apt-get update && apt-get install -y docker-ce-cli

# 3. Install Node.js 20
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - && apt-get install -y nodejs

# 4. Install Chromium Browser (For Angular Headless Tests)
RUN apt-get update && apt-get install -y chromium
ENV CHROME_BIN=/usr/bin/chromium