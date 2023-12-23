---
title: Road Safety Analysis
date: 2023-12-15
categories: [Projects, Machine Learning] 
tags: [Machine Learning, PySpark, Decision Tree, SVM, Linear Regression, Random Forest, KMeans, Anomaly Detection, Classification, Clustering]
pin: true
---

[![Open in Github Page](https://img.shields.io/badge/Hosted_with-GitHub_Pages-blue?logo=github&logoColor=white)](https://github.com/joyinning/Motor-Crashes-Safety-Analysis/blob/main/Road_Safety_Analysis.ipynb)

# Road Safety Analysis
## PART 1 Project Overview & Environment Setting
### **Project Overview**
**Background** <br>
Over the last five years, fatalities resulting from vehicle accidents on Syracuse streets have risen by over 70%. Also, incidents involving severe injuries from crashes have seen a 12% increase on the street in Syracuse during the same timeframe.
<br>
<br>
**Business Objective** <br>
Considering the background mentioned above, the business objective in this project is to minimize the occurrence of vehicle-related accidents on Syracuse streets, thereby reducing both severe injuries and fatalities.
<br>
<br>
**Project Goal** <br>
The goal of this project is to decipher the intricate relationship between various factors by utilizing advanced machine learning techniques in order to provide the solutions of the business objective.
<br>
<br>
**Predictions** <br>
Through the project, we will answer the following questions (predictions).
1. *Can we predict the time of that day of accidents, given the road information, weather, etc?*
2. *Can we predict the event type based on time, road condtions, or weather conditions?*
3. *Are there any specific patterns in accidents during certain weather, lighting, or road surface conditions?*
4. *Are there distinct groups or clusters of accidents based on similar conditions?*
5. *Can we identify anomalies or outliers in accident occurrences based on the collected attributes?*

### **Environment Setting**
Before the research, this step is for setting up the environment for analysis and modeling. The main module we used in the project is PySpark. <br>

## PART 2 Exploratory Data Analysis
Explore and analyze the given dataset through the following methods to select the best features for better performance of machine learning models. We will conduct the following strategies.
### **Data Structure**
- The dataset is collected from the case information of motor crash from New York State Open Data Portal and NOAA (National Oceanic and Atmospheric Administration) Climate Data Online Tool. This dataset contains **23,638 observations with 31 variables**.
- We divided the variables except event_descriptor (target) into 5 categories as follows.
![image](https://github.com/joyinning/joyinning.github.io/assets/123600666/a34a5330-529d-494c-8fbe-34d4ccd7a0e4)
### **Data Analysis & Correlations**
1. ***Date and Time Information***
- Mostly there are accidents at 16:00 on Friday or in the spring season (Jan ~ Mar).
- It doesn’t have a significant relationship with other factors.
  ![image](https://github.com/joyinning/joyinning.github.io/assets/123600666/b0a52a93-0dde-426c-9d51-96eb243ba189) ![image](https://github.com/joyinning/joyinning.github.io/assets/123600666/0d7a2118-3382-4fc6-821f-ded079365fa4)
2. ***Accident Information***
- Most accidents result from colliding with other motor vehicles (1 ~ 2 cars) in a situation when a car runs into another vehicle in front of it or property damage accident. ![image](https://github.com/joyinning/joyinning.github.io/assets/123600666/f6baf303-241e-4e65-8fdb-a90207c74097)
- The relationship between Event Descriptor and the Number of vehicles involved has the highest (negative) correlation.
  ![image](https://github.com/joyinning/joyinning.github.io/assets/123600666/b8d19090-214e-4049-9b4a-d1c5d6c13be4)

3. ***Environmental Factors***
- Most accidents are caused in the daylight.
  ![image](https://github.com/joyinning/joyinning.github.io/assets/123600666/830c516d-58ec-40c7-a2c7-ed88c18967fe)
- Road surface conditions and the weather conditions (cold, foggy, etc) are highly related.
  ![image](https://github.com/joyinning/joyinning.github.io/assets/123600666/700f2355-84a1-4c90-a807-5518ef575662)

4. ***Weather Conditions***
- The weathers conditions do not seem to significantly affect accidents. (Mostly occurred in the clear weather conditions.) Accidents frequently occur in cold or foggy conditions.
  ![image](https://github.com/joyinning/joyinning.github.io/assets/123600666/fb27ab17-a64b-4628-a3d3-d6dea3077e2c)

5. ***Traffic Control and Pedestrian Information***
- Traffic control and pedestrian information is slightly related to the accident information.

## PART 3 Modeling
![image](https://github.com/joyinning/joyinning.github.io/assets/123600666/8f0364e0-2cdb-40eb-b1c3-1d79de650664)
1. Classification- Predictive Modeling: Find the best features and build the model to predict the time/date or the event type of accidents.
2. Clustering: Create distinct clusters (groups) of event descriptors based on the selected features and find the specific patterns in accidents of each cluster.
3. Anomaly Detection: Based on the final clustering model, find the anomalies (outliers) in the accidents.

### **1. Classification- Predictive Modeling**
Create classification models for the target variables (hour_category and event descriptor)
1. **Process**
![image](https://github.com/joyinning/joyinning.github.io/assets/123600666/67a250c8-242a-45fb-b389-77c94d2095ff)
2. **Modeling**
  - Time(Hour_category): Weather conditions (type, snow/wind) and road conditions have a strong association in this model.
    ![image](https://github.com/joyinning/joyinning.github.io/assets/123600666/803b778a-789a-4d68-a49d-f76b95169f80)
  - Event Descriptor: Hour_category, weather conditions (type, snow/wind), and road conditions can be better features in this model.
    ![image](https://github.com/joyinning/joyinning.github.io/assets/123600666/9b830b8f-db02-416e-b505-6a7c2469179b)
3. **Evaluation**
- The evaluation scores of time(hour) predictive models demonstrate moderate overall performance across models, with Decision Tree exhibiting slightly higher performance in accuracy and precision compared to other models.
  <img width="1098" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/c8eef644-ff34-442c-9ae5-a0df7769b1f5">
- All models demonstrate consistent high accuracy and recall, suggesting robust predictive capabilities, albeit with slightly varied precision scores, showcasing Logistic Regression having slightly higher precision among the models listed.
  <img width="1088" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/75af885f-38d0-4dd4-8b3d-82e32da9467a">

### **2. Clustering**
Build the best KMeans model to create clusters and define specific patterns in the given accidents. 
1. **Process**
- ***Assumptions***: Build the draft KMeans model based on the two assumptions (Selecting features in categories or correlations), then select the best model by comparing visualizations and scores
- ***Modeling Process***: Two potential approaches were considered for constructing the model in response to the question: “Choosing features based on variable categories or correlations might serve as a viable criterion for creating clusters.” (In this scenario, the 'Event Descriptor' variable was divided into two parts: 'Event_descriptor_Type' and 'Event_descriptor'. For the analysis, only 'Event_descriptor_Type' was utilized.)
![image](https://github.com/joyinning/joyinning.github.io/assets/123600666/14e348b4-2f29-4d63-a1ce-13779425a238)
2. **Modeling**
- ***Assumption 1***: Through categories number 1~5, we recognised that the Means model with factors in the accident information category slightly createds better clusters in terms of event descriptor.
    ![image](https://github.com/joyinning/joyinning.github.io/assets/123600666/517b1fbb-1ce3-49ff-a8b3-76580af203db)
- ***Assumption 2***: Based on the correlations of each feature, we will select only Number of Vehicles Involved and Collision Type Descriptor as features of the KMean model, which have the highest correlation values.
    <img width="1246" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/a96ae631-3496-43fe-9c25-234f035c41a0">
3. **Application & Evaluation**
- ***Improvement***: The methodology involved building KMeans algorithms for each assumption, comparing their performances and results, improving by applying for PCA technique, and evaluating with PCA visualization, sum of squared errors, and silhouette scores to identify the optimal model. 
- ***Final Model***: By comparing visualization outcomes (Sum of Squared Errors, Silhouette), the KMeans models from Assumption 1 exhibited distinct, well-defined clusters. Considering both visualization and scores, the optimized KMeans model of Assumption 2 – Trial 2 (Corr_Trial 1) demonstrated the most significant enhancement compared to the default model. Consequently, the KMeans model from assumption 2 - trial 2 (utilizing Number of Vehicles Involved and Collision Type Descriptor as features) was chosen to identify specific patterns within each cluster. ![image](https://github.com/joyinning/joyinning.github.io/assets/123600666/80516d95-843a-4cf7-becf-1cff6390f4e0)
- ***Application***: These clusters primarily represent various collision scenarios involving multiple vehicles, such as overtaking, rear-end collisions, and right-angle impacts, each occurring with varying frequencies and police report filings, primarily resulting in property damage. Moreover, in terms of environmental conditions, a majority of these incidents transpire during daylight hours on straight and level roads, typically featuring dry road surfaces.
<img width="1249" alt="Screenshot 2023-12-22 at 8 41 27 PM" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/08dbc17f-3133-4095-a493-4d84300dde93">

### **3. Anomaly Detection**
1. **Process & Modeling**: Employing the KMeans algorithm on accident data, an advanced anomaly detection model was developed to address the above question.
The anomaly detection model was constructed through several stages: Preprocessing, involving StringIndexer, One-hot Encoding, StandardScaler, and PCA; Modeling, which utilized KMeans and a UDF for distance calculation with the squared_distance function from the pyspark.ml.linalg.Vectors module; and Application, focusing on establishing a threshold and identifying anomalies.
2. **Conclusion & Application**: In conclusion, the anomaly detection process determined the optimal threshold value of 0.413 for detecting anomalies within accident data points. Within the final KMeans model, 350 anomalies were discovered within clusters, showcasing patterns involving accidents with two cars and an undefined collision type descriptor. ![image](https://github.com/joyinning/joyinning.github.io/assets/123600666/2b335d85-7ee5-442b-b875-cd16e65217b3)

