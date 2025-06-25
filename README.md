# 🛍️ Flipkart Product Review Analysis: NLP & Customer Satisfaction Modeling

## 🧩 Problem Statement

As a Marketing Data Analyst, I was tasked to uncover what drives customer satisfaction on Flipkart using 205,000+ customer reviews. The goal was to:

Understand customer opinions and emotional tone.

Verify if written feedback aligns with customer satisfaction.

Predict star ratings using sentiment and review characteristics.

Provide actionable recommendations for marketing and product stakeholders.

## 📌 Project Brief

This project covers the complete review analytics pipeline, from data wrangling to regression modeling.

### 🔄 1. Data Cleaning & Preprocessing:

- Removed duplicates, missing values, and outliers using IQR method.
  
- Standardized text (regex: removed symbols, trimmed spaces), and corrected messy texts.
  
- Lemmatized review summaries for sentiment analysis and keyword extraction (for wordcloud analysis).

### 🧠 2. Sentiment Analysis:

- Applied **VADER (NLTK)** sentiment scoring on lemmatized summaries.

- Built a **custom Enhanced Sentiment Classifier** ranging from (Very Positive to Very Negative).

- Finetuned polarity thresholds and validated performance against actual ratings.

### 📊 3. Visual & Exploratory Analysis:
- Generated multiple visualisations:

  - Wordclouds (Positive and Non-Positive feedback)
 
  - Sentiment distributions and boxplots (summary length across sentiments)
 
  - Stacked bar chart (Sentiment breakdown across 1-5 star ratings)
 
  - Heatmap (Correlation matrix for sentiment score, rating, price, and length)
 
### 🔢 4. Regression Modeling:
- Performed Linear Regression to predict `Rate` from:
  - Sentiment Score
  - Review / Summary Length
  - Product Price
  - One-hot encoded Enhanced Sentiment

- Evaluated with R2 Score (0.725), MSE, MAE

### 🔞 5. Insight Extraction:

- Used statistical outputs and visual patterns to answer core questions.

- Highlighted relationships between sentiment, text patterns, and customer rating.

## 📊 Dataset Description

- **Source:** [Nirali Vaghani, and Mansi Thummar. (2023). Flipkart Product reviews with sentiment Dataset [Data set]. Kaggle.](https://www.kaggle.com/datasets/niraliivaghani/flipkart-product-customer-reviews-dataset/data)

- **License:** [Open Data Commons Attribution License (ODC-By v1.0)](https://opendatacommons.org/licenses/dbcl/1-0/)

- Size: 205053 rows and 6 columns.

1. Product_name: Name of product
2. Product_price: Price of product
3. Rate: Customer rating (1-5)
4. Review: Full review text
5. Summary: A descriptive information of customer's thought on each product.
6. Sentiment: Contains 3 labels - Positive, Negative, and Neutral (Based on Summary)


## 📅 Methodology Snapshots & Insights

### 🌐 WordCloud - All Feedback
<img width="638" alt="image" src="https://github.com/user-attachments/assets/22076075-beef-4d44-b65a-7544971345bd" />

- Customers frequently mention: `good`, `excellent`, `thank`, `worth`, `value`, indicating overall positivity. The wordcloud is dominated by mostly positive words, showing that consumers of Flipkart generally have a positive outlook on the brand. 

### 🌐 WordCloud - Non-Positive Feedback (What Are Dissatisfied Customers Saying?)
<img width="636" alt="image" src="https://github.com/user-attachments/assets/6a3f300d-0127-404a-9116-99ce86ee6996" />

- After isolating the `Positive` and `Very Positive` sentiments:
  - Frequent negative signals include `dont buy`, `poor`, `quality`, `waste money`, `broken`, `worst`, `small size`, `stopped working`, and `service bad`.

### 📊 Sentiment Distribution
<img width="597" alt="image" src="https://github.com/user-attachments/assets/f41e2ee4-b290-4090-a30d-260c3bc9b1c9" />

- Over 60% of reviews are `Very Positive`.

- `Neutral` and `Negative`, and `Very Negative` reviews form only about 20% combined.

### 🏛️ Correlation Heatmap
<img width="620" alt="image" src="https://github.com/user-attachments/assets/50f3bcc2-c593-43f1-b148-8e9dd2ee4109" />

- `Sentiment_score` and `Rate`: +0.70 (strong positive correlation)

- `Product_price` & `Rate`: ~0.06 (weak positive correlation)

- `Summary_length` & `Rate`: -0.07 (weak negative correlation)

### 🛋️ Boxplot: Summary Length vs Sentiment
<img width="615" alt="image" src="https://github.com/user-attachments/assets/39d714dc-07ea-457d-a2bb-001c9f67de5f" />

- Very Negative reviews are the longest (median around 8 words).

- Positive reviews are short and uniform.

### 🔺 Stacked Bar: Sentiment Composition by Rating
<img width="646" alt="image" src="https://github.com/user-attachments/assets/59c0d908-7b12-4776-acf6-02117c5a223f" />

- Sentiment aligns well with Ratings. **`Very Positive` = Rating 5, `Very Negative` = Rating 1.**

- Some **edge cases** (e.g. `Very Positive` sentiment appeared in 3 star rating), this reflects sarcasm or polite language.

**Cross Check Verification:** 
<img width="611" alt="image" src="https://github.com/user-attachments/assets/c73a942e-2595-47ae-ba65-f61df1bcdb18" />

< include a summary of what was written on jupyter notebooks > 

### 📊 Regression Results

<img width="594" alt="image" src="https://github.com/user-attachments/assets/15bd9855-c599-4b3e-9a0e-28362cb81a81" />

<img width="410" alt="image" src="https://github.com/user-attachments/assets/83afc422-3dfa-47f0-b0ac-140f250e7b84" />

### Pearson Coefficients

<img width="351" alt="image" src="https://github.com/user-attachments/assets/63cce804-a4fa-4084-b6c6-bdfebcd95f13" />





