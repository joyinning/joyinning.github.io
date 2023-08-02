---
title: Top 100 Songs in Music Streaming Companies
date: 2023-04-25
categories: [Projects, Data Analysis] 
tags: [Data Analysis, Data Mining, Data Visualization, pandas, numpy, matplotlib, Music Streaming, Python]

---

### Objectives
The goal of the mini-project is to analyze the popularity and audio features of songs selected by giant companies in the music-streaming (or reviewing) industry, including  **_Spotify_**,  **_Rolling Stone_**,  **_Billboard_**, and  **_Red Music Company_**.

Through this project, we can answer the following questions.

1.  _What is the standard(s) of each company to select the best song?_
2.  _Are the best songs popular in public?_

**Note**  
All the information is in the Spotify Web API, even though these songs are selected from different music-streaming companies.

### Process
1. **Data Collection**
- This part is collecting data related to songs in the rank of each company, using Spotify API and ***spotipy***, which is a useful library for Spotify Web API to get information from the Web API without writing complex codes. 
- In this part, the following information of each music ranking chart would be collected: Artist's name, Genre, Popularity of the song, and audio features). It is required to understand the structure of the Spotify playlist object.

2. **Data Analysis**
- This part is analyzing collected data sets, exploring informative insights from them, and answering the following questions.

	-  _Which audio characteristics does each playlist have?_
	-  _Are the selected music really popular in public?_
	- _What are the relationships among the popularity and audio features?_

### Conclusions
1. Data Collection: Collected required information from Spotify Web API and created data frames for further analysis.
	- Sample 

2. Data Analysis
	
	-  _Which audio characteristics does each playlist have?_
		- 
	-  _Are the selected music really popular in public?_
		- The songs selected by **Billboard** are the most popular songs in public.
		- **Rolling Stone** selected the songs in various range of popularity. 
	- _What are the relationships among the popularity and audio features?_
