FROM ghcr.io/credify-pte-ltd/golang-dev:latest

LABEL MAINTAINER="Spy Kab" EMAIL="vinh.vo@credify.one"

WORKDIR /credify

all:
    BUILD +builder

builder:
    ARG DOCKER_REGISTRY
    ARG APPLICATION
    ARG IMAGE_TAG
    
    RUN apk add ca-certificates libc-dev gcc

    COPY . .

    RUN cd vendor/gitlab.com/credify.one/services/common && ./install.sh

    RUN --mount=type=cache,target=/root/.cache/go-build go build

    RUN rm -rf /credify/*

    SAVE IMAGE "$DOCKER_REGISTRY/$APPLICATION-builder:$IMAGE_TAG"
