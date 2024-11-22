# Leveraging Social Media for Suicidal Text Detection - 242A Final Report

### Authors:
Capucine Hustin, Anand-Arnaud Pajaniradjane
**Date:** April 2024

---

## Motivation

In contemporary times, there is a noticeable increase in feelings of depression and occurrences of suicidal ideation among individuals, especially younger generations. Concurrently, there has been a surge in the number of people sharing their personal experiences and thoughts on social media platforms. This trend has led to some individuals openly discussing their suicidal thoughts and feelings on digital platforms like Facebook, Reddit, Quora, or X.  

Most machine learning models used on social media aim to maximize engagement and revenue by recommending content and advertisements. This project explores using such models for ethical purposes: detecting suicidal posts and connecting individuals with help.  

---

## Data

### Dataset Collection
The dataset comprises four categories:
1. **Suicidal Posts**: Web-scraped Reddit discussions about suicidal thoughts.  
   - Example: *"I just want to die. Can't live like this anymore. Father blames me for everything"*  
   **Label:** 1 (suicidal)

2. **Random Posts**: Neutral or positive tweets from publicly available datasets.  
   - Example: *"I love this app and use it for everything, however, for some reason it is no longer showing any holidays when I clicked on that tab."*  
   **Label:** 0 (non-suicidal)

3. **War News Titles**: Headlines discussing death and killings without suicidal thoughts (from Kaggle).  
   - Example: *"Three Algerians killed in attack presidency blames on Morocco"*  
   **Label:** 0 (non-suicidal)

4. **Suicide Definitions and Scientific Posts**: Neutral, factual sentences about suicide generated using OpenAI's API.  
   - Example: *"Adolescents and young adults are particularly susceptible to suicide due to the psychological changes and challenges associated with this developmental stage."*  
   **Label:** 0 (non-suicidal)

This comprehensive approach prevents the model from over-relying on keywords like "kill" or "suicide."

---

## Pre-Processing
Data preparation involved:
- Removing HTML tags, punctuation, and digits.  
- Lowercasing text and removing stopwords.  
- Stemming words to their root form.  
- Converting text into numerical vectors using `CountVectorizer`.

---

## Models Used

### Supervised Learning
1. **Decision Tree**: Captures non-linear relationships and provides interpretable insights.
2. **SVM**: Handles high-dimensional text data and captures nuanced patterns.
3. **Gradient Boosting**: Builds strong predictive models through iterative weak learners.
4. **Random Forest**: Provides feature importance while handling noisy data.
5. **Logistic Regression**: Simple linear model offering probability estimates.

### Deep Learning
1. **Neural Networks**: Learns complex representations of suicidal language patterns.

### Unsupervised Learning and Clustering
1. **PCA + kNN (Without Word Elimination)**: Identifies suicidal posts based on semantic patterns.  
2. **PCA + kNN (With Word Elimination)**: Excludes frequent words to capture subtle linguistic nuances.

---

## Results

### Model Comparisons
- **Precision**: Gradient Boosting achieved the highest (0.9769), closely followed by Logistic Regression (0.9680).  
- **False Negative Rate (FNR)**: PCA + kNN (Without Word Elimination) had the lowest FNR (0.02075), making it the most reliable model for identifying suicidal posts.

### Best Method: PCA + kNN
**Principal Component Analysis (PCA):** Reduces data dimensionality while preserving variance.  
**k-Nearest Neighbors (kNN):** Classifies data points based on the closest training examples in PCA-reduced space.

Visualizations:
1. **Figure 1**: PCA clustering without excluding frequent words shows distinct clusters of suicidal and non-suicidal posts.
2. **Figure 2**: Excluding frequent words disrupts clustering and reduces model accuracy.

---

## Impact and Next Steps
This project addresses a critical public health issue. Next steps include incorporating demographic data (age, gender, location) for enhanced accuracy and improving the ethical deployment of detection models to protect user privacy and free speech.  

