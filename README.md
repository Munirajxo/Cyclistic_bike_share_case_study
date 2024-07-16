# Cyclistic_bike_share_case_study

## case study:How Does a Bike-Share Navigate Speedy Success?

## Table of Contents 
- [Background](#background)
- [Ask](#ask)
- [Prepare](#prepare)
- [Process](#process)
- [Analyze](#analyze)
- [Share](#share)
- [Conclusion](#conclusion)
## Background
---
In this case study, I am going to follow "The APPASA process" (Ask - Prepare - Process - Analyze - Share - Act) to complete the assignment.

### Scenario

I am a junior data analyst working in the marketing analyst team at Cyclistic, a bike-share company in Chicago. The director of marketing believes the company’s future success depends on maximizing the number of annual memberships. Therefore, my team wants to understand how casual riders and annual members use Cyclistic bikes differently. From these insights, my team will design a new marketing strategy to convert casual riders into annual members.

### The goal of this case study
Three questions will guide the future marketing program:
1. How do annual members and casual riders use Cyclistic bikes differently?
2. Why would casual riders buy Cyclistic annual memberships?
3. How can Cyclistic use digital media to influence casual riders to become members?
The director of marketing has assigned me the first question to answer: How do annual members and casual riders use Cyclistic bikes differently?

In this assignment, I will produce a report with the following deliverables:
1. A clear statement of the business task
2. A description of all data sources used
3. Documentation of any cleaning or manipulation of data
4. A summary of my analysis
5. Supporting visualizations and key findings

### Ask
---
1. Business Task In order to maximize the number of annual membership, I, data analyst, will find trend and patterns among casual riders and membership riders, and identify potential riders who can get benefit from annual membership. I do not need to raise awareness of annual membership among casual riders as they are already aware of the program.
2. Stakeholders
- The director of marketing
- The marketing analysis team
- Cyclistic's Executive team
3. Stakeholder's expectation Design marketing strategies aimed at converting casual riders into annual members. In order to do that, however, the marketing analyst team needs to better understand how annual members and casual riders differ, why casual riders would buy a membership, and how digital media could affect their marketing tactics. The marketing team is interested in analyzing the Cyclistic historical bike trip data to identify trends. 
### Prepare
---
- DATA TYPE check
- ROOOC Check
- Sampling bias
- Observer bias
- Interpretation bias
- Confirmation bias

#### About the data set:

Since Cyclistic is a fictional company, I will use Divvy’s, a bike-share program based in Chicago, data from May 2022 – April 2023 to complete this case study. To download the data, [https://www.kaggle.com/datasets/munirajmallesan/cyclistic-bike-share-analysis](#https://www.kaggle.com/datasets/munirajmallesan/cyclistic-bike-share-analysis). This data was made public by Motivate International Inc, under this license. Due to data privacy issues, personal information has been removed or encrypted.
```
library(tidyverse)  #helps wrangle data
library(lubridate)  #helps wrangle date attributes
library(ggplot2)  #helps visualize data
library(dplyr) #helps clean data
library(tidyr) #helps clean data
library(geosphere)
# Read the trip data from 202205 - 202304 (12 months)
tripdata_2022_05 <- read.csv("/kaggle/input/cyclistic-bike-share-analysis/202205-divvy-tripdata_1.csv")
tripdata_2022_06 <- read.csv("/kaggle/input/cyclistic-bike-share-analysis/202206-divvy-tripdata_2.csv")
tripdata_2022_07 <- read.csv("/kaggle/input/cyclistic-bike-share-analysis/202207-divvy-tripdata_3.csv")
tripdata_2022_08 <- read.csv("/kaggle/input/cyclistic-bike-share-analysis/202208-divvy-tripdata_4.csv")
tripdata_2022_09 <- read.csv("/kaggle/input/cyclistic-bike-share-analysis/202209-divvy-publictripdata_5.csv")
tripdata_2022_10 <- read.csv("/kaggle/input/cyclistic-bike-share-analysis/202210-divvy-tripdata_6.csv")
tripdata_2022_11 <- read.csv("/kaggle/input/cyclistic-bike-share-analysis/202211-divvy-tripdata_7.csv")
tripdata_2022_12 <- read.csv("/kaggle/input/cyclistic-bike-share-analysis/202212-divvy-tripdata_8.csv")
tripdata_2023_01 <- read.csv("/kaggle/input/cyclistic-bike-share-analysis/202301-divvy-tripdata_9.csv")
tripdata_2023_02 <- read.csv("/kaggle/input/cyclistic-bike-share-analysis/202302-divvy-tripdata_10.csv")
tripdata_2023_03 <- read.csv("/kaggle/input/cyclistic-bike-share-analysis/202303-divvy-tripdata_11.csv")
tripdata_2023_04 <- read.csv("/kaggle/input/cyclistic-bike-share-analysis/202304-divvy-tripdata_12.csv")

#Combine all the data sets
all_trips <- bind_rows(tripdata_2022_05, tripdata_2022_06, tripdata_2022_07, tripdata_2022_08, tripdata_2022_09, tripdata_2022_10, tripdata_2022_11, tripdata_2022_12, tripdata_2023_01, tripdata_2023_02, tripdata_2023_03, tripdata_2023_04)
```
### Process
---
Data Cleaning before conducting analysis
Due to the large data set, I will use R for data cleaning and data analysis.
```
colnames(all_trips)  #List of column names
nrow(all_trips)  #How many rows are in data frame?
dim(all_trips)  #Dimensions of the data frame?

Remove bad data
1. Remove ride length is less than 0 second and is > 1440 minutes as ride length shouldn't be either negative or more than one day
 # Remove "bad" data
# The dataframe includes a few hundred entries when bikes were taken out of docks and checked for quality by Divvy or ride_length was negative
#Create a new data frame without records that have ride length <= zero minute OR > 1440 minutes
all_trips_v2 <- all_trips[!(all_trips$ride_length <= 0 | all_trips$ride_length > 1440),]
summary(all_trips_v3)
```
![Summary_v3](https://github.com/user-attachments/assets/9ca83eb3-7059-46e7-bead-f1e8fe0d3cee)

### Analyze
No_of_rides_monthwise
![monthly_rides](https://github.com/user-attachments/assets/7b986098-ecf8-49e4-8627-68a242bfe144)
member_casual_rides
![member_casual_rides](https://github.com/user-attachments/assets/d0fbe704-f7d4-41fa-97b5-48891484dec2)

Findings:
1. Membership rider's trip is longer than casual ones regardless of the season or day
2. All users take longer trips over weekend and summer
3. While 6% of casual riders return their bike to their start point station,
4. 4% of membership rider returns at their start point station.

### Share
---
Members vs Casual 
1. Ridedistance and count
![ride_dis and count](https://github.com/user-attachments/assets/0c452c34-0ee9-476b-ad71-b3d3ba42e4c0)
2. Weekly ride_distance
![avg_ride_distance_week](https://github.com/user-attachments/assets/12d878a1-9bea-4d05-b7bd-2dc1b269e358)
3. Monthly ride distance
![avg_ride_dis_month](https://github.com/user-attachments/assets/6f1c4706-0c6e-49b9-8129-79ae2d6b4f84)

- It seems that the casual users travel the same average distance than the member users, but they have relatively longer rides, that would indicate a more leisure oriented usage vs a more "public transport" or pragmatic use of the bikes by the annual members.
-  Casual riders are more likely to return their bikes at the same station.
- Additionaly, while that membership riders are more active on weekday, casual riders use the service more often over weekend. It lead me to conclude that membership riders use this service for their commute while casual rider use it for fun.

### Conclusion
---
1. The Casual users have leisure, and tourism rides mostly on weekends.
2. The Annual users have commute or pragmatic rides during weekdays.

