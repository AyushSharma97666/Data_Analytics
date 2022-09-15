# Data_Analytics
Google Data Analytics Certificate Case Study 


## Case Study: How Does a Bike-Share Navigate Speedy Success?

**Introduction:**

Welcome to the Cyclistic bike-share analysis case study!
This case study represents course 8 “Capstone project” of the Google Data Analytics Professional Certificate on Coursera

**The Scenario:**

Cyclistic is a fictional bike-share company in Chicago. The director of marketing believes the company’s future success depends on maximising the number of annual memberships. Therefore, the data analytics team wants to understand how casual riders and annual members use Cyclistic bikes differently. From these insights, the team will design a new marketing strategy to convert casual riders into annual members.

**About the company:**

In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown to a fleet of 5,824 bicycles that are geotracked and locked into a network of 692 stations across Chicago. Cyclistic has flexible pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members.

### Ask

Moreno, the director of marketing, has set a clear goal: Design marketing strategies aimed at converting casual riders into annual members.

There are three questions that will guide the future marketing program:
1. How do annual members and casual riders use Cyclistic bikes differently?
2. Why would casual riders buy Cyclistic annual memberships?
3. How can Cyclistic use digital media to influence casual riders to become members?

Moreno has assigned me the first question to answer: How do annual members and casual riders use Cyclistic bikes differently?

**The business task:**      
Analyse the Cyclistic data set for the year 2020 to understand how annual members and casual riders use Cyclistic bikes differently.

**Stakeholders:**

Lily Moreno: The director of marketing. Moreno is responsible for the development of campaigns and initiatives to promote the bike-share program.     
Cyclistic marketing analytics team: A team of data analysts who are responsible for collecting, analysing, and reporting data that helps guide Cyclistic marketing strategy.     
Cyclistic executive team: The executive team will decide whether to approve the recommended marketing program.


**Deliverables:**

- A description of all data sources used
- Documentation of any cleaning or manipulation of data
- A summary of the analysis
- Supporting visualisations and key findings
- Top three to four recommendations based on the analysis

### Prepare 

**1. A description of all data sources used**    
Cyclistic’s historical trip data to analyze and identify trends. [Download the previous 12 months of Cyclistic trip data
here.](https://divvy-tripdata.s3.amazonaws.com/index.html) (Note: The datasets have a different name because Cyclistic is a fictional company. For the purposes of this case study,
the datasets are appropriate and will enable you to answer the business questions. The data has been made available by
Motivate International Inc. under this [license](https://ride.divvybikes.com/data-license-agreement).) This is public data that you can use to explore how different customer types are
using Cyclistic bikes. But note that data-privacy issues prohibit you from using riders’ personally identifiable information. This
means that you won’t be able to connect pass purchases to credit card numbers to determine if casual riders live in the
Cyclistic service area or if they have purchased multiple single passes.

**2. Documentation of any cleaning or manipulation of data**   
Cleaning and ensuring data quality is a vital part of the data analytics process.

There are 4 csv file have last 12 months data in 12 columns and in quarterly formate 
1. Divvy_Trips_2019_Q2.csv (2019_Q1)
2. Divvy_Trips_2019_Q3.csv (2019_Q2)
3. Divvy_Trips_2019_Q4.csv (2019_Q3)
4. Divvy_Trips_2020_Q1.csv (2020_Q1)

There are 12 columns  2019_Q2, 2019_Q3 have  following columns :-
1. trip_id (int64)
2. start_time (object)
3. end_time (object)
4. bikeid (int64)
5. tripduration (object)
6. from_station_id (int64)
7. from_station_name (object)
8. to_station_id (int64)
9. to_station_name (object)
10. usertype (object)
11. gender (object)
12. birthyear (float64)

Ther are 12 columns 2019_Q4 have following columns:- 
1.  01 - Rental Details Rental ID (int64)
2. 01 - Rental Details Local Start Time (object)
3. 01 - Rental Details Local End Time (object)
4. 01 - Rental Details Bike ID (int64)
5. 01 - Rental Details Duration In Seconds Uncapped (object)
6. 03 - Rental Start Station ID (int64)
7. 03 - Rental Start Station Name (object)
8. 02 - Rental End Station ID (int64)
9.  02 - Rental End Station Name (object)
10. User Type (object)
11. Member Gender (object)
12. 05 - Member Details Member Birthday Year (float64)

There are 12 columns 2020_Q1 have folllowing columns:-
 1. ride_id (object)
 2. rideable_type (object)
 3. started_at (object)
 4. ended_at (object)
 5. start_station_id (int64)
 6. start_station_name (object)
 7. end_station_id (int64)
 8. end_station_name (object)
 9. start_lat (float64)
 10. start_lng (float64)
 11. end_lat (float64)
 12. end_lng (float64)
 13. member_casual (object)


For Cleaning, I used Microsoft Excel.
Used filter function from Exceel to get bird eye of data from all files. According to data we do following steps were taken:
- I checked for and removed duplicate
- I made sure there are no extra unneeded spaces. For this I used the TRIM function on trip_id , ride_id  column. 
- I also used the TRIM and PROPER functions on both start_station_name and end_station_name to ensure proper unified text formatting: TRIM(PROPER(F2)) in all four files 
- According filter, there are start_time, 01 - Rental Details Local Start Time, started_at and end_time,01 - Rental Details Local End Time,  ended_at columns have the same timestamp format: ‘dd-mm-yyyy hh:mm:ss’ in all files.

Next for merging all files I used python, CSV files have  large data size. It was easy and fast with python. 
Python script is at the [link](https://github.com/AyushSharma97666/python_1/blob/main/python.py)

- imported 2019_Q2, 2019_Q3 and 2019_Q4 csv files into dataframe 
- renamed 2019_Q4 dataframe, all the 3 datafranme have 12 columns and same datatype but name is different in 2019_Q4 
- some columns are only in these 3 files but not in 2020_Q1 so removed those columns such as bikeid.  gender , birthyear, tripduration 
- concated these 3 dataframe into one 
- imported 2020_Q1 files and some columns are different than concated dataframe, so droped those columns 
- concated these 2020_Q1 with previous dataframe 
- created new column with trip_time from start and end time 
- created new column with day of week from star_time column 


## An
