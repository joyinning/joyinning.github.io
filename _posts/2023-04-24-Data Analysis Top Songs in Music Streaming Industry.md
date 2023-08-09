---
title: Top 100 Songs in Music Streaming Companies
date: 2023-04-25
categories: [Projects, Data Analysis] 
tags: [Data Analysis, Data Mining, Data Visualization, pandas, numpy, matplotlib, Music Streaming, Python]

---

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/joyinning/Data-Analysis_Top-Songs-in-Music-Streaming-Companies/blob/main/Data%20Analysis%3A%20Top%20100%20songs%20in%20Music%20Streaming%20Companies.ipynb)
<br>

### Objectives
The goal of the mini-project is to analyze the popularity and audio features of songs selected by giant companies in the music-streaming (or reviewing) industry, including  **_Spotify_**,  **_Rolling Stone_**,  **_Billboard_**, and  **_Red Music Company_**.

Through this project, we can answer the following questions.

1.  _What is the standard(s) of each company to select the best song?_
2.  _Are the best songs popular in public?_

**Note**  
All the information is in the Spotify Web API, even though these songs are selected from different music-streaming companies.

### Process
1. ***Data Collection***
- This part is collecting data related to songs in the rank of each company, using Spotify API and ***spotipy***, which is a useful library for Spotify Web API to get information from the Web API without writing complex codes. 
- The following information of each music ranking chart would be collected: Artist's name, Genre, Popularity of the song, and audio features). It is required to understand the structure of the Spotify playlist object.

2. ***Data Analysis***
- This part is analyzing collected data sets, exploring informative insights from them, and answering the following questions.

	  - Which audio characteristics does each playlist have?
	  - Are the selected music really popular in public?
	  - What are the relationships among the popularity and audio features?

### Conclusions
1. ***Data Collection***: Collected required information from Spotify Web API and created data frames for further analysis. <img width="1058" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/5fe6927a-3be0-4775-9f73-e0dc83a40734">
 

2. ***Data Analysis***
	
	-  **Which audio characteristics does each playlist have?** <img width="583" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/5156beae-7cc8-4c5e-9b6d-7362bbfa0943">
        - The songs in Rolling Stone’s playlist have active audio features: danceability, energy, loudness, mode, speechiness, instrumentalness
        - Billboard ‘s best songs are acousticness.
        - Spotify’s best songs have a longer duration than others.
        - Red Music may consider liveness, valence, and tempo as they select the best songs. 

	-  **Are the selected music really popular in public?** <img width="400" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/70040175-8eda-4548-98f5-fc4b048aca5f">
        <br>
		    - The songs selected by **Billboard** are the most popular songs in public.
            - The average scores of popularity of each playlist are as follows. The songs selected by **Billboard** are the most popular in public. 
                -  Billboard:  85.08
                -  Rolling Stone:  65.52
                -  Spotify:  63.07
                -  Red Music:  73.83
         - **Rolling Stone** selected the songs in various range of popularity. 
	- **What are the relationships among the popularity and audio features?**
    
      1. ***Billboard*** <img width="633" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/a4f9434d-c3cf-463d-95f1-cffadb8b31aa">

      2. ***Rolling Stones*** <img width="622" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/05ee878f-9ffc-4f7f-96b1-aebcd1ef9bf5">

      3. ***Spotify*** <img width="628" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/3728d768-569e-46c9-9fb0-bddb98f5ff2d">

      4. ***Red Music Company*** <img width="632" alt="image" src="https://github.com/joyinning/joyinning.github.io/assets/123600666/39cf7adf-4d13-419c-aef4-741992b976a4">

      6. **Conclusion**
          - **Billboard** and **Red Music Company** selected the songs with high instrumental quality as the best and actually, these songs are popular in public. 
          - The popular songs selected by **Spotify** as the best songs have a high liveness feature.
          - The **Rolling Stones** selected the best and most popular songs that contain a high danceability sound. 
          - Most songs that are very **loud** in the playlists may also have the audio features of **energy**. 



