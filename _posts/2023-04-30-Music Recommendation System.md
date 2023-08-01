---
title: Music Recommendation System
date: 2023-04-30
categories: [Projects, Machine Learning] 
tags: [Machine Learning, Clustering, Music Recommendation System]

---

### Introduction
Big companies (Spotify and Apple Music) have already adapted and developed the new technology trend by releasing their innovative ML-based approaches and services, including the AI solution to recommend songs to users. Through this algorithm, it is possible to increase user satisfaction and engagement in the music streaming services as well as make enormous profits against competitors.

### Objectives 
We will understand what the music recommendation system is, explore all possible machine learning models for building the system, and solve the following business and technical questions.

1.  Which model can be applied to create the music recommendation system?
2.  How do the models recommend songs to users?

### Process
1. **Exploratory Data Analysis (EDA)**
- This part is exploring the given data set to understand the basic data structure, the meaning of values, and the importance of features for building a music recommendation system.

2. **Modeling**
- This part is building music recommendation models with the audio features, based on  **Association Rules**  and  **Clustering**.
- The data modeling part will be implemented with the following steps.  
	1. Data Preprocessing 
		- Association Rule: Discretization, One-Hot Encoding
		- Clustering: Normalization, Dimensionality Reduction using PCA and t-SNE
	2. Data Modeling 
		- Association Rule: apriori(), association_rules()
		- Clustering: K-means clustering, DBSCAN clustering, Hierarchical (ward linkage) and Agglomerative clustering, and Spectral clustering
	3. Model Evaluation
		- Association Rule: Finding the best parameter among the followings: Confidence, Lift, and Support
		- Clustering: Calculating Avg. Silhouette Scores and Calinski-Harabasz Scores

3. **Preliminary Analysis**
- This part is defining the preliminary conclusion from the above research, implementing application (developing recommendation systems), and make suggestions and improvements for further studies.

### Conclusions
1. Association Rule
	- The best parameter: support (Min = 0.05, Threshold = 0.5)
	- Most active digital songs contains instrumental-based features in the frequent item sets. 
		- Active: Danceability, energy, valence, and loudness.

2. Clustering
	- Best Model: K-Means Clustering
	- It shows the highest performance of matching data points in the own clusters and better clustering results. 

3. Results
- ***1.  Which model can be applied to create the music recommendation system?***
	- K-Means clustering showed the best result of recommending music based on audio features. 
- ***2.  How do the models recommend songs to users?***
	- It partitions a dataset into k clusters. In the below scatter plot, we could observe 5 clusters of the given dataset.
