---
date: 2022-07-17T10:58:08-04:00
description: "Natural Language Processing group project. Applied supervised learning to identify whether the review was helpful. Performed pre-processing, LDA, TF-IDF, Doc2Wec, Word2Vec, logistic regression, neural networks (LSTM), transformers. We even tried to classify test set ourselfes to see if we could outperfrom NLP classifier."
featured_image: "/images/nlp1.png"
title: "Determining whether the IMDB review was helpful using NLP frameworks" 
---
📂 [Github Repo](https://github.com/sinkov/NLP-IMDB-Classification) has the corresponding Jupyter notebook and beautiful report 😋.
# Assignment description
The final course project (FCP) consists of a text classification task: you’re supposed to adjudicate between helpful and unhelpful movie reviews from the IMDB database. For the sake of redundancy, your goal is to classify each movie review “i” into one of the two categories: 0/not helpful: less than 30% of IMDB users found movie review “i” helpful 1/helpful: more than 70% of IMDB users found movie review “i” helpful

The training data (train.csv, see the download area below) contains 10,755 labelled reviews. The test data contains 5,071 reviews that are unlabeled (test.csv, see below). All the reviews included in the dataset have at least 80 votes. The dataset for this FCP focuses on the left- and right-hand ‘tails’ of the distribution.
