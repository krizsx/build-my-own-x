# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.148.1/containers/cpp/.devcontainer/base.Dockerfile

# [Choice] Debian / Ubuntu version: debian-10, debian-9, ubuntu-20.04, ubuntu-18.04
ARG VARIANT="buster"
FROM mcr.microsoft.com/vscode/devcontainers/cpp:0-${VARIANT}
ARG GO_VERSION="1.15.6"

# [Optional] Uncomment this section to install additional packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>
RUN curl -L https://golang.org/dl/go${GO_VERSION}.linux-amd64.tar.gz -o /tmp/go.linux-amd64.tar.gz \
    && tar -C /usr/local -xzf /tmp/go.linux-amd64.tar.gz \
    && rm -rf /tmp/**

USER vscode

RUN mkdir -p ~/project/go \
    && mkdir -p ~/project/go/bin \
    && mkdir -p ~/project/go/pkg \
    && mkdir -p ~/project/go/src \
    && echo "export GOPROXY=\"https://goproxy.cn,https://proxy.golang.org,direct\"" >> ~/.zshrc \
    && echo "export GOSUMDB=\"sum.golang.google.cn\"" >> ~/.zshrc

ENV GOROOT /usr/local/go
ENV GOPATH /home/vscode/project/go
ENV PATH /home/vscode/project/go/bin:/usr/local/go/bin:$PATH