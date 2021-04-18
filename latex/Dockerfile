ARG BASE_REGISTRY=docker.io
ARG BASE_IMAGE=debian
ARG BASE_TAG=stable-slim

FROM ${BASE_REGISTRY}/${BASE_IMAGE}:${BASE_TAG} AS base

RUN apt-get update && \
    apt-get install --quiet --yes texlive-full && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /tmp/*
      
WORKDIR /home/workdir

VOLUME [ "/home/workdir" ]