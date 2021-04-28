# Debian TeX Live Docker

## Build Image

```sh
docker build . -t debian-latex
```

## Run
From latex project root directory. 

> In Linux
```sh
docker run --rm \
 -v $(pwd):/home/workdir \
 debian-latex \
 pdflatex sample.tex
```

> In Windows Command Line (cmd)
```cmd
docker run --rm \
 -v %cd%:/home/workdir \
 debian-latex \
 pdflatex sample.tex
```

> In Windows PowerShell
```ps
docker run --rm \
 -v ${pwd}:/home/workdir \
 debian-latex \
 pdflatex sample.tex
```
