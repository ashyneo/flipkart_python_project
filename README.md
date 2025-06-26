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
3. Rate: Customer rating (1-5) 1 being the worst; 5 being the best
4. Review: Full review text
5. Summary: A descriptive information of customer's thought on each product.
6. Sentiment: Contains 3 labels - Positive, Negative, and Neutral (Based on Summary)


## 📅 Methodology Snapshots & Insights

### 🌐 WordCloud - All Feedback (What Is The Overall Sentiment of The Brand?)
<img width="638" alt="image" src="https://github.com/user-attachments/assets/22076075-beef-4d44-b65a-7544971345bd" />

- To understand the overtone of Flipkart's customer reviews, I first **lemmatized** the Summary column by condensing words into their base form (e.g. 'loved' becomes 'love') and removed common stopwords like ('the', 'is', 'and'). I then generated the WordCloud above to visualize frequently used keywords across all reviews.

`Findings:` Customers frequently mention: `good`, `excellent`, `thank`, `worth`, `value`, indicating overall positivity. 

`Summary:` The positive words appear consistently across a large dataset of the 205k reviews, suggesting that Flipkart has a predominatly positive customer experience base.


### 🌐 WordCloud - Non-Positive Feedback (What Are Dissatisfied Customers Saying?)
<img width="636" alt="image" src="https://github.com/user-attachments/assets/6a3f300d-0127-404a-9116-99ce86ee6996" />

- To uncover key customer pain points, I filtered the dataset to include only reviews labeled as `Neutral`, `Negative`, and `Very Negative` using my `Enhanced_Sentiment` classifier. 

`Findings:` Common negative expressions and keywords revealed: 
  - `dont buy`, `waste money`, `poor quality`, `service bad`
  - `broken`, `stopped working`, `worst product`
  - Size related complaints: `small size`, `size`?
  - `average`, `low quality`

`Summary:` While the size of dissatisafied customer reviews is **significantly smaller** than Positive reviews, they reflect concerns that Flipkart can address about product reliability, misleading sizes, and poor after sales service.

<img width="220" alt="image" src="https://github.com/user-attachments/assets/8b5649dc-2d1e-4c20-8da2-7261173c39ec" />



### 📊 Sentiment Distribution
<img width="597" alt="image" src="https://github.com/user-attachments/assets/f41e2ee4-b290-4090-a30d-260c3bc9b1c9" />

- To provide a visual of the proportions of the five enhanced sentiment classes, I plotted a bar chart based on the percentages of each sentiments.

`Findings:` 
- Over 60% of all reviews are `Very Positive` (Strong satisfaction as expected based on Wordcloud findings)
- `Positive` (14%) and `Neutral` (11%) sentiments formed the mid range, likely representing reviews that are short, vague, or ambivalent words like "ok ok product", "not bad" or "fine".
- `Negative` (~4%) and `Very Negative` (~8%) sentiments are rare.

`Summary:` This suggests that highly critical reviews are in the minority, which reflects high customer satisfaction, effective issue resolution for most, or there could be an underlying cause: review selection bias, where satisfied customers are more likely to leave a feedback? 

The low volume of negative sentiment may also indicate that Flipkart's quality control and resolution management are generally effective even though a small percentage of dissatisfaction still warrants deeper attention as seen in the previous word cloud.


### 🏛️ Correlation Heatmap
<img width="620" alt="image" src="https://github.com/user-attachments/assets/50f3bcc2-c593-43f1-b148-8e9dd2ee4109" />

- I then use a heatmap to visualize the **pearson correlation coefficients** between crucial features like `sentiment_score`, `Rate`, `product_price`, and `summary_length`.

`Findings:` 
  - `Sentiment_score` and `Rate` has the strongest positive correlation of +0.70. The more positive the review text (as measured by VADER), the higher the customer rating. This makes sense and validates my VADER sentiment which captures customer satisfaction well.

  - `product_price` and `Rate` has a very weak positive correlation of +0.064. Ratings are not strongly affected by price and customer do not necessarily rate higher for more expensive items which is true. Satisfaction likely depends more on value perception.

  - `summary_length` and `Rate` has a slight negative correlation of -0.07. Longer summaries tend to be associated with lower or neutral ratings, which suggests that customers may write more when they have issues or mixed experiences.

`Summary:` Sentiemnt score is the strongest predictor of how a customer rates, which reinforces the value of my NLP sentiment analysis in customer experience. Price and summary length do not meaningfully impact rating scores as well, buttressing the analysis that expectation vs reality matters more than cost or verbosity. 

Albeit the correlation heatmap shows a brief overview of the relationships betwen each selected feature, it does not represent causation. 

### 🛋️ Boxplot: Summary Length vs Sentiment
<img width="615" alt="image" src="https://github.com/user-attachments/assets/39d714dc-07ea-457d-a2bb-001c9f67de5f" />

- Next, to explore how review length correlates to emotional tone, I plotted a boxplot to compare the `Summary_length` across each `Enhanced_Sentiment` classes.

`Findings:` 
  - In general, each sentiment category looks relatively uniform. `Very Negative` reviews have the highest median word count of around 8 words. It also has the widest interquartile range (IQR), showing a broad range of word count in how customers express dissatisfaction.

  - `Positive` and `Very Positive` reviews are shorter on average, and also more uniform in length, shown by the narrow IQR.

  - Outliers (Above 100+ words) are found in every sentiment class. Some users go into extended detail possibly to explain more stronger emotional reactions, have repetitive or storytelling behaviour. No lower outliers is present as words like "ok" or "bad" are too common to be flagged as unusual.

`Summary:` Dissatisfied customers tend to write longer and more varied reviews, possibly to justify their low rating or problems they face. Satisfied customers write more concise and uniform summaries that reflect brief praise. 

However, `Summary_length` alone is not a reliable predictor of satisfaction due to the high variability and presence of long reviews in all categories. Perhaps pairing `Review_length` with `Sentiment_score` could be useful to flag out potential negative experiences for any early intevention. 



### 🔺 Stacked Bar: Sentiment Composition by Rating
<img width="646" alt="image" src="https://github.com/user-attachments/assets/59c0d908-7b12-4776-acf6-02117c5a223f" />

- Finally, let's visualise the distribution of enhanced sentiment classes across the 5 rating levels (1 to 5).

`Findings:` 
   - As expected, customers who gave 5 for `Rate` are mostly `Very Positive`, and those who gave 1 for `Rate` are mostly `Very Negative`. This confirms strong alignment between customer rating and textual sentiment.

   - Those who gave 2 and 3 for `Rate` display a mixed sentiment distribution, which is common in real world reviews where a customer's experiences are nuanced or ambivalent. _(Bigne et al., 2023)_

   - A small share of `Very Positive` sentiments are in 3 star ratings. They are likely due to customers having high expectations e.g. (wrote "very impressive" but not fully satisfied.)
   
     **Polite language biases? Misalignment or sarcasm** (a limitation of the VADER model), or possibly **user incosistencies in rating and their words**. To verify this, **I will cross-check the ratings for this category.**

**Cross Check Verification:** 
<img width="611" alt="image" src="https://github.com/user-attachments/assets/c73a942e-2595-47ae-ba65-f61df1bcdb18" />

- I applied a filter for `Rate` == 3 and `Enhanced_Sentiment` == `Very Positive`, and I found:

  - Words like "Very impressive cooler..." were being categorised into `Very Positive` sentiment by VADER, which explains why despite its neutral tone.
 
  - Customers tend to use **very positive words** like 'awesome' but gave a 3 for `Rate`.

`Summary:` 
- Since the mismatch is rare and explainable, the classifier remains reliable and accurate for clear cases (1 or 5 star reviews). These edge cases provided me a useful insight.

- There is high overall alignment between sentiment and rating which confirms the strength of my `Enhanced_Sentiment` model.

- There are minor discrepancies in middle ratings but are explainable and acceptable, especially given the limitations of text-only sentiment analysis like VADER.

- The VADER model performs reliably across clear sentiment extremes, and these edge cases provides an opportunity to explore future improvements like incorporating sarcasm detection, or more complex behavioural nuanced modeling.

### 📊 Regression Results

<img width="594" alt="image" src="https://github.com/user-attachments/assets/15bd9855-c599-4b3e-9a0e-28362cb81a81" />

<img width="410" alt="image" src="https://github.com/user-attachments/assets/83afc422-3dfa-47f0-b0ac-140f250e7b84" />

### Pearson Coefficients

<img width="351" alt="image" src="https://github.com/user-attachments/assets/63cce804-a4fa-4084-b6c6-bdfebcd95f13" />



### References

Bigne, E., Ruiz, C., Pérez‑Cabañero, C., & Cuenca, A. C. (2023). _Are customer star ratings and sentiments aligned? A deep learning study of the customer service experience in tourism destinations_. Service Business, 17(1), 281–314. [https://doi.org/10.1007/s11628-023-00524-0 ] (https://www.researchgate.net/publication/368305619_Are_customer_star_ratings_and_sentiments_aligned_A_deep_learning_study_of_the_customer_service_experience_in_tourism_destinations)

Nirali Vaghani, and Mansi Thummar. (2023). _Flipkart Product reviews with sentiment Dataset_ [Data set]. Kaggle. [https://www.kaggle.com/datasets/niraliivaghani/flipkart-product-customer-reviews-dataset/data](https://www.kaggle.com/datasets/niraliivaghani/flipkart-product-customer-reviews-dataset/data)




