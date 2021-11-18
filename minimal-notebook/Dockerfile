ARG BASE_REGISTRY=docker.io
ARG BASE_IMAGE=jupyter/minimal-notebook
ARG BASE_TAG=hub-1.5.0

FROM ${BASE_REGISTRY}/${BASE_IMAGE}:${BASE_TAG} AS minimal

# name your environment and choose python 3.x version
ARG conda_env=python38
ARG py_ver=3.8

USER root

# ffmpeg for matplotlib anim & dvipng+cm-super for latex labels
RUN apt-get update --yes && \
    apt-get install --yes --no-install-recommends ffmpeg dvipng cm-super && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

USER ${NB_UID}

# you can add additional libraries you want mamba to install by listing them below the first line and ending with "&& \"
RUN mamba create --quiet --yes -p "${CONDA_DIR}/envs/${conda_env}" python=${py_ver} ipython ipykernel \
    'bokeh' \
    'ipympl' \
    'ipywidgets' \
    'numba' \
    'pandas' \
    'scikit-image' \
    'scikit-learn' \
    'scipy' \
    'seaborn' && \
    pip install --quiet --no-cache-dir matplotlib jupyter-dash && \
    ### can modify or enable additional extensions here
    jupyter nbextension enable --py jupyter_dash --user && \
    jupyter lab build && \
    mamba clean --all -f -y

# create Python 3.x environment and link it to jupyter
RUN "${CONDA_DIR}/envs/${conda_env}/bin/python" -m ipykernel install --user --name="${conda_env}" && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"

# Import matplotlib the first time to build the font cache.
ENV XDG_CACHE_HOME="/home/${NB_USER}/.cache/"

RUN MPLBACKEND=Agg python -c "import matplotlib.pyplot" && \
    fix-permissions "/home/${NB_USER}"

# prepend conda environment to path
ENV PATH "${CONDA_DIR}/envs/${conda_env}/bin:${PATH}"

USER ${NB_UID}

WORKDIR "${HOME}"