---
title: Healthcare Price Prediction Model
date: 2022-11-30
categories: [Projects, Machine Learning 
tags: [Machine Learning, Healthcare, Decision Tree, SVM, Linear Regression, R]

---

### Objectives
The goal is to build a prediction model on whether or not a healthcare cost of a customer will be expensive.
- To deliver the results with shiny apps website.
- To generate actionable insights for HMO(Health Maintenance Organization) on how to lower the cost of healthcare.

### Process and Conclusion
1. **Data Cleaning**
- **Dealing with missing data points**: Removed 158 missing data points in ***bmi*** and ***hypertension*** variables. 
- **Inspecting the data set**: 7,502 examples with 14 features related to personal health information (cost, age, bmi, number of children, and etc.). 
- **Performing binning and transformation on variables**
	- Numeric to Categorical: age, bmi
	- Categorical to Logical: education level, the number of children
- **Setting the boundary for expensive or not expensive** 
	- Considering the average cost, which is $4,049.5, set the boundary for expensive or not to be **$6,000**. 
		- People who were charged more than **$6,000** will be labeled as ***expensive***, while people who paid less will be labeled as ***not expensive***.
2. **Exploratory Data Analysis with Visualization**
- **Bar Charts**: demonstrated that the percentages of customers paying more than $6,000 can vary among different groups. 
	- ***have_child***, ***is_educated***, ***location_type***, ***yearly_physical***, ***married*** don't have a significant difference.
- **Histograms and box plots**: displayed the distribution of customers who pay more or less than $6,000 by each variable and visualized the statistical summary.  People who has the following health condition (or personal information) usually paid for their healthcare highly. 
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
- **Mapping**: showed the distribution based on geographical information. 
	- People who live on ***New York state*** have higher chances of paying more than $6,000 on their healthcare.
3. **Data Modeling**: The prediction model simulation in Shiny Apps [Link](https://haotianshen.shinyapps.io/FinalProj/?_ga=2.151311673.1694501232.1670083961-1568296780.1670083961)
- Applied the supervised and unsupervised algorithms and compared the results to find the best prediction model using accuracy and sensitivity rates.
| Model            | Details              | Results |
|---------------------|:---------------------------------:|:-----------:|
| Linear Regression     | Using numeric predictors (age, bmi, and the number of children)                                 | Sensitivity: 0.8705, Accuracy:           |
| Decision Tree            | ✓                                 | ✗           |
| Decision Tree            | ✓                                 | ✗           |
| Decision Tree            | ✓                                 | ✗           |

	- **Linear Regression**: using numeric predictors (age, bmi, and the number of children)
		- Although all of the predictors are significant, the model only explain 15,69% of the data set, which is quite low.
		- Based on the result of confusion matrix in this case, the sensitivity is 0.8705. The accuracy rate is below the 'No Information' rate. Therefore, we would say this model is not a good model. 
	- **Decision Tree**
		1.  Building Decision Tree Model using all features except hypertension
			- The sensitivity is 0.9714, which has been significantly improved compared with linear model. The accuracy is also higher than no information rate. 
			- Considering that we put all features in the model, tried to simplify the model by turning numeric variables into categorical variables.
		2. Building Decision Tree Model using all features  that are converted to categorical.
			- The sensitivity rate goes up to 0.9725 and accuracy was significantly improved compared to no information rate as we simplified the features.
			- Tried to remove less important predictors and build the same model again.
		3.  Remove gender, have_child, hypertension.
			- The sensitivity rate goes up to 0.9758 when simplified some of predictors. 
	- **SVM Model**: building with all features.
		- Sensitivity and accuracy rate are less than those in the Decision Tree Model.
	- **Associate Mining**: checking the importance of each feature.
		- The most supported association here indicated that expensiveness relates to bmi and smoker.

- The final model contains the following predictors and machine learning algorithm. <br>
  - ***Predictors***: age, bmi, smoker, exercise, expensive <br>
  - ***Algorithm***: Decision Tree <br>
  - ***Accuracy***: 96.84% <br>
  - ***Sensitivity***: 98.11% <br>
- Note 1) The simulation require the train and test dataset as input. Find on the [Link]() <br>
- Note 2) The expensive predictor indicates whether or not the healthcare cost of each customer is expensive based on the boundary, $12,282. <br>
4. **Business Suggestions**
- Only certain factors are needed to build a model with great sensitivity, and therefore the cost for collecting and processing the less significant data could be saved. <br>
- Certain groups of people tend to be overcharged. Therefore, campaigns like smoking cessation programs (i.e. targeting smokers), regular yoga sessions (i.e. targeting less active group) could be initiated to promote healthy lifestyle. <Br>
- Differences among States have brought our attention to how income level, tax, and socioeconomics statues might affect health cost. Our suggestion is that a nationwide standard to be set for maximum cost in healthcare. <br>
