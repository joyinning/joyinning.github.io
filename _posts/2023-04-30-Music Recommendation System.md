--- 
title: Music Recommendation System
date: 2023-04-30
categories: [Projects, Machine Learning] 
tags: [Machine Learning, Clustering, Music Recommendation System]
pin: true
---

### Preview
Build a music recommendation system based on audio features of 170,000 digital songs using Association Rule and Clustering in Python.


![image](https://github.com/joyinning/joyinning.github.io/assets/123600666/d28f0339-b955-45ed-9bb3-a37f50c44de7)
<br>
<br>
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/joyinning/python_music_recommendation_system/blob/main/music_recommendation_system_eunbi_kim_project_reference.ipynb)
<br>

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
	1. ***Data Preprocessing***
		- Association Rule: Discretization, One-Hot Encoding
		- Clustering: Normalization, Dimensionality Reduction using PCA and t-SNE
	2. ***Data Modeling***
		- Association Rule: apriori(), association_rules()
		- Clustering: K-means clustering, DBSCAN clustering, Hierarchical (ward linkage) and Agglomerative clustering, and Spectral clustering
	3. ***Model Evaluation***
		- Association Rule: Finding the best metric among the followings: Confidence, Lift, and Support
		- Clustering: Calculating Avg. Silhouette Scores and Calinski-Harabasz Scores

3. **Preliminary Analysis**
- This part is defining the preliminary conclusion from the above research, implementing application (developing recommendation systems), and make suggestions and improvements for further studies.

### Conclusions
1. **Exploratory Data Analysis (EDA)**
- ***Handle Outliers***: The numeric values in audio features are not on the same scale. We would solve this part for better outputs of the model, removing unnecessary columns or deploying normalization in the data preprocessing part. <img width="661" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/c4699fb5-35bf-4cef-8ac3-38eefe7e2201">
- ***Explore the Values***: There are 34,088 artists in the data set. Also the range of released year of songs in the data set is between 1921 to 2020. Most songs in the data set were released between 1950s and 2010s. <img width="601" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/bb956062-61da-46f7-8db9-86478ae6bb65">


2. **Modeling**
	1. ***Data Preprocessing***
		- ***Association Rule***: Used all the autio features, converted the numeric values into three categories (high, medium, and low), and then implemented one-hot encoding.
		- ***Clustering***: Based on the results of EDA, selected the following features: **valence, energy, instrumentalness, key, liveness, speechiness, and year_group**. Nomalized these values with MinMaxScaler() and conduct dimensionality reduction using PCA and t-SNE.
          - ***PCA***:  <img width="565" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/d7ab62ca-1bcc-446d-b2b4-37731f6b8eb3">
          - ***t-SNE***: <img width="595" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/f12f553d-ab9f-4b02-88e7-4d361af64238">


	2. ***Data Modeling***
		- ***Association Rule***: Calculated support, confidence, and lift values. <img width="846" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/37f3ea3b-1755-4b40-839e-735263e3bdb1">

		- ***Clustering***: K-means clustering, DBSCAN clustering, Hierarchical (ward linkage) and Agglomerative clustering, and Spectral clustering <img width="1001" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/4ca1c13b-38af-40b8-bb81-5876ed12a372">

	3. ***Model Evaluation***
		- ***Association Rule***: Tried to compare the results of the following metrics.
          - lift, confidence, support, lift + confidence + support
          - The best metric: support <img width="625" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/fad3f868-97bf-48f8-91af-3bd007797fdd">

		- ***Clustering***: Calculating Avg. Silhouette Scores and Calinski-Harabasz Scores <img width="1040" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/f43a16e2-dab4-4eac-8981-310a7adfa68f">
          - Based on the results, K-Means will be the best model to build clustering model.

                  - Avg. Silhouette Score (0.503): The data point in k-means clusters is very well mached to its own cluster, but not to neighboring clusters.
                  - Calinski-Harabasz Score (74711.500): It shows the better clustering results.


3. **Preliminary Analysis**
- The music recommendation system based on K-means clustering showed the relevant result.
  - Association Rule <br> <img width="591" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/c5ed9ac6-105d-4bfb-8f6a-4543abf330d7">

  - Clustering <br> <img width="623" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/d89c5ff2-d517-46c0-8652-1d9337da8fcb">
- ***1.  Which model can be applied to create the music recommendation system?***
  - The K-Means clustering model can be applied to build the optimized music recommendation system based on audio features of digital songs.
- ***2. How do the models recommend songs to users?***
  - It partitations the data set, which contains the audio features (valence, energy, instrumentalness, key, liveness, speechiness, and year_group), into 5 clusters. Based on the clusters, the music recommendation system finds the best cluster for a new input data. 
