### LITA_CAPSTONE_PROJECT-CUSTOMERDATA

### PROJECT TITLE: Customer Segmentation for a Subscription Service

### PROJECT OVERVIEW
This project involves analyzing customer data for a subscription service to identify segments and trends such as understanding customer behavior, track subscription types, 
identify key trends in cancellations and renewals and finally using a Power BI dashboard to present the analysis.

### DATA SOURCE
This secondary data source from LITA_CAPSTONE_PROJECT DATASET.

### TOOLS USED
     - Microsoft Excel for cleaning, analyzing and visualization of data
     - SQL - Structured Query Language for querying of data.
     - Power BI for data visualization
          
### DATA ANALYSIS
- Excel
  
       1. Analyze customer data using pivot tables to find subscription patterns.
  
  - ![PIVOT TABLE FOR CUSTOMERDATA](https://github.com/user-attachments/assets/903e7e4f-403e-482d-ae27-17c98a5e8e4c)

       2. Calculate the average subscription duration and identify the most popular subscription types.
          
  - ![CUSTOMERDATA RESULT](https://github.com/user-attachments/assets/45d3e110-ff30-494f-97f1-ce346bdf3209)
    
       3. Create any other interesting reports

  - ![customer chart](https://github.com/user-attachments/assets/6da572c5-15bf-4f92-a587-82f8f8f86e80)


  - SQL

        CREATE DATABASE LITAPROJECT_DB

        SELECT * FROM  [dbo].[LITA CUSTOMERDATA]

     a. TOTAL NUMBER OF CUSTOMER FOR EACH REGION


        SELECT COUNT(CustomerID)AS TotalNumberOfCustomer, Region FROM [dbo].[LITA CUSTOMERDATA]
          GROUP BY Region


     b. MOST POPULAR SUBSCRIPTION TPYE BY THE NUMBER OF CUSTOMERS


        SELECT TOP 1 COUNT(CUSTOMERID)AS NumberOfCustomer , SubscriptionType
          FROM [dbo].[LITA CUSTOMERDATA]
             GROUP BY SubscriptionType
                ORDER BY COUNT(CUSTOMERID) DESC


     c. CUSTOMERS WHO CANCELED THEIR SUBSCRIPTION WITHIN 6MONTHS
 

        SELECT CustomerName FROM [dbo].[LITA CUSTOMERDATA]
            where Canceled = 1
               AND DATEDIFF (MONTH, SubscriptionStart, SubscriptionEnd) <=6;


     d. AVERAGE SUBSCRIPTION DURATION FOR ALL CUSTOMERS


        SELECT AVG(DATEDIFF(DAY, SubscriptionStart, SubscriptionEnd)) 
            AS AverageSubscriptionDuration FROM [dbo].[LITA CUSTOMERDATA]


     e. CUSTOMER WITH SUBSCRIPTION LONGER THAN 12 MONTHS


        SELECT CustomerName FROM [dbo].[LITA CUSTOMERDATA]
              where DATEDIFF (MONTH, SubscriptionStart, SubscriptionEnd) >12; 


     f. TOTAL REVENUE BY SUBSCRIPTION TYPE 


        SELECT SUM(Revenue)as TotalRevenue, SubscriptionType FROM [dbo].[LITA CUSTOMERDATA]
            GROUP BY SubscriptionType


     g. TOP 3 REGIONS BY SUBSCRIPTION CANCELLATIONS

    
        SELECT TOP 3 Region, COUNT(CustomerID) AS Cancellations FROM [dbo].[LITA CUSTOMERDATA]
             where Canceled = 1
                 GROUP BY Region
                     ORDER BY Cancellations DESC


     h. TOTAL NUMBER OF ACTIVE AND CANCELED SUBSCRIPTION


        SELECT SUM (CASE WHEN Canceled =0 THEN 1 ELSE 0 END) AS ActiveSubscriptions, 
               SUM (CASE WHEN Canceled =1 THEN 1 ELSE 0 END) AS CanceledSubscriptions
                    FROM[dbo].[LITA CUSTOMERDATA]







