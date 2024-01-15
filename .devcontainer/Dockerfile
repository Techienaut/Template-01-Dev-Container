FROM mcr.microsoft.com/vscode/devcontainers/base:bullseye

# curl and ca-certificates are needed for volta installation
RUN apt-get update \
  && apt-get install -y \
  curl \
  ca-certificates \
  --no-install-recommends \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

# set volta environment variables
RUN echo 'export VOLTA_HOME="$HOME/.volta"' >> /home/vscode/.bashrc \
  && echo 'export PATH="$VOLTA_HOME/bin:$PATH"' >> /home/vscode/.bashrc

# change USER to vscode bash environment and use /home/vscode/.bashrc
USER vscode

# install volta and node
RUN curl https://get.volta.sh | bash \
  && export VOLTA_HOME="$HOME/.volta" \
  && export PATH="$VOLTA_HOME/bin:$PATH" \
  && volta install node
  
WORKDIR $CODESPACE_VSCODE_FOLDER