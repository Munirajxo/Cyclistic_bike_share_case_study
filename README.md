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

#### About the company

In 2016, Cyclistic launched a successful bike-share oering. Since then, the program has grown to a fleet of 5,824 bicycles that are geotracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime. Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members. Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. Although the pricing flexibility helps Cyclistic attract more customers, The director of marketing believes that maximizing the number of annual members will be key to future growth. Rather than creating a marketing campaign that targets all-new customers, she believes there is a very good chance to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs.

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

Since Cyclistic is a fictional company, I will use Divvy’s, a bike-share program based in Chicago, data from May 2022 – April 2023 to complete this case study. To download the data, [please use this link](#https://www.kaggle.com/datasets/munirajmallesan/cyclistic-bike-share-analysis). This data was made public by Motivate International Inc, under this license. Due to data privacy issues, personal information has been removed or encrypted.

add Codeadd Markdown
### Data Cleaning
---
In the initial preparation phase, We performed following tasks:
1. Build and connected a database.
2. Cleand and organized data using sql queries .
3. Data cleaning and formatting.
   
### Explotary Data Analysis 
---
EDA involved exploring the data to answer questions such as:
- Finding the healthiest employees for bonus?
- Wage increase for the non-smokers?
- Finding the reason for absenteeism?

### Data Analysis 
---
```
--Create a join table
use work
select * From Absenteeism_at_work a
left join compensation b
on a. ID = b. ID 
left join Reasons r on
a. Reason_for_absence = r.Number ;

--- find the healthiest Employees for the bonus 
select * From Absenteeism_at_work
where Social_drinker = 0 and Social_smoker = 0 
and Body_mass_index <25 and
Absenteeism_time_in_hours < (select AVG (Absenteeism_time_in_hours) from Absenteeism_at_work)

--- compansation rate increase for non-smoker / budget $ 983,221 do .68 increase per hour / $1414.4 increase per year 
select count(*) as nonsmookers from Absenteeism_at_work
where Social_smoker = 0;

--Optimize this query 
select 
a . ID,
r. Reason,
Month_of_absence,
Body_mass_index,
CASE WHEN Body_mass_index < 18.5 then 'UnderWeight'
     WHEN Body_mass_index between 18.5 and 25 then 'HealthyWeight'
     WHEN Body_mass_index between 25 and 30 then 'OverWeight'
     WHEN Body_mass_index > 30 then 'Obese'
	 ELSE 'Unknown' end as BMI_Category,
CASE WHEN Month_of_absence IN (12,1,2) then 'Winter'
     WHEN Month_of_absence IN (3,4,5) then 'Spring'
     WHEN Month_of_absence IN (6,7,8) then 'Summer'
     WHEN Month_of_absence IN (9,10,11) then 'Fall'
		  ELSE 'Unkown' END as Season_Names,
		  Seasons,
		  Month_of_absence,
		  Day_of_the_week,
		  Transportation_expense,
		  Education,
		  Son,
		  Social_drinker,
		  Social_smoker,
		  Pet,
		  Disciplinary_failure,
		  Age,
		  Work_load_Average_day,
		  Absenteeism_time_in_hours
From Absenteeism_at_work a
left join compensation b
on a.ID = b.ID 
left join Reasons r on
a. Reason_for_absence = r.Number ;
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
