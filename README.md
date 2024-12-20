# LITA CAPSTONE PROJECT

### Project Title:Customer Segmentation for a Subscription Service

### Project Overview

In today's competitive subscription-based economy, understanding customer segments is crucial for delivering personalized experiences and optimizing business strategies. This project aims to dissect the customer base into distinct segments based on their behavior, preferences, and demographics.

### Project Objectives

The primary objectives of this project is to utilize data analytics techniques to categorize customers into meaningful segments and trends.To understand customer behavior,analyze subscription patterns,track subscription types and identify key trends in cancellations and renewals. 
By exploring the dataset I sought to:

- analyze usage behavior and engagement metrics
- develop insights to tailor marketing strategies for each customer segment
- highlight trends and patterns that can inform strategic decisions
- enhance customer retention,suggest intervention to improve retention rate.

### Data Source
The primary source of data used here is Lita Capstone Dataset.xlsx which was provided by the INCUBATOR HUB as a project work for every student.

### Methodology
- Micosoft Excel 
   1. for data cleaning 
   2. for analysis 
   3. for data visualization
- Structured Query Language (SQL)
   1. for cleaning and querying
   2. extraction and manipulation of data
- PowerBI for visualization and report      
- Github for porfolio building

### Data cleaning and Preparation
In the initial phase of the data cleaning and preparation,the following actions was performed;
1. data loading and inspections to ensure accuracy and consistency
2. handling missing variables
3. data cleaning and formatting

### Exploratory Data Analysis
EDA involved the exploring of the data to answer some questions about the data such as;

1. Excel: 
- Analyze customer data using pivot tables to find subscription patterns. 
- Calculate the average subscription duration and identify the most popular subscription types.
- Create any other interesting reports. 

2. SQL: 
Hint – You need to load the dataset into your SQL Server environment to write and validate your queries. 
Write queries to extract key insights based on the following questions.  
-  retrieve the total number of customers from each region.
- find the most popular subscription type by the number of customers.
- find customers who canceled their subscription within 6 months.
- calculate the average subscription duration for all customers.
- find customers with subscriptions longer than 12 months.
- calculate total revenue by subscription type.
- find the top 3 regions by subscription cancellations.
- find the total number of active and canceled subscriptions. 
3. Power BI: 
- Build a Power BI dashboard that visualizes key customer segments, cancellations, and subscription trends. Include slicers for interactive analysis.

### Results and Interpretation

<img width="808" alt="capstone customerdata" src="https://github.com/user-attachments/assets/878fd7fb-2b1e-4554-b81d-e23297128b92">

These pivot tables summarizes 'Basic' as  the subscription type with the highest revenue and it is also the most popular by count of '16921'.The average duration is 365.35 and this means its a yearly subscription regardless of the type of subscription.

```SQL

----1 Retrieve the total number of customers from each region---

SELECT COUNT(*) AS Total_customer,Region 
FROM [dbo].[LITACapstoneDataset2]
GROUP BY Region ;

---- 2 find the most popular subscription type by the number of customers---

SELECT COUNT(*) AS Most_popular,Subscription_type
FROM [dbo].[LITACapstoneDataset2]
GROUP BY Subscription_type;

--- 3 find customers who canceled their subscription within 6 months---
SELECT Customer_id
FROM [dbo].[LITACapstoneDataset2]
WHERE Canceled = 1
AND DATEDIFF(MONTH, Subscription_start, Subscription_end) <= 6

---4  calculate the average subscription duration for all customers----
SELECT AVG(Subscription_duration) AS Avg_sub_duration
FROM [dbo].[LITACapstoneDataset2]


---5  find customers with subscriptions longer than 12 months---
SELECT Customer_id ,Subscription_duration
FROM [dbo].[LITACapstoneDataset2]
WHERE Subscription_duration > 366;

------6  calculate total revenue by subscription type---
SELECT SUM(Revenue) AS Total_revenue,Subscription_type
FROM [dbo].[LITACapstoneDataset2]
GROUP BY Subscription_type

--- 7  find the top 3 regions by subscription cancellations----
SELECT TOP 3 Region,COUNT(Canceled) AS Sub_cancellation
FROM [dbo].[LITACapstoneDataset2]
GROUP BY Region
ORDER BY 2 DESC;

SELECT TOP 3 Region,COUNT(Canceled) AS Sub_cancellation
FROM [dbo].[LITACapstoneDataset2]
WHERE Canceled = 1
GROUP BY Region
ORDER BY 2 DESC;



---8  find the total number of active and canceled subscriptions----
SELECT *
FROM [dbo].[LITACapstoneDataset2]

SELECT COUNT(Canceled) AS Total_Sub_count
FROM [dbo].[LITACapstoneDataset2]
 

SELECT COUNT(Canceled) AS Total_Sub_count
FROM [dbo].[LITACapstoneDataset2]
WHERE Canceled = 1 

SELECT COUNT(Canceled) AS Total_Sub_count
FROM [dbo].[LITACapstoneDataset2]
WHERE Canceled = 0

```
<img width="271" alt="totsl customer output 2" src="https://github.com/user-attachments/assets/fea2d871-5af7-4a68-9a89-97eb81b5b605" />
<img width="374" alt="most pop sub output" src="https://github.com/user-attachments/assets/8c68c3b0-5f02-4ef6-8e37-33906610e5d1" />
<img width="533" alt="6 months canceled" src="https://github.com/user-attachments/assets/dc1344f0-b9e3-48d6-8c45-716a9bb1c1ab" />
<img width="435" alt="avg sub duration" src="https://github.com/user-attachments/assets/75ab090f-b035-4b9f-ae17-0126e77e5949" />
<img width="464" alt="12 months canceled" src="https://github.com/user-attachments/assets/c064e2a0-4736-410a-b0ec-2b65d84cb290" />
<img width="536" alt="total revenue output" src="https://github.com/user-attachments/assets/f8a2936e-77b7-4c95-b9c7-3d0a6404e7ff" />
<img width="482" alt="top 3 canceled" src="https://github.com/user-attachments/assets/f8be7ccf-bb04-4e17-b91a-2de9756de8f0" />
<img width="736" alt="active and canceled sub" src="https://github.com/user-attachments/assets/91a5b31d-f622-4b1d-8432-b86275a87d19" />

### Data visualization

Interactive dashboard that visualizes key customer segments, cancellations and subscription trends was created which reveals the several significant insights found in excel and SQL such as customers who canceled their subscription, which is 15,175 and active customers which 18,612  while the total number of customers is 33,787.Filtering on the Region; in the North 5067 canceled subscription and its the top area where customers cancelled subscription,although the difference in the cancelled numbers in the top 3 regions is not so significant.Also,customers in the North go for 'Basic' subscription type,South 'Premium' and West 'Standard'.


<img width="598" alt="customerdata powerBI" src="https://github.com/user-attachments/assets/197fd5df-72df-4b8a-803c-58e06f84a613">

### Recommendations

The insight gotten from this segmentation analysis provide a roadmap for targeted strategies:

- Customized Marketing Campaigns: Tailor marketing efforts to the specific needs and preferences of each of the region
- Retention Strategies: The value for churned customers is very high,theres a need to implement targeted interventions for all segments to improve retention and reduce churn.
- Product Development: Innovate and refine product offerings based on the preferences and behaviors of different segments.

### Conclusion

This project underscores the importance of understanding customer diversity. By leveraging data-driven insights, businesses can enhance customer experiences, optimize marketing efforts, and ultimately drive growth and loyalty in a competitive market.

