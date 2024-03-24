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


