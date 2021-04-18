# Debian TeX Live Docker

## Build Image

```sh
docker build . -t debian-latex
```

## Run
> From latex project root directory. 
```sh
docker run --rm \
 -v $(pwd):/home/workdir \
 debian-latex \
 pdflatex sample.tex
```