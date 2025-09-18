# Research Topic Prediction

## Overview

This project predicts the research topics of scientific articles based on their title and abstract. Given a dataset of research papers, the model classifies each article into one or more of the following topics: Computer Science, Physics, Mathematics, Statistics, Quantitative Biology, and Quantitative Finance. The dataset is multi-label, meaning a single research article can belong to multiple topics.

## Dataset

The project uses three CSV files: train.csv (training data with columns TITLE, ABSTRACT, and topic labels), test.csv (articles for which predictions are to be made), and submission6.csv (sample submission file).

Columns in train.csv:

* TITLE: Title of the research article
* ABSTRACT: Abstract of the article
* Labels: Binary columns for each topic (1 if the article belongs to the topic, 0 otherwise)

## Steps & Preprocessing

1. Data Cleaning: Removed punctuation and one-letter words, converted all text to lowercase, and removed multiple spaces.
2. Feature Engineering: Combined TITLE and ABSTRACT into a single column combined, applied CountVectorizer with n-grams (1,2), and applied TF-IDF transformation.
3. Splitting Data: Used train\_test\_split to split the training data into training and validation sets (90%-10%).
4. Model Training: Used LinearSVC classifier wrapped in MultiOutputClassifier to handle multi-label classification.
5. Prediction & Evaluation: Predicted on validation set and test set, evaluated using accuracy and classification report for precision, recall, and F1-score.

## Libraries Used

Python 3, pandas, numpy, matplotlib, nltk (for text preprocessing), scikit-learn (for vectorization and modeling)

## Output

Predictions are saved in submission2.csv in the following format:

| ID    | Computer Science | Physics | Mathematics | Statistics | Quantitative Biology | Quantitative Finance |
| ----- | ---------------- | ------- | ----------- | ---------- | -------------------- | -------------------- |
| 20973 | 0                | 0       | 0           | 1          | 0                    | 0                    |
| 20974 | 0                | 1       | 0           | 0          | 0                    | 0                    |

1 indicates the article belongs to the topic, 0 otherwise.

## How to Use

1. Load the notebook in Google Colab or Jupyter Notebook.
2. Ensure the CSV files (train.csv, test.csv, submission6.csv) are uploaded.
3. Run all cells to train the model and generate predictions.
4. The output CSV (submission2.csv) can be submitted or used for further analysis.

## Notes

* Stopwords removal is optional and commented in the code.
* The notebook is compatible with Google Colab and can be pushed directly to GitHub for sharing.
* For best results, the model may require hyperparameter tuning or use of more advanced NLP techniques.
