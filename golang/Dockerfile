FROM golang:1.11-alpine3.8

# Dependencies
RUN apk add --no-cache --update \
    bash \
    git \
    make \
    openssh-client

# Git setup to enable having private github.com repos as dependencies
RUN mkdir /root/.ssh && \
    chmod 0700 /root/.ssh && \
    echo "Host github.com\n\tStrictHostKeyChecking no\n" >> /root/.ssh/config && \
    ssh-keyscan -t rsa github.com >> /root/.ssh/known_hosts && \
    git config --global --add url."git@github.com:".insteadOf "https://github.com/"

# RSA keys can then be added like such:
# - COPY id_rsa /root/.ssh/id_rsa
# - COPY id_rsa.pub /root/.ssh/id_rsa.pub
# - RUN chmod 0600 /root/.ssh/id_rsa

# Application workdir
RUN mkdir -p /opt/app
WORKDIR /opt/app
