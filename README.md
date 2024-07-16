# Cyclistic_bike_share_case_study

## case study:How Does a Bike-Share Navigate Speedy Success?

## Table of Contents 
- [Background](#background)
- [Ask](#ask)
- [Prepare](#prepare)
- [Process](#process)
- [Analyze](#analyze)
- [Share](#share)
- [Results](#results)
- [Recommendations](#recommendations)
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
### Analyze
---



```


```
- Findings:

1. While Casual rider has slightly longer distance trip on weekday, membership ride's slighly longer over weekend.
2. All users take slightly longer distance trip in Spring
3. While 6% of casual riders return their bike to their start point station, 4% of membership rider returns at their start point station.

### Share
---
```

```
- Joined Tables: Combined Absenteeism,Reasons, and Compensation tables using SQL joins.
- Aggregate Functions: Calculated average wage increases with functions like AVG.
- CASE Functions: Categorized data using CASE statements to identify healthy non-smoking individuals.
- Data Filtering: Applied filters to isolate data for healthy non-smokers.
- Query Optimization: Enhanced performance by indexing and selecting relevant columns.
- Power BI Integration: Connected the optimized SQL query to Power BI to visualize outcomes and insights.
  Including sql queries that i worked



### Results
---
- Compensation Increase: The compensation rate increased by $0.68 per hour, amounting to $1,414.40 increase per year for non-smokers, within a budget of $983,221.
- Highest Absenteeism: 3 individuals had the highest absenteeism rates.
- Weekly Absenteeism: Across all 5 days of the week, the sum of absenteeism time in hours ranged from 553 to 1489.
- Percentage Contribution: The 3 individuals accounted for 14.93% of the total absenteeism time in hours.
- Monthly and Weekly Analysis: Analyzed absenteeism by month and by day of the week.
- Reasons for Absenteeism: Identified reasons for taking leave.


### Recommendations
---
- Focus on high absenteeism individuals with personalized wellness programs.
- Adjust wage increases based on performance and health metrics.
- Investigate and address the causes of high absenteeism on specific days and months.
- Consider flexible scheduling or remote work options to reduce absenteeism.
- Implement flexible work policies to accommodate employee needs.
