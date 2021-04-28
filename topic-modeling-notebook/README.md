# Jupyter Notebook Stack Docker

Using [Jupyter Notebook Scientific Python Stack](https://github.com/jupyter/docker-stacks/tree/master/scipy-notebook).

Please visit the project documentation site for help using and contributing to this image and
others.

- [Jupyter Docker Stacks on ReadTheDocs](http://jupyter-docker-stacks.readthedocs.io/en/latest/index.html)
- [Selecting an Image :: Core Stacks :: jupyter/scipy-notebook](http://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html#jupyter-scipy-notebook)

Everything in the jupyter/scipy-notebook and their ancestor images.
* [NLTK](https://www.nltk.org/) Natural Language Toolkit
* [spaCy](https://spacy.io/) Natural Language Processing library
* [Gensim](https://radimrehurek.com/gensim/) for topic modelling
* [emoji](https://github.com/carpedm20/emoji/) Emoji for Python
* [pyLDAvis](https://github.com/bmabey/pyLDAvis) for interactive topic model visualization
* [Chart Studio](https://plotly.com/chart-studio/) for interactive charts
* [wordcloud](http://amueller.github.io/word_cloud/) for generating word cloud

## Build Image

```sh
docker build . -t nlp-notebook
```

## Run
From latex project root directory. 

> In Linux
```sh
docker run --rm \
 -it -p 8888:8888 \
 nlp-notebook
```