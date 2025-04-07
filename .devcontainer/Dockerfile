FROM mcr.microsoft.com/vscode/devcontainers/javascript-node:16

# Install Firefox
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends firefox-esr \
    wget \
    gnupg \
    unzip

# Install Chrome
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
    && echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" > /etc/apt/sources.list.d/google.list \
    && apt-get update \
    && apt-get -y install --no-install-recommends google-chrome-stable

# Install web-ext tool for Firefox extension testing and packaging
RUN npm install --global web-ext

# Install Chrome extension CLI tools
RUN npm install --global chrome-extension-cli

# Clean up
RUN apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/*

# Create app directory and set permissions
WORKDIR /app
