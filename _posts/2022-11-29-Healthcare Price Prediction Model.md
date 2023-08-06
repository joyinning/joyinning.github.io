---
title: Healthcare Price Prediction Model
date: 2022-11-29
categories: [Projects, Machine Learning] 
tags: [Machine Learning, Healthcare, Decision Tree, SVM, Linear Regression, R]
pin: true
---

## Objectives
The goal is to build a prediction model on whether or not a healthcare cost of a customer will be expensive.
- To deliver the results with shiny apps website.
- To generate actionable insights for HMO(Health Maintenance Organization) on how to lower the cost of healthcare.

## Process and Results
### 1. **Data Cleaning**
- **Dealing with missing data points**: we removed 158 missing data points in ***bmi*** and ***hypertension*** variables. 
- **Inspecting the data set**: There are 7,502 examples with 14 features related to personal health information (cost, age, bmi, number of children, and etc.). 
- **Performing binning and transformation on variables**
	- Numeric to Categorical: age, bmi
	- Categorical to Logical: education level, the number of children
- **Setting the boundary for expensive or not expensive** 
	- Considering that 80% of people spent less than or equal to $5,789.4, we set the boundary for expensive or not to be **$6,000**. 
		- People who were charged more than **$6,000** will be labeled as ***expensive***, while people who paid less will be labeled as ***not expensive***. <br> <img width="200" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/75e15b25-e71a-4eb8-b7e0-4a14b4ded515">
### 2. **Exploratory Data Analysis with Visualization**
    
- **Bar Charts** demonstrated that the percentages of customers paying more than $6,000 can vary among different groups. <br>
<br> <img width="200" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/c3c7c9ff-35e5-46f6-875d-c77ded73d755"> <br>
  ***have_child***, ***is_educated***, ***location_type***, ***yearly_physical***, ***married*** don't have a significant difference. 

- **Histograms and box plots** displayed the distribution of customers who pay more or less than $6,000 by each variable and visualized the statistical summary. <br>
<img width="200" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/99b1ffe6-6b20-4e37-b59f-734187faf0a1"> <img width="200" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/6e7b1c7d-e64f-4f4d-93ce-1258bdd7a0cb"> <img width="200" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/160ab0cc-04a2-4237-9be7-142f16c858fb">
<br> People who has the following health condition (or personal information) usually paid for their healthcare highly. 
	- ***Age***: 50-59
	- ***BMI***: obesity
	- ***Location type***: urban
	- ***Exercise***: Not-active (no exercise)
	- ***Smoker***: Yes
	- ***yearly_physical***: No (not well visit with their doctor during the year)
	- ***gender***: male
	- ***is_educated***: yes
	- ***married***: yes
	- ***have_child***: yes
- **Mapping** showed the distribution based on geographical information. <br> <img width="400" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/016fd95c-ff52-4691-a062-cd2f543991e1"> <br>
	- People who live on ***New York state*** have higher chances of paying more than $6,000 on their healthcare.

### 3. **Data Modeling** 
The prediction model simulation in Shiny Apps [Link](https://haotianshen.shinyapps.io/FinalProj/?_ga=2.151311673.1694501232.1670083961-1568296780.1670083961)
- **Modeling**: Applied the supervised and unsupervised algorithms and compared the results to find the best prediction model using accuracy and sensitivity rates. The algorithms and results are in the below table. <img width="948" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/37992dcd-212a-440c-9e71-a99a1df325aa">

	1. **Linear Regression**
    - We used numeric predictors (age, bmi, and the number of children)
    - Although all of the predictors are significant, the model only explain 15,69% of the data set, which is quite low.
    - The sensitivity is 0.8705, which means the model predicted 87% of the expensive healthcare prices in the dataset.
    - The accuracy rate is 77%, which is less than the 'No Information' rate (80.29%)
    - Based on these results, we would say the linear model is not a good prediction model in general. <br>
     <img width="200" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/95cacccc-1a76-46e2-a3c5-880f36b1bb5d">
     <img width="200" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/e972aa27-072b-4dc7-9ff6-b0c9cdc9c5d6">
     <img width="200" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/0df43a9e-5279-4d4c-9169-a6d11b28aead">

	2. **Decision Tree**
		1.  Building Decision Tree Model using all features except hypertension
			- The sensitivity is 0.9714, which has been significantly improved compared with linear model. The accuracy rate is also higher than no information rate (90.84%).
			- Considering that we put all features in the model, we tried to simplify the model by turning numeric variables into categorical variables. <br>
   <img width="300" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/0b5f5186-7017-477a-bf24-1102c6b872f9"> <br>

		2. Building Decision Tree Model using all features that are converted to categorical.
			- The sensitivity rate goes up to 0.9725 and accuracy was significantly improved compared to no information rate as we simplified the features. (91.33%)
			- Tried to remove less important predictors and build the same model again.
      <img width="300" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/1d7ed93b-d826-45a5-8353-fba033692b60"> <br>
		3.  Remove gender, have_child, hypertension.
			- The sensitivity rate goes up to 0.9758 when simplified some of predictors.<br>
      <img width="200" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/d5d928e0-94fa-41c0-ba10-9fdbbd4bf879">
      <img width="400" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/7337b433-cbf7-4fd4-9817-23286885ee11">
      <br>

	3. **SVM Model**: Building Decision Tree Model using all features except hypertension and converted to categorical.
  		- Sensitivity and accuracy rate are less than those in the Decision Tree Model.
- **Further Exploration with unsupervised machine learning**: Used unsupervised learning models (Associate Mining and K-Means clustering) to get more insights on cost and features. 
   1. **Associate Mining**: checking the importance of each variable to find the best predictors for the prediction model.
    - The following table shows the top 5 rules (sorted by support) in the Associate Mining model. <img width="941" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/bea039df-0951-4585-b899-d7dcc31a881f">
    - The most supported association here indicated that expensiveness relates to ***bmi*** and ***smoker***.

   2. **K-Means Clustering**: According to associate mining and the bar graph, ***bmi*** might be a most signficiant predictor of cost. Therefore, create clusters using ***bmi*** and ***cost*** and adjust the cost boundary on whether the healthcare price is expensive or not, if needed.
    <img width="568" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/11f088a6-837a-40ac-9cb6-2a38e136749c"> <br>
    - Divided the data set into five clusters, the lowest cost of the first cluster at the top, which is $12,282, could be considered as the boundary.
    
- **Conclusion**: Based on the results of the modeling and further exploration steps, the final model contains the following predictors and machine learning algorithm. <br>
<img width="646" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/defbbef3-a04e-4f5c-8df5-75971595ff38">

  > 1. ***Predictors***: age, bmi, smoker, exercise, expensive <br>
  > 2. ***Algorithm***: Decision Tree <br>
  > 3. ***Accuracy***: 96.84% <br>
  > 4. ***Sensitivity***: 98.81% <br>
  > 5. Notes
  > - The simulation require the train and test dataset as input. Find on the [Link](https://github.com/joyinning/r_healthcare_price_prediction/tree/main/data%20sets)
  > - The expensive predictor indicates whether or not the healthcare cost of each customer.

### 4. **Business Suggestions**
- Only certain factors are needed to build a model with great sensitivity, and therefore the cost for collecting and processing the less significant data could be saved. <br>
- Certain groups of people tend to be overcharged. Therefore, campaigns like smoking cessation programs (i.e. targeting smokers), regular yoga sessions (i.e. targeting less active group) could be initiated to promote healthy lifestyle. <Br>
- Differences among States have brought our attention to how income level, tax, and socioeconomics statues might affect health cost. Our suggestion is that a nationwide standard to be set for maximum cost in healthcare. <br>
