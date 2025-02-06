# See here for image contents: https://github.com/microsoft/vscode-dev-containers/blob/main/containers/go/.devcontainer/Dockerfile
ARG VARIANT="1"
FROM mcr.microsoft.com/devcontainers/go:1-${VARIANT}

# Setup
ENV GOTOOLCHAIN=auto

ENV HOME="/home/vscode"
WORKDIR /home/vscode

# Install standard packages
RUN apt-get update && \
        # General purpose tools
    apt-get install -y \
        # Python
        libsasl2-dev libldap2-dev libssl-dev libsnmp-dev libffi-dev \
        libncurses-dev libsqlite3-dev libbz2-dev libreadline-dev liblzma-dev tzdata tk-dev graphviz;

USER vscode

# Install Python
RUN git clone --depth=1 https://github.com/pyenv/pyenv.git .pyenv
ENV PYENV_ROOT="/home/vscode/.pyenv"
ENV PATH="$PYENV_ROOT/shims:$PYENV_ROOT/bin:${HOME}/.local/bin:${PATH}"
RUN git clone https://github.com/pyenv/pyenv-virtualenv.git $(pyenv root)/plugins/pyenv-virtualenv

ARG PYTHON_VERSION="3.13"
RUN pyenv install ${PYTHON_VERSION} && \
    pyenv global ${PYTHON_VERSION}

# Install tools
# - Tools
RUN sh -c "$(curl --location https://taskfile.dev/install.sh)" -- -d
COPY --from=quay.io/helmpack/chart-testing /usr/local/bin/helm /usr/local/bin
COPY --from=quay.io/helmpack/chart-testing /usr/local/bin/kubectl /usr/local/bin
COPY --from=quay.io/helmpack/chart-testing /usr/local/bin/ct /usr/local/bin
COPY --from=quay.io/helmpack/chart-testing /usr/bin/yamllint /usr/local/bin
COPY --from=quay.io/helmpack/chart-testing /usr/bin/yamale /usr/local/bin

# - Golang
RUN go install github.com/norwoodj/helm-docs/cmd/helm-docs@latest

# Modify dotfile
RUN echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
RUN echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
RUN echo 'export PATH="$PYENV_ROOT/shims:$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
RUN echo 'export PATH="$PYENV_ROOT/shims:$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
RUN echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bashrc
RUN echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.zshrc
