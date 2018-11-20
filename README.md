golang-docker
=============

This repository contains `Dockerfile`s for:

* [`oxio/golang`](https://hub.docker.com/r/oxio/golang/): Barebone Golang image on Alpine with make, git and openssh-client
* [`oxio/golang-protoc`](https://hub.docker.com/r/oxio/golang-protoc/): From `oxio/golang` with `protoc` installed and available in user `PATH`

Build locally
-------------

* In each directory, run: `docker-compose build`
* Alternatively: `docker build -t oxio/<dir-name> .`

Background
----------

At [OXIO](https://www.oxio.io), our Golang projects are built using a `Makefile` that sets a local `GOPATH` which allows us to use different versions for our dependencies across all our projects. We therefore do not need to `go get` anything in the global `GOPATH`, hence the reason why `golang-protoc` doesn't come with dependencies such as `protoc-gen-go`.
