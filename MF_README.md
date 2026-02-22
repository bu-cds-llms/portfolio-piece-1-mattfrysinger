# N-Gram Language Modeling with Hard Backoff Method;
# Memorization and Generalization in Mary Shelley's Frankenstein

## Overview

This portfolio piece builds off of Lab 1 and improves upon its mistakes. The purpose, to investigate a variable order n-gram model and see how it behaves trained on an entire text of a book. The model has a hard backoff approach when higher n-values do not work; the goal is to see the quality of the model's memorization / generalization of text, assuming they will be worse when using higher values of n.

We want to see a relationship between contextual specificity (n) and the model's ability to predict the next word. That's achieved by using a min_count variable and evaluating performance using perplexity.

## Methods

### 1. N-Gram Model

The n-gram model goes through max_n = 10 and defaults to trying the highest n, unless the context is unseen or does not meet the min_counst freq. threshold, in which it backs off to the lower n (= 9) and so on...

The tested context freq. thresholds were 1, 2 and 5. Rare contexts (1) can exist only once in the text, leading to memorization. Higher thresholds requires contexts that are not only seen once.

### 2. Train/Test Split

The first 80% of the book is used for training. The last 20% is used for testing. It is better to evaluate the model on unseen text

### 3. Perplexity Evaluation Metric

Measures how well the model predicts the next word. Lower perplexity = better predictive performance (for the test data only). This reveals overfitting and the importance of the freq. thresholds.

## Key Results

With min_count = 1, the model relied on 10-grams almsot every time. The train perplexity of 1 meant it was just memorizing the text, and the outrageously high test perplexity meant the model had no idea how to predict the next word given the unseen test split.

By increasing the min_count freq. threshold, it reduced reliance on high-n contexts. Results at higher min_count vales showed substantially lower perplexities for the test data. 
That's the tradeoff:
* high-n = memorization of text, inability to predict future words
* backoff utilized = improved generalization, ability to predict

The values were still very high, indicating there is still room to grow.

## How to Run

1. Clone the repo
2. Ensure "Frankenstein_Full-Text.txt" is in your directory. Size = 418 KB, small
3. run cells in order
4. observe perplexity, n-usage distribution

## Requirements

Ran on Python 3.11.5 as a .ipynb file

Include all packages in first code cell;

* numpy
* matplotlib
* collections
* re
* math
* random