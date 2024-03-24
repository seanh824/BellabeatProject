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

<img width="336" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/357cbf26-e010-4af3-b9e7-f3f9074df937">

Data cleaning in RStudio Cloud began with the clean function.  Every row that contained missing values was removed.  The following syntax was applied to 2 of the datasets.  The weight log dataset contained a column with only two values, so that row, ‘Fat’, was removed:

<img width="328" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/c530b87f-c821-448f-b7ff-f7ee591af6a2">

The unique function, which was applied to all 3 datasets, was used to eliminate any duplicate value or row:

<img width="325" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/98b1d6fd-e89b-4934-b190-49244a2d3d8f">

## Analyze
To get an initial understanding of the datasets, the summary function was used.
### Average Weight (lbs)

<img width="303" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/08761e9f-47c1-4429-8175-68056148fa14">

<img width="295" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/d24eed13-d6e2-4a9e-b73e-87b8f204ac62">

As confirmed from early data cleaning, only 8 participants submitted weight logs.  On top of that, 5 of the 8 participants submitted only 1 or 2 weight entries.
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

The resulting scatterplot shows an indirect relationship but is less pronounced than the direct relationships from the graphs above.  This suggests that calories can still be burned even with large amounts of one’s inactive days.
### Very Active Minutes vs Weight (lbs)
A violin plot was created to illustrate which weight groups are most active:

<img width="468" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/b5c1f9ee-2f75-41d8-ae2b-61832e72baee">

<img width="448" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/cd79f69f-291f-4dc0-b078-00682f98b2f2">

<img width="468" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/a4318c6c-71b3-472b-8a1a-458c23d75242">

Participants between 125 to 175 pounds were the most active.
## Share
### Activity Level Pie Chart
A pie chart was generated using Tableau, illustrating the distribution of activity levels. Among all individuals, a striking 81% of daily time was found to be inactive, with the remaining 19% allocated to different levels of activity. Remarkably, more than 97% of the day was characterized by either light activity or complete inactivity. To put it into perspective, 2.86% of a day translates to approximately 40 minutes of engaging in high-intensity or fairly high-intensity activities.

<img width="293" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/6b5820d8-4267-4269-a435-1339b2548489">

<img width="468" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/f9fd36fb-da5b-464d-a2ff-228c12d10c09">

### Average Hours of Sleep by Day
The ‘SleepDay’ column contained both the date and time, ‘sleep_day’ was created, separating the date from the time:

<img width="468" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/8ac4bee0-a8a5-4da9-b624-84ed72df145a">

The ‘TotalMinutesAsleep’ column was converted into hours in a new column called ‘TotalHoursAsleep’:

<img width="457" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/f66838bc-7dd4-4973-afb4-ea1aef9c7318">

Then, the column, ‘sleep_day’, was formatted as a date:

<img width="468" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/3c9cc816-a3eb-4c99-8e79-5b00c32299ce">

A new column, ‘day_of_week’, transformed the dates from ‘sleep_day’ to days of the week:

<img width="468" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/3d145e8d-4e09-4fec-95e0-b125830ec7f3">

The average amount of sleep in hours for each day of the week was calculated, yielding this bar graph:

<img width="468" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/4385bdde-c7b1-4398-a9b8-a19ca21dc801">

<img width="468" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/a2eb212d-2b17-4078-baa5-3b6dd798256f">

I was expecting significantly more sleep on Friday and Saturday compared to the middle of the work week, but that is evidently not the case.  In fact, you'll find almost no differences when comparing the amount of sleep on Monday to Saturday and Tuesday to Friday.  More context could be given if the data specified the time at which each sleep log began or ended.  The fact that a sample of 24 participants slept nearly the same amount regardless of the day of the week suggests that parts of life, like work or going out on the weekends, did not impact sleep length. Presumably, the body has an internal clock; going to bed earlier, like during the work week, equates to waking up earlier.  Similarly, going to bed later, like during the weekend, equates to waking up proportionally later.
### Activity Level & Burned Calories by Day
To examine how burned calories and activity level change based on the day of the week, the syntaxes below were respectively entered:

<img width="468" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/8ac85a4e-a912-4452-94d3-132350d022a0">

<img width="468" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/955f96a4-4e0a-4dac-a0ee-609f87c622fe">

Both tables produced were imported to Tableau to create a combination chart.

<img width="468" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/70e9e800-c967-45cb-8df4-32322bae602a">

There is a clear relationship between calories burned and activity level.  When activity level suffers, so does the amount of calories burned.
### Average Steps by Day
The average number of steps taken per weekday was calculated with this syntax:

<img width="468" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/5ae61814-0371-4d46-8836-8b05ebcd666f">

Tableau summarized that data with a bar graph:

<img width="310" alt="image" src="https://github.com/seanh824/BellabeatProject/assets/140123586/0323ebfa-8dac-466e-8923-536105548ff4">

This graph is consistent with the combination chart from above and the idea that activity is cyclical - steps peak early in the work week, before dropping from Wednesday to Friday, and then going back up on Saturday.  Sunday, often referred to as a day of rest, averaged the least amount of steps.
## Act
Bellabeat’s founders, Urška Sršen and Sando Mur, knew the company was capable of more, so they looked toward the power of data and the insights it could bring.  Analyzing data about similar products on the market ultimately facilitated recommendations for future Bellabeat products and their subsequent marketing strategies.
The business task was to apply the findings of the data analysis to a single Bellabeat product.  Bellabeat offers a multitude of products but one of the most essential parts of all of them is the Bellabeat App.  Without a well-designed app, all of Bellabeat’s products are inherently less insightful, which is ultimately why my recommendations are specific to the Bellabeat App.
Providing consumers with useful app features will immediately improve a range of Bellabeat products.  Consumers in this market may vary in their pursuit of physical fitness, which is why Bellabeat+ should exist.  Bellabeat+, $8.99/month, is geared towards very active consumers who want to optimize their current health standards: sleep, diet, and activity level.  Bellabeat+ is powered by an ai assistant - Bellabot, which gives the app character and performs quintessential parts of the premium subscription.  On the other hand, the free version of the Bellabeat App is designed for consumers looking to become more physically active.
### Bellabeat+
Sleep Tracking
●	Bellabot will learn how long you sleep and what time you typically wake up on specific days. It will notify you what time to be asleep to achieve what your body considers healthy sleep.  Bellabot will also notify you about any trends in your sleep, including failure to meet healthy sleep standards.
Nutrition Tracking
●	Bellabeat+ allows users to input all of the foods and drinks they consume either via search or barcode scan.  Simply scan the food or drink packaging you consume and all major nutritional facts will automatically be counted towards your daily total.  If your food or drink has no barcode, you can search for the item in the food/drink database.   Bellabot will recommend daily caloric, protein, fat, and carbohydrate intake based on your current weight and targeted weight.  Bellabot also suggests an appropriate target date for meeting said desired weight, encouraging healthy eating habits and sustainable weight changes.
Cardio Progression System
●	Users will be prompted to enter how many times a week they aim to run. Next, they’ll enter their current run distance and time and set a run distance and time goal.  The goal also comes with a deadline decided by the user themselves or Bellabot can recommend a healthy goal deadline.  By tracking runs with a Bellabeat smartwatch, Bellabot will let users know how they are progressing toward their running goals.
Weight Lifting Progression System
●	Bellabeat+ members will be prompted to enter their weekly workout plan by selecting exercises from a database.  They also have the option to let Bellabot generate a workout plan.  After, they’ll enter their current reps and weight of any workout they want to track.  Then, a reps and weight goal for said workouts will be set along with a deadline for achieving the goal.  Again, Bellabot will recommend a healthy target date, which helps prevent overexertion.  How frequently a user must update their current exercise reps and weight is dependent on when their goal deadline is.
### The Free Version of the Bellabeat App
There are a few big differences between the free version of the Bellabeat App and Bellabeat+.  First, smart bedtime notifications are not included and users can only view their last week of sleep logs.  Second, in regard to nutrition tracking, there is no barcode tracking in the free version of the Bellabeat App.  Lastly, the Cardio & Weight Lifting Progression System is exclusive to Bellabeat+, but purchasing a Bellabeat product comes with a 3-month free trial.
## References
Edward R. Laskowski, M. D. (2023, July 26). How much exercise do you really need?. Mayo Clinic. https://www.mayoclinic.org/healthy-lifestyle/fitness/expert-answers/exercise/faq-20057916#:~:text=As%20a%20general%20goal%2C%20aim,sitting%20time%20is%20important%2C%20too.
MediLexicon International. (n.d.-a). Average steps per day by age, sex, and occupation. Medical News Today. https://www.medicalnewstoday.com/articles/average-steps-per-day#summary
MediLexicon International. (n.d.-b). Calories burned in a day: Calculation, factors, exercise, weight loss. Medical News Today. https://www.medicalnewstoday.com/articles/319731











































































