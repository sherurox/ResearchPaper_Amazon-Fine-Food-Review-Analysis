# 📊 Amazon Fine Food Review Analysis

This repository contains the source code, dataset references, and analysis for the research paper "Amazon Fine Food Review Analysis", published in the International Journal for Research in Applied Science & Engineering Technology (IJRASET), Vol. 11, Issue X, October 2023. The study focuses on text mining, topic modeling, and review score prediction on Amazon Fine Food reviews using NLP and linear regression techniques.

## 📜 Abstract

The project analyzes over 568,454 Amazon Fine Food reviews spanning from October 1999 to October 2012, extracting insights using natural language processing (NLP), topic modeling, and predictive modeling.

Key highlights of the study:

**Descriptive Analysis:** Understanding review patterns, score distributions, and temporal trends in text length, helpfulness ratio, and ratings.

**Text Preprocessing:** Tokenization, stopword removal, lemmatization, and TF-IDF vectorization (unigrams + bigrams), followed by PCA for dimensionality reduction.

**Topic Modeling:** Latent Dirichlet Allocation (LDA) with 5 topics to identify common themes in customer reviews.

**Predictive Modeling:** Multiple linear regression variants (helpfulness-weighted, inverse-frequency-weighted, and unweighted) plus Lasso and Ridge regression for review score prediction (1–5 stars).

**Best Result:** Unweighted linear regression achieved an RMSE of 1.0936 and ~42.6% exact-match accuracy on the held-out test set.

## 📊 Visualizations

<p align="center">
    <b>Figure 1: Text analysis of reviews</b><br>
    <img src="https://github.com/user-attachments/assets/5cd6c2d5-a262-426a-ace2-cc709d8b869e" width="500"/>
</p>

<p align="center">
    <b>Figure 2: A histogram for Text length and summary length</b><br>
    <img src="https://github.com/user-attachments/assets/ab85d3df-825f-46b4-86e4-4f24046b4380" width="500"/>
</p>

<p align="center">
    <b>Figure 3: Violin plots for the relationship between scores and summary/text lengths</b><br>
    <img src="https://github.com/user-attachments/assets/c5af9bbf-ac68-4269-9f5b-d321e0f9dc0e" width="500"/>
</p>

## 📊 Results

### Descriptive Statistics

| Metric | Text Length | Summary Length | Score | Helpfulness Ratio |
|--------|-----------|---------------|-------|-------------------|
| **Min** | 3 | 0 | 1 | 0 |
| **Mean** | 79.10 | 4.11 | 4.18 | 0.41 |
| **Median** | 56 | 4 | 5 | 0 |
| **Max** | 3,377 | 42 | 5 | 1 |

---

### Topic Modeling (LDA — 5 Topics Extracted)

| Topic | Interpretation | Top 10 Keywords |
|-------|---------------|-----------------|
| 1 | **Dog Food Reviews** | food, dog, like, eat, dogs, treats, love, loves, just, good |
| 2 | **Tea & Beverages** | tea, flavor, like, coffee, taste, good, chocolate, just, cup, drink |
| 3 | **Snacks & Chips** | like, good, taste, great, just, flavor, love, chips, salt, really |
| 4 | **Coffee & Amazon Orders** | coffee, amazon, product, price, good, great, order, just, buy, box |
| 5 | **Cooking Ingredients** | product, water, like, sugar, use, taste, oil, just, good, bottle |

---

### Model Performance (Review Score Prediction, 1–5 Stars)

| Model | Accuracy (Exact Match) | RMSE |
|-------|----------------------|------|
| Linear Regression (helpfulness-weighted) | 42.2% | 1.1008 |
| Linear Regression (inverse-frequency-weighted) | 23.2% | 1.3387 |
| **Linear Regression (unweighted) — Best** | **42.6%** | **1.0936** |

Lasso and Ridge regression were also evaluated across a range of regularization strengths, but neither outperformed the unweighted linear regression, suggesting the PCA-reduced feature set was already sufficiently constrained.

**Note:** This is a regression task predicting star ratings (1–5), not a binary sentiment classifier. Accuracy reflects exact score matches after rounding continuous predictions to the nearest integer and clipping to the [1, 5] range.

## 🔧 Pipeline Overview

1. Load and clean 568,454 reviews (timestamp conversion, HTML tag removal, helpfulness value correction)
2. Engineer features: text length, summary length, helpfulness ratio
3. Exploratory analysis with time-series plots, histograms, and violin plots
4. LDA topic modeling (5 topics) with pyLDAvis interactive visualization
5. Text preprocessing with NLTK (tokenization, stopword removal, lemmatization)
6. TF-IDF vectorization (unigrams + bigrams, top 300 features) → PCA (retaining 80% variance)
7. Combine PCA components with numeric features (year-after-2007, log-transformed text/summary lengths)
8. Train and evaluate three linear regression models with different weighting strategies
9. Experiment with Lasso and Ridge regularization
10. Export best model predictions to submission file

## 🛠️ Technologies Used

Python, NumPy, Pandas, Scikit-Learn (LinearRegression, Lasso, Ridge, PCA, LDA, TF-IDF, CountVectorizer), NLTK, Matplotlib, Seaborn, pyLDAvis, Jupyter Notebook, Git

## 📚 References

S. Kapadia – "Topic Modelling in Python: Latent Dirichlet Allocation (LDA)"<br>
Y. Berdugo – "Review Rating Prediction: A Combined Approach"<br>
Chevalier, J. A., & Mayzlin, D. – "Effect of Word of Mouth on Sales: Online Book Reviews"<br>
Liu, Y. – "Word of Mouth for Movies: Its Dynamics and Impact on Box Office Revenue"<br>
Vermeulen, I. E., & Seegers, D. – "Tried and Tested: The Impact of Online Hotel Reviews on Consumer Consideration"<br>
Luca, M., & Zervas, G. – "Fake It Till You Make It: Reputation, Competition, and Yelp Review Fraud"<br>

## 👥 Authors & Acknowledgments

This research was conducted by Shreyas Khandale, Prathamesh Patil (https://github.com/PrathameshPatil547), and Rohan Patil (https://github.com/rohanpatil2), published in IJRASET, October 2023.

🔗 Paper Link: [Amazon Fine Food Review Analysis](https://www.ijraset.com/best-journal/amazon-fine-food-review-analysis)<br>
DOI: https://doi.org/10.22214/ijraset.2023.55930

## 📄 License

This project is licensed under the MIT License – see the LICENSE file for details.
