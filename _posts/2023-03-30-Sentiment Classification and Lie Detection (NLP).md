---
title: Healthcare Price Prediction Model
date: 2023-03-30
categories: [Blogs, Machine Learning 
tags: [Machine Learning, NLP, Sentiment Classification, Lie Detection, Multinomial Naive Bayes, SVM, Decision Tree, Random Forest, Gain Ratio, Feature Selection, R]

---

### Background and Goal
There are many machine learning solutions to detect if a person is lying or not. The goal of this mini project is too build sentiment classification and lie detection using the reviews of hotels in the United States. The detailed objectives are as follows.
- To select the best features to build the models using gain ratio scores. 
- To understand the difference between sentiment classification and lie detection and conclude which model can make a better performance, using Multinomial Naive Bayes, SVM, Decision Tree, and Random Forest models.

### Process and Conclusion
1. **Data Preprocessing & Text Preprocessing**
- This part is for preparing and exploring the given data set (the reviews of US hotels) for further machine learning project. 

- **EDA**: The data set has 35,437 reviews with the following three attributes. 
	1.  **`is_positive`**: whether the review is positive or negative (positive = '`y`', negative = '`n`')
	2.  **`Reviewer_score`**: the review score (10 points scale)
	3.  **`review`**: actual reviews, string values 

- Included the following steps: handling missing values and converting the values of `is_positive` to numeric values. 

- **Text Preprocessing**: Defining a function to implement text preprocessing using the following classifiers from NLTK library.
		- Sentence Tokenizer
		- Stopwords
		- Regexp Tokenizer
		- WordNet Lemmatizer
		- Porter Stemmer
		(code screen shot)
		
2. **Vectorization and Feature Selection**
- This part is vectorizing the text data using count vectorization and TD-IDF vectorization and selecting best feature by calculating gain ratio scores for further data modeling.
- (table) features selected in countv
- (table) features selected in td-idf

4. **Data Modeling**
- This part is building sentiment classification and lie detection model for the preprocessed data in previous parts. 
	- Sentiment Classification: MultinomialNB (Naive Bayes), SVM (Support Vector Machine)
	- Lie Detection: Decision Tree, Random Forest

5. **Evaluating the Models**
- This part is comparing the results of each algorithm and think about the next  step for improvements of those models. 
