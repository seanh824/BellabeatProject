# Bellabeat Case Study

## Introduction
Bellabeat is a tech-driven wellness company for women that was founded by Urška Sršen and Sando Mur in 2013.  Through the collection of data on sleep, stress, activity, and reproductive health Bellabeat has given women the knowledge and power of their health.  Bellabeat’s product line includes:
- Bellabeat App (a hub for all data tracked by Bellabeat products)
- Leaf (can be worn as a bracelet, necklace, or clip that tracks activity, sleep, and stress)
- Time (a smartwatch that tracks activity, sleep, and stress)
- Spring (a water bottle that tracks your hydration levels and connects to the Bellabeat App)
- Bellabeat Membership (gives 24/7 access to personalized guidance on nutrition, activity, sleep, health and beauty, and mindfulness)
Sršen believes there is untapped potential with Bellabeat and by analyzing smart device fitness data, better business and marketing decisions can be made.  She asks the marketing analytics team to determine how consumers use their smart devices based on the data, then apply the findings to a Bellabeat product. 
## Ask
### Business Task
The business task is to analyze consumer smart device data and apply such findings to the Bellabeat ‘Time’ smartwatch.  These insights will guide stakeholders in their quest of creating smart devices that cater to the needs of their customers.
### Stakeholders
The key stakeholders are Bellabeat’s cofounders Urška Sršen (Chief Creative Officer) and Sando Mur (Mathematician).  The Bellabeat marketing analytics team makes up the secondary stakeholders.
## Prepare
### Data Sources
The data comes from thirty Fitbit users who consented to share personal information like the output of physical activity, heart rate, steps, and sleep monitoring.  The dataset is separated into 18 .csv files.
### ROCCC Analysis
Reliable - Low, a sample size of 30 is small and could be misleading.
Original - Low, originally collected by Amazon Mechanical Turk and distributed by a third party. 
Comprehensive - Low, the demographics of participants are missing.  Information like gender, age, health, etc.  Data could not be randomized, leading to further bias.
Current - Medium, this data is from 2016.  Smartwatch technology and subsequent consumer behavior may not be representative of today. 
Cited - Unknown, there is skepticism about the credibility of the Amazon Mechanical Turk source.
## Process
### Tools
Google Sheets, Google BigQuery, RStudio Cloud, Tableau
### Data Cleaning
In BigQuery, the number of unique ‘Id’ values in each spreadsheet was counted, dailyActivity_merged (33), sleepDay_merged (24), and weightLogInfo_merged (8).  The syntax is as follows:

![file1](https://github.com/seanh824/BellabeatProject/assets/140123586/3adce867-0862-4806-9980-098762dd3840)

Then, using Google Sheets, each unique ‘Id’ was conditional formatted in order to color code every row like such:

![file2](https://github.com/seanh824/BellabeatProject/assets/140123586/96cab103-c84f-44f0-a3de-402a71b06eca)

In RStudio Cloud, the “tidyverse” “ggplot2” and “dplyr” packages were installed and the following data was imported:

![image](https://github.com/seanh824/BellabeatProject/assets/140123586/ed908c51-7523-407a-91da-65799535b034)

Data cleaning in RStudio Cloud began with the clean function.  Every row that contained missing values was removed.  The following syntax was applied to 2 of the datasets.  The weight log dataset contained a column with only two values, so that row, ‘Fat’, was removed:

<img width="328" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/c530b87f-c821-448f-b7ff-f7ee591af6a2">

The unique function, which was applied to all 3 datasets, was used to eliminate any duplicate value or row:

<img width="325" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/98b1d6fd-e89b-4934-b190-49244a2d3d8f">

## Analyze
To get an initial understanding of the datasets, the summary function was used.
### Average Weight (lbs)

<img width="303" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/08761e9f-47c1-4429-8175-68056148fa14">

<img width="295" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/d24eed13-d6e2-4a9e-b73e-87b8f204ac62">

As confirmed from early data cleaning, only 8 participants submitted weight logs.  On top of that, 5 of the 8 participants submitted only 1 or 2 weight entries.![image](https://github.com/seanh824/BellabeatProject/assets/140123586/87ad7624-6903-4df9-bf77-48efdfeafb44)

### Total Steps

<img width="276" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/ea2b4bd8-c6ba-4b21-9bb5-45e0819d5d0d">

Typically, a healthy adult should aim for approximately 10,000 steps per day.  However, the average number of steps in this dataset is 7,638.  1 in 4 participants averaged 3,790 steps or less per day, significantly lower than the recommended 10,000 steps.

### Calories

<img width="267" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/b1352aad-80ff-4829-b4d2-d10f16443786">

The average number of calories burned per day for all participants is 2,304.  This is more than the suggested amount of calories for women (~2,000) but slightly behind the number of calories men should burn daily (~2,700).  Unfortunately, there are many limitations of this dataset, this being one of them.
### Very Active Minutes

<img width="276" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/08209cd2-e160-48f3-a978-33e9fd15f2ce">

Half of all participants averaged 4 daily ‘very active minutes’, quite below the recommended 30 minutes of activity per day.
### Very Active Minutes vs Calories Burned
To produce a scatterplot with the ‘very active minutes' data to calories burned, the following code was entered:

<img width="468" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/5c7a67f4-9bda-471c-93c6-184375578669">

<img width="357" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/61e1ab73-8b66-481d-89e0-8eed73056dd4">

The scatterplot illustrates a direct relationship between active minutes and calories burned.  It also points to the fact that most data in the ‘very active minutes’ axis is near or at zero, which confirms an earlier summary table.
### Total Steps vs Calories Burned

<img width="468" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/de540db7-1a3d-490f-9597-db5c427a23b4">

<img width="446" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/e1e97d38-1264-469d-a546-e63bedbebc30">

Again, we see a direct relationship between total steps and calories burned.
### Sedentary Minutes vs Calories Burned

<img width="468" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/d8c958c4-44b5-462e-94ea-b7a0a8ee6099">

<img width="468" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/3c05039f-bb7a-4df2-9f56-c396f7284ae5">


























