ARG BASE_REGISTRY=docker.io
ARG BASE_IMAGE=jupyter/scipy-notebook
ARG BASE_TAG=latest

FROM ${BASE_REGISTRY}/${BASE_IMAGE}:${BASE_TAG} AS base

RUN pip install --quiet --no-cache-dir \
    'pyLDAvis==3.3.*' \
    'chart-studio==1.1.*' \
    'nltk==3.6.*' \
    'gensim==4.0.1' \
    'spacy==3.0.6' \
    'wordcloud==1.8.*' \
    'emoji==1.2.0' && \
    python -m spacy download en_core_web_lg && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"
    