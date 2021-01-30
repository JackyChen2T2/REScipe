# REScipe (Data Processing)
## Table of Contents
* [Introduction](#Introduction)
* [Language](#language)
* [Examples of Use](#examples-of-use)
* [Project Status](#project-status)
## Introduction
REScipe is a project for recipe recommendation given an image of food/dishes. The project has two parts, data processing and neural network training. This repo contains most of the data processing part, including tokenization, data cleaning, LDA model training, hyperparameter search, and label generation.

This part of the project aims to generate lower-dimensional labels for more than 40 thousand recipes given their recipe names (crawled from `allrecipe.com`). Since each recipe name is unique, it is necessary to extract common features as labels to make the training of the classification model practical. This program takes an XML spreadsheet of recipes, and outputs a trained LDA model that can be used to generate reasonably small labels for most recipes.
## Language
* Python 3.7
* Libraries:
   * `Pandas`
   * `NumPy`
   * `SpaCy`, with the trained language model `en_core_web_sm` for tokenization
   * `Gensim` for LDA model training
   * `inflect` for plural-to-singular lemmatization
   * `Matplotlib`
## Examples of Use
1. Load the XML spreadsheet into data frame

![Recipe Names in Data Frame](images/00_recipe.JPG)

2. Tokenization and lemmatization

![Tokenized and Lemmatized](images/01_tokenized.JPG)

3. Filtering after tokenization

![1st Row of Filtering](images/02_filtered.JPG)

* The 50 most common tokens in the corpus

![The 50 Most Common Tokens in the Corpus](images/03_top_50_corpus.png)

4. Training LDA model, using the corpus (Hyperparameter Tuning)

![Grid Search Tuning](images/TABLE.JPG)

5. Validation of the LDA model

![Example Validation](images/04_test_model.JPG)

6. Label Generation

![Label Generation](images/05_labels.JPG)
## Project Status
This part of the project can be run independently given a structured XML spreadsheet. The entire project has been completed and recorded:

[![Project REScipe](https://img.youtube.com/vi/qBLpT7K2xFw/0.jpg)](https://www.youtube.com/watch?v=qBLpT7K2xFw)

The other part of the project is [REScipe-NeuralNet](https://github.com/JackyChen2T2/REScipe-NeuralNet).

Adjustment to file directories and hyperparameters is necessary when working with a new XML spreadsheets. Depending on the setting, the LDA model training process can take from seconds to half an hour. The `LDA_hyperparameter_tuning.xlsx` file can be used for reference (in the Google Colab environment).
