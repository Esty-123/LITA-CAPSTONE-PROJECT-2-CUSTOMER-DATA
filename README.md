### LITA-Capstone Project Two Documentation 

### Project Title:Customer Segmentation for Subscription Service

[Project Overview](project-overview)

Data Source

Tools Used

Data Cleaning and Preparation

Exploratory Data Analysis

[Data Analysis](data-analysis)

Data Visualization

### Project Overview

This project aims to implement customer segmentation for a subscription-based service to better understand and cater to different customer groups. By analyzing customer data, the project will divide the customer base into distinct segments based on their behaviors, preferences, and usage patterns. The goal is to identify key characteristics of each segment to inform targeted marketing strategies, enhance customer retention, and personalize offerings.

### Data Source
This is the primary source of data used here is Customer Data. xlsx and  this is an open data that can be freely downloaded online such as Kaggle or FRED or any other resprespostry site. 

### Tools Used
- Microsoft Excel
1. For Data cleaning
3. For Anaysis
4. For Data Visualization
- SQL-Structured Query Language for Querying Data.
- GitHub for Portfolio building
- Data Visualizatio(Power Business Intelligence)
  
### Data Cleaning and Preparation

This process focuses on preparing the dataset for analysis by identifying and rectifying inaccuracies, inconsistencies, and errors. Key steps include:

1. Handling Missing Values: Identifying and addressing missing data through removal or imputation.

2. Removing Duplicates: Ensuring that each record is unique by eliminating duplicate entries.

3. Correcting Errors: Fixing typographical errors, formatting issues, and out-of-range values.

4. Filtering Outliers: Identifying and deciding how to manage outliers that may skew results.

5. Data Transformation: Converting data types and normalizing values as needed.

### Exploratory Data Analysis
Its involves the exploring of data to answer some question such as
- What  is the overall customer Behaviour ? 
- which customer ID has the highest Subcription type?
- What is the average subscription duraion.
  
### Data Analysis
---
This is where we conclude some basic lines of type codes, Queries or even DAX expressions use during the analysis

```` SQL
CREATE DATABASE LITA_CAPSTONE_PROJECT_2_DB

select * from[dbo].[CUSTOMER DATA 1]

.....1 Retrieve the total number of customers from each region.
Select Region,count(DISTINCT CustomerID) as Total_customers
from[dbo].[CUSTOMER DATA 1]
group by Region;


.... 2 The most popular subscription type by the number of customers...
Select top 1 subscriptiontype,
count(distinct CustomerID)as Total_customers
from[dbo].[CUSTOMER DATA 1]
group by subscriptiontype
Order by Total_customers desc


  ...... 3 find customers who canceled their subscription within 6 months....
  Select'Customer'IDS
  from [dbo].[CUSTOMER DATA 1]
  Where (DATEDIFF(DAY,subscriptionstart,subscriptionend))<=6;

   ......4 calculate the average subscription duration for all customers.
   Select AVG(DATEDIFF(day,subscriptionstart,subscriptionend))as AVG_subscription_duration
   FROM [dbo].[CUSTOMER DATA 1]


  ...... 5 find customers with subscriptions longer than 12 months.
  select 
  CustomerID,
  customer_Name,
  Subscription_start_date,
  Subscription_end_date
  from
  [dbo].[CUSTOMER DATA 1]
  WHERE
  DATEDIFF(MONTH,subscriptionstartdate,subscriptionenddate)>12;--
  'Adjust'- based on SQl dialect

  from[dbo].[CUSTOMER DATA 1]
   Where DATEDIFF(MONTH,subscriptionstartdate,subscriptionenddate)>12;

   ...... 6 calculate total revenue by subscription type.
   select subscriptiontype,
   SUM(revenue)as total_revenue 
   from[dbo].[CUSTOMER DATA 1]
   group by 
   SubscriptionType;

  ......7 find the top 3 regions by subscription cancellations..
  select top 3 region,
  count(*)as Subscriptionend_count
  from[dbo].[CUSTOMER DATA 1] 
  where SubscriptionEnd is null
  group by region
  Order by Subscriptionend_count desc
  

  .......8 find the total number of active and canceled subscriptions.
 select canceled,
 count(*) as'total_subcriptions'
 From[dbo].[CUSTOMER DATA 1]
 group by
 canceled;

### Data Visualization
  

