---
title: Sentiment Classification and Lie Detection (NLP)
date: 2023-03-30
categories: [Blogs, Machine Learning 
tags: [Machine Learning, NLP, Sentiment Classification, Lie Detection, Multinomial Naive Bayes, SVM, Decision Tree, Random Forest, Gain Ratio, Feature Selection, R]
---

## Background and Goal
There are many machine learning solutions to detect if a person is lying or not. The goal of this mini project is too build sentiment classification and lie detection using the reviews of hotels in the United States. The detailed objectives are as follows.
- To select the best features to build the models using gain ratio scores. 
- To understand the difference between sentiment classification and lie detection and conclude which model can make a better performance, using Multinomial Naive Bayes, SVM, Decision Tree, and Random Forest models.

## Process and Conclusion
### 1. **Data Preprocessing & Text Preprocessing**
- This part is for preparing and exploring the given data set (the reviews of US hotels) for further machine learning project. 

- **EDA**: The data set has 35,437 reviews with the following three attributes. 
	1.  **`is_positive`**: whether the review is positive or negative (positive = '`y`', negative = '`n`')
	2.  **`Reviewer_score`**: the review score (10 points scale)
	3.  **`review`**: actual reviews, string values 

- **handling missing values**: investigating missing values
- **Value Transformation**: converting the values of `is_positive` to numeric values. 

- **Text Preprocessing**: Defining a function to implement text preprocessing using the following classifiers from NLTK library. 	<img width="869" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/735a61dc-7cd5-4e2d-af85-3dc6ea431179">
  1. Sentence Tokenizer
  2. Stopwords
  3. Regexp Tokenizer
  4. WordNet Lemmatizer
  5. Porter Stemmer
		
### 2. **Vectorization and Feature Selection**
- This part is vectorizing the text data using count vectorization and TF-IDF vectorization and selecting best feature by calculating gain ratio scores for further data modeling. <br>
  <img width="300" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/f5b3b7b7-4edf-4b42-a38f-01f927b4a72e"> <img width="300" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/68e1cd4f-ee6e-4d42-9e14-11db07ef8086">


### 3. **Data Modeling**
- This part is building sentiment classification and lie detection model for the preprocessed data in previous parts. 
	- Sentiment Classification: MultinomialNB (Naive Bayes), SVM (Support Vector Machine)
	- Lie Detection: Decision Tree, Random Forest

### 4. **Evaluating the Models**
- This part is comparing the results of each algorithm and think about the next  step for improvements of those models. <br>
   <img width="578" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/4160a827-1665-402e-8b00-315102d808bc">
   <img width="633" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/4caca2f5-cb2d-46d5-8b08-b3a5c55ff8cb">
  - According to the above results, sentiment classifications using Multinomial NB and TD-IDF (C-2) and SVM with count vectorization (D-1) models have the best accuracy score, about 0.969. We would interpret that the models predict the values correctly.
  - However, the roc auc score of these models shows the worst scores among the models used in the research, about 0.5. The confusion matrix of these models also showed the lowest ability of these models to divide the data into positive and negative clearly. 

### 5. **Conclusion**
1. Feature Selection using two vectorization techniques: count vectorization and TF-IDF
  - Count vectorization showed the results focused on sentiment words. The top 5 features in the count vectorization are positive, negative, great, rude, and dirty, which are emotional words. However, the TD-IDF focused on the categories (or conditions that we use in choosing the best hotel) rather than emotions because the four fifth of the top 5 features in the TD-IDF are room, staff, hotel, and location. 
2. Sentiment Classification and Lie Detection Models
  - When using the features selected in this research, the sentiment classification with the MultinomialNB model can detect whether a review is a lie or not better than lie detection. However, all models used in the research showed a lower score of the ability to distinguish between positive and negative values, even though they have a good accuracy score. For further improvement, we should consider how to make a balanced confusion matrix using the data set. 
