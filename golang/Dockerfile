FROM golang:1.15-alpine3.12

# Dependencies
RUN apk add --no-cache --update \
    bash \
    git \
    mercurial \
    make \
    openssh-client \
    gcc \
    libc-dev \
    tzdata

# Git setup to enable having private github.com repos as dependencies
RUN mkdir /root/.ssh && \
    chmod 0700 /root/.ssh && \
    ssh-keyscan -t rsa github.com >> /root/.ssh/known_hosts && \
    ssh-keyscan -t rsa gitlab.com >> /root/.ssh/known_hosts && \
    git config --global --add url."git@github.com:".insteadOf "https://github.com/" && \
    git config --global --add url."git@gitlab.com:".insteadOf "https://gitlab.com/"

# RSA keys can then be added like such:
# - COPY id_rsa /root/.ssh/id_rsa
# - COPY id_rsa.pub /root/.ssh/id_rsa.pub
# - RUN chmod 0600 /root/.ssh/id_rsa

# Application workdir
RUN mkdir -p /opt/app
WORKDIR /opt/app
