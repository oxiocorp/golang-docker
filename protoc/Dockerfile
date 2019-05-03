FROM oxio/golang:1.1

# Moving to installation workdir
RUN mkdir -p /opt/setup
WORKDIR /opt/setup

# Downloading compatible glibc for alpine
ADD https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub /etc/apk/keys/sgerrand.rsa.pub
ADD https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.28-r0/glibc-2.28-r0.apk .
RUN echo "f0a00f56fdee9dc888bafec0bf8f54fb188e99b5346032251abb79ef9c99f079  glibc-2.28-r0.apk" > glibc_sum.txt && \
    sha256sum -c glibc_sum.txt && \
    rm glibc_sum.txt
RUN apk add --no-cache --update \
    glibc-2.28-r0.apk

# Protobuf
ARG protobuf_version
ADD https://github.com/protocolbuffers/protobuf/releases/download/v${protobuf_version}/protoc-${protobuf_version}-linux-x86_64.zip .
RUN unzip protoc-${protobuf_version}-linux-x86_64.zip && \
    mv bin/protoc /usr/local/bin/ && \
    mv include /usr/local/include

# Application workdir
WORKDIR /opt/app

# Cleanup
RUN rm -rf /opt/setup
