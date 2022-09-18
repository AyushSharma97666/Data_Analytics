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
- saved all last 12 months data in one csv file 


## Analyze

for starting analysics we have some question to start 
1. Percentage of annual and non annual user of cyclistic
2. Quarterly growth in user 
3. Number of user by day of week 
4. Average trip 

The final_year.csv size is more than 100MB so we are useing BigQuery for analysics.
1. Percentage of annual and non annual user of cyclistic  
select   
usertype,  
round(count(*) *100/ (select   
count(*)  
from lithe-vector-361209.case_study_1.prepare), 0) as per  
from lithe-vector-361209.case_study_1.prepare  
group by usertype  


![image](https://user-images.githubusercontent.com/110818513/190449828-2a6e927c-7072-4521-9e1b-1757360e7a57.png)


Now we know that there 23% of user are not useing annual subscription. we know that annual subscription is more profitable than daily or one time pass. we have to convert these 23% user into annual subscribe.

2. Quarterly growth in user
 
To get last year user growth on quarterly basic we use below query     
SELECT    
 extract(quarter FROM date) as quarter,   
 count(*) as count  
FROM lithe-vector-361209.case_study_1.prepare    
group by quarter  
order by quarter   

![image](https://user-images.githubusercontent.com/110818513/190447003-98fd571b-2bac-4c7b-a56e-e627a00158ed.png)

there is good growth in number of user before 4th quarter then in 4th sudden fall is there 
![image](https://user-images.githubusercontent.com/110818513/190449382-cfc852aa-f733-479f-ae98-215fda320f80.png)  

3. Number of user by day of week
Now we are looking number of user on different day of weeek for these we used below query   
select   
  day_of_week ,  
  count(*) as count  
from lithe-vector-361209.case_study_1.prepare   
group by day_of_week   
order by day_of_week  

![image](https://user-images.githubusercontent.com/110818513/190451803-63b3b418-201a-4fa6-8d72-982d005e88e2.png)

Note 0= monday and 6 = sunday 

Now we are useing where cause to get more data inside on above query 
firstly we are useing for annual subscriber, then on non subscriber

![image](https://user-images.githubusercontent.com/110818513/190454394-5e92dd23-a646-4768-b912-71fbd45be616.png)
![image](https://user-images.githubusercontent.com/110818513/190454463-77067566-cd67-4c69-a13c-0eedc548c05d.png)

4. Average trip 
for these we used below query   
select  
 usertype,   
 avg(time_diff) as avg
from  lithe-vector-361209.case_study_1.prepare 
group by  usertype
order by avg 

![image](https://user-images.githubusercontent.com/110818513/190456758-85d99dfb-fbca-4a79-8448-5fced461cab1.png)


In these we have used exceel for creating visualtion, after running query in BigQuery we getting result in csv files. It was easy and fast to use exceel for small data visualtion. you can also use r, power BI , tableau,etc for big data sizes.


## Share 
After looking into data we get following insides
- Quarterly growth was reduced in 4th quarter and growh of annual and non annual subscriber are also have same effect.
- Annual subscriber are useing on weekdays and non annual subscriber are on weekends
- Non Annual subscriber are have more trip than annual subscriber it was 3 time more than annual 

##  Act

**Recommendations Based on Analysis**
- Saturday and Sunday should be prioritised when it comes to scheduling ads for the digital online campaign.
- Last quarter shows downward move in use of cyclistics, so we should use more marketing in that quarter.
- Giving time limit on use of bikies to Non annual subscriber and no limit to annual subscriber reason is that instead of taking one day pass they will take annual subscription

Thank you very much for your time, I hope you enjoyed the reading

I would be very happy to read your comments and feedback
