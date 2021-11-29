# Jupyter Notebook Stack Docker

Customise version of [jupyter/minimal-notebook](https://github.com/jupyter/docker-stacks/tree/master/minimal-notebook) for Python 3.8.

- [Jupyter Docker Stacks on ReadTheDocs](https://jupyter-docker-stacks.readthedocs.io/en/latest/index.html)
- [Selecting an Image :: Core Stacks :: jupyter/minimal-notebook](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html#jupyter-minimal-notebook)


## Build Image

```sh
docker build --no-cache . -t my-notebook:hub-1.5.0
docker build . -t my-notebook:hub-1.5.0
```

## Run
From project root directory. 

> In Linux
```sh
docker run --rm \
 --gpus all \
 -p 8888:8888 \
 -e JUPYTER_ENABLE_LAB=yes \
 -v ${pwd}:/home/jovyan/work \
 my-notebook:hub-1.5.0
```

Instructs the startup script to run `jupyter lab` instead of the default `jupyter notebook` command.

> In Linux
```sh
docker run --rm \
-p 8888:8888 \
-e JUPYTER_ENABLE_LAB=yes \
-v "${pwd}":/home/jovyan/work \
my-notebook:hub-1.5.0
```

> In Windows PowerShell
```ps
docker run --rm `
--gpus all `
-p 8888:8888 `
-e JUPYTER_ENABLE_LAB=yes `
-v "${pwd}":/home/jovyan/work `
my-notebook:hub-1.5.0
```