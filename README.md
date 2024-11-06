# LITA_CAPSTONE_PROJECT_CUSTOMERSDATA
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
Order by cancellation_count_top3

- West	5044
- South	5064
- North	5067


---8. FIND THE TOTAL NUMBER OF ACTIVE AND CANCELED SUBSCRIPTION---

select 
Sum(case when canceled = 1 then 1 else 0 end) as total_canceled,
Sum(case when canceled = 0 then 1 else 0 end) as total_active
From [dbo].[CustomerData_CP]

Cancelled  Renewaled
15175	     18612
```




## Data visualization:
---




Findings:
---




Recommendation:
---
































































































































































































       

     

