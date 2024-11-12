# LITA_CAPSTONE_PROJECT_CUSTOMERDATA
---

## Project Title: Segmentation and Customers' Subscription Analysis
---

[Project Overview](#project-overview)

[Data Sources](#data-sources)

[Tools Used](#tools-used)

[Data Cleaning and preparation](#data-cleaning-and-preparation)

[Exporatory Data Analysis](#exporatory-data-analysis)

[Data Analysis](#data-analysis)

[Data Visualization](#data-visualization)

[Finding](#findings)

[Recommendation](#recommendation)


## Project Overview:
This project focuses on analyzing customer data for a subscription service to identify key customer segments and trends. 
The primary objective is to understand customer behavior, track subscription types, and identify important patterns in cancellations and renewals.
The insights generated will help improve customer retention strategies, optimize marketing efforts, and enhance subscription offerings.
The final deliverable will be an interactive Power BI dashboard that showcase the  customer segments, cancellations, and subscription trends.
which will in turn affect the enhancement of the services render.


## Data Sources:
---
The data used in this analysis is emanent from primary source such as customer subscription records, which include essential columns such as CustomerID, 
CustomerName, Region, SubscriptionType, SubscriptionStart, SubscriptionEnd, Canceled, and Revenue. This data provides 
information on customer demographics, subscription behavior, revenue, and cancellation history.

## Tools Used:
- Excel Microsoft Excel[Download Here](https://www.microsoft.com)
      - For initial data exploration, 
      - creating pivot tables, 
        and calculating summary statistics using Average and 
- SQL -Structured query language [Download Here](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
     - For data extraction and analysis through structured queries.
- Power BI - power business intellegence:[download Here](https://power-bi-desktop.en.microsoft.com)
     - For building an interactive dashboard to visualize key insights, trends, and segments.
 - Gitup- Github account[Download Here](https://www.github.com)
     - for portfolio building
     
## Data Cleaning and Preparation:
---
- Duplicates remover:
   - Check for duplicate rows in the dataset, especially in CustomerID or subscription records, and remove any redundancies.
   - Standardize Data:
   - Ensure consistency in data formats, such as dates (SubscriptionStart, SubscriptionEnd),
   - I checked for uniformity in categorical fields like SubscriptionType and Region.
   - Data Transformation: Calculate new fields, such as subscription duration   .
   - Active Status: Create an indicator for active subscriptions based on SubscriptionEnd and Canceled columns.
     
## Exporatory Data Analysis
---
EDA is used to analyze the data set by answering some questons about the data, such as;Retrieve the total number of customers from each region.

- Find the most popular subscription type by the number of customers.
- Find customers who canceled their subscription within 6 months.
- Calculate the average subscription duration for all customers.
- Find customers with subscriptions longer than 12 months.
- Calculate total revenue by subscription type.
- Find the top 3 regions by subscription cancellations.
- Find the total number of active and canceled subscriptions.


## Data Analysis
---
This is where we include some basic lines of code/ queries or even some of the DAX expression used during analysis;

```SQL
Select *from CustomerData_CP

---Total number of Customers by Region---

Select  Region, 
count(Customerid) as Total_Customers 
from [dbo].[CustomerData_CP]
Group by Region
Order by Region asc1

-  East 8488
-  North 8433
-  South 8446
-  West 8420


---2. Most popular Subscription type by Customer---

Select top 1 subscriptiontype,
Count(Customerid) as Total_Customers
From [dbo].[CustomerData_CP]
Group by subscriptiontype 
Order by Total_Customers desc

- basic 16921


--3. Customers who Cancelled their Subscription within 6 Months--

update [dbo].[CustomerData_CP]
set Canceled = 1
      where Canceled = 'true'
update [dbo].[CustomerData_CP]
set canceled = 0
where canceled = 'false'
select count(customerid) as canceled_customers_in_6mnth
from [dbo].[CustomerData_CP] 
where Canceled = 1
and SubscriptionEnd>=dateadd(month,-6,getdate())

 - 3385



---4. Average Subscription duration for all Customers---

Select AVG(datediff(day,subscriptionstart,subscriptionend))
as avg_subscription_duration
from [dbo].[CustomerData_CP]365

- 365

---5. Customers with subcription longer than 12 Months---
 
Select count(customerid) as suscrption_12_month
From [dbo].[CustomerData_CP]
where subscriptionstart<Dateadd(month,-12, getdate())subscriptiontype	total_revenue

 - 33787


---6. CALCULATE SUBSCRIPTION TYPE BY REVENUE---

Select subscriptiontype,
Sum(revenue) as total_revenue 
From [dbo].[CustomerData_CP]
Group by subscriptiontype

 - Basic	 33,776735
- Premium	16,899,064
- Standard	16,864,376


--7.FIND THE TOP 3 REGIONS BY SUBSCRIPTION--

Select top 3 region,
Count(customerid) as cancellation_count_top3
From [dbo].[CustomerData_CP] 
Where Canceled = 1
Group by Region
Order by cancellation_count_top3 desc

- North	5067
- South	5064
- West	5044



---8. FIND THE TOTAL NUMBER OF ACTIVE AND CANCELED SUBSCRIPTION---

select 
Sum(case when canceled = 1 then 1 else 0 end) as total_canceled,

Sum(case when canceled = 0 then 1 else 0 end) as total_active
From [dbo].[CustomerData_CP]

Cancelled  Active
15175	     18612
```




![CUSTOMERDATA PIVOT TABLES](https://github.com/user-attachments/assets/47ef73e2-4fe8-439a-b2b5-c61b0af7c685)





## Data visualization:
---




![CUSTOMERDATA DASHBOARD 2](https://github.com/user-attachments/assets/666f2032-e70d-4080-8f2c-9fe39e75b1a1)



Findings:
---
 In the analysis of the data given the following was found



1. Total Subscriptions and Revenue:

- Unique subscription customers: 33,787
- Total revenue: $67,540,176 (approx. $68 million)
- Subscription Renewals and Inactive Accounts:

- Total renewals: 18,612
- Inactive subscriptions: 15,175

2. Subscription Types:

- Basic: 16,921 (50.08%)
- Premium: 8,420 (24.92%)
- Standard: 8,446 (25%)

3. Regional Distribution:

- East: 8,488 customers
- North: 8,433 customers
- South: 8,446 customers
- West: 8,420 customers

4. Revenue by Subscription Type:

- Basic: $33,776,735
- Premium: $16,899,064
- Standard: $16,864,376
- Total revenue: $67,540,176 (aligns with total revenue)

 This overview gives a clear picture of subscription types, customer distribution, and revenue breakdown across regions

 Below is a detail tabular representation of the 20 unique Customer analysis using their unique name

|Serial No|Customer name|Total Customerid|Revenue generated($)|Region Covered|Subscription type|Renewal|Month|
|---------|-------------|----------------|--------------------|--------------|-----------------|-------|-----|
|1        |Alex         |1690            |3,377,675           |East          | Basic           |1690   |March|
|2        |Anna         |1700            |3,398,288           |West          |Standard         |1700   |December|
|3        |Chris        |1692            |3,351,226           |North         |Basic            |0      |January|
|4        |Dan          |1680            |3,354,858           |East          |Basic            |1680   |July   |
|5        |Elia         |1679            |3,346,887           |South         |Premmium         |0      |June|
|6        |Eva          |1692            |3,384,539           |South         |Premium          |0      |October|
|7        |Grace        |1687            |3,385,349           |West          |Standard         |0      |April|
|8        |James        |1673            |3,345,833           |North         |Basic            |1673   |May|
|9        |Jane         |1693            |3,395,374           |South         |Premium          |0      |February|
|10       |John         |1693            |3,378,897           |North         |Basic            |1693   |January|
|11       |Liam         |1718            |3,437,444           |East          |Basic            |1718   |November|
|12       |Maria        |1662            |3,326,162           |West          |Standard         |0      |April|
|13       |Mike         |1714            |3,427,436           |East          |Basic            |1714   |July|
|14       |Nina         |1695            |3,399,895           |West          |Standard         |0      |August|
|15       |Paul         |1686            |3,361,350           |East          |Basic            |1686   |March|
|16       |Rob          |1690            |3,376,796           |North         |Basic            |0      |May|
|17       |Sara         |1676            |3,354,682           |West          |Standard         |1676   |August|
|18       |Sophia       |1699            |3,414,995           |South         |Premium          |1699   |June|
|19       |Tom          |1685            |3,365,221           |North         |Basic            |0      |September|
|20       |Zoe          |1683            |3,357,269           |South         |Premium          |1683   |February|
|Total    |             |                |67,540,176          |              |                 |18612  |        |










Recommendation:
---
































































































































































































       

     

