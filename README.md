# LITA_CAPSTONE_PROJECT_CUSTOMERSDATA
---

## Project Overview:
This project focuses on analyzing customer data for a subscription service to identify key customer segments and trends. 
The primary objective is to understand customer behavior, track subscription types, and identify important patterns in cancellations and renewals.
The insights generated will help improve customer retention strategies, optimize marketing efforts, and enhance subscription offerings.
The final deliverable will be an interactive Power BI dashboard that showcase the  customer segments, cancellations, and subscription trends.
which will in turn affect the enhancement of the services render.


## Source of Data:
---
The data used in this analysis is emanent from primary source such as customer subscription records, which include essential columns such as CustomerID, 
CustomerName, Region, SubscriptionType, SubscriptionStart, SubscriptionEnd, Canceled, and Revenue. This data provides 
information on customer demographics, subscription behavior, revenue, and cancellation history.

## Tools to be Used:
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
     
## Data Cleaning and Preparation Process
---
- Duplicates remover:
   - Check for duplicate rows in the dataset, especially in CustomerID or subscription records, and remove any redundancies.
   - Standardize Data:
   - Ensure consistency in data formats, such as dates (SubscriptionStart, SubscriptionEnd),
   - I checked for uniformity in categorical fields like SubscriptionType and Region.
   - Data Transformation: Calculate new fields, such as subscription duration   .
   - Active Status: Create an indicator for active subscriptions based on SubscriptionEnd and Canceled columns.


       

     

