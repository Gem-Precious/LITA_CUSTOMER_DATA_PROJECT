# Customer Data Analysis

### Project Overview

This data analysis project is targeted towards generating insights into customers behavior and subscription trends of a Subscription Service Company. analyzing various aspects of the data, I aim to identify different customer segments and partterns, Understanding customers' preferrence, enabling data-driven decisions to be made.

### Data Sources

Customer_Data: The primary data source use for this analysis is the "Customer_data.csv file" containing detailed information on the Subscription status of the company.

### Tools Used

- Excel - Data cleaning and analysis with Pivot tables
- SQL - Data analysis
- PowerBI - Creating of reports


### Data Preparations

In the initial data preparation phase, the following tasks were performed:

1. Data loading and Inspection
2. Handling missing values
3. Data cleaning and formating


 ### Questions

- Retrieve the total number of customers from each region
- Find the most popular subscription type by the number of customers
- Find customers who canceled their subscription within 6 months
- Calculate the average subscription duration for all customers
- Find customers with subscriptions longer than 12 months
- Calculate total revenue by subscription type
- Find the top 3 regions by subscription cancellations
- Find the total number of active and canceled subscriptions

  
 ### Data Analysis

 Some interesting codes worked with:

 ~~~ SQL

SELECT * FROM [dbo].[Customer_Data]

SELECT Region, COUNT(CustomerID) As Number_Of_Customers
FROM [dbo].[Customer_Data]
GROUP BY Region

SELECT TOP 1 (SubscriptionType) as PopularSubscription,
count(CustomerID) As CustomerCount
FROM [dbo].[Customer_Data]
GROUP BY SubscriptionType

SELECT COUNT(CustomerID) AS CanceledSubscription
FROM [dbo].[Customer_Data]
WHERE Canceled = 1 and DATEDIFF(Month,SubscriptionStart,
SubscriptionEnd) <=6

SELECT AVG(DATEDIFF(Day,SubscriptionStart,SubscriptionEnd))
AS AverageDuration From [dbo].[Customer_Data] 

SELECT CustomerID, CustomerName, SubscriptionType
FROM [dbo].[Customer_Data]
WHERE DATEDIFF(Month,SubscriptionEnd,SubscriptionStart) >12

SELECT SubscriptionType, Sum(Revenue) AS TotalRevenue
From [dbo].[Customer_Data]
GROUP BY SubscriptionType
ORDER BY 2 DESC

SELECT Top 3 Region, Count(Canceled) AS CancelledSub
FROM [dbo].[Customer_Data]
WHERE Canceled = 1
GROUP BY Region
ORDER BY 2 DESC

SELECT 
CASE 
WHEN Canceled = 1 THEN 'Canceled'
ELSE 'Active'
END AS SubscriptionStatus,
COUNT(*) SubscriptionCount
FROM [dbo].[Customer_Data]
GROUP BY Canceled


~~~

### Results

The analysis are summarized as follows:

- The number of customers in each region are almost evenly distributed
- Basic is the most popular subcription type used by the majority of customers
- No customers canceled their subscription within 6 months
- The average duration for all subscriptions was 365 days
- There was no subscription longer than 12 months
- Basic is the highest generating revenue
- There was no cancelation in the East region
- The number of active subscriptions is higher than number of canceled subscriptions


### Conclusion

- Basic is the highest subscription used mostly in the east and north regions
- Basic has the most active subcriptions and generates the highest revenue


### Recommendations

Based on the analysis, we recommend the following actions:

- Focus on expanding and promoting Basic subscriptions
- Implement a customer segmentation strategy to target high-LTV customers effectively
- More marketing strategies should be implemented in the east region to generate more revenue
 

 
