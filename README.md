# CREDIT CARD
## WEEKLY STATUS REPORT

## Content
 - Project objective
 - Data from SQL
 - Data processing & DAX
 - Dashboard & insights
 - Export & share project

# Project Objective
To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.

Import data to SQL database
 - Prepare csv file
 - Create tables in SQL
 - import csv file into SQL

## DAX Queries
```
AgeGroup = SWITCH(
    TRUE(),
    'public cust_detail'[customer_age] < 30 , "20-30",
    'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40 , "30-40",
    'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50 , "40-50",
    'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60 , "50-60",
    'public cust_detail'[customer_age] >= 60 , "60+",
    "Unknown"
)

IncomeGroup = SWITCH(
    TRUE(),
    'public cust_detail'[income] < 30000 , "Low",
    'public cust_detail'[income] >= 30000 && 'public cust_detail'[income] < 70000 , "Mid",
    'public cust_detail'[income] >= 70000 , "High",
    "Unknown"
)

week_number = WEEKNUM('public cc_detail'[week_start_date])

Revenue = 'public cc_detail'[annual_fees]+'public cc_detail'[total_trans_amt]+'public cc_detail'[interest_earned]

CurrentWeekRevenue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    FILTER(
        ALL('public cc_detail'),
        'public cc_detail'[week_number]=MAX('public cc_detail'[week_number])
        )
    )

PreviousWeekRevenue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    FILTER(
        ALL('public cc_detail'),
        'public cc_detail'[week_number]=MAX('public cc_detail'[week_number])-1)
    )

```

# Project Insights- Week 53 (31st	Dec)
## WoW change:
 1 Revenue increased by 28.8%,
 2 Total Transaction Amt & Count increased by 33.5% & 1 %
 3 Customer count increased by 13%%
## Overview YTD:
 1 Overall revenue is 57M
 2 Total interest is 8M
 3 Total transaction amount is 46M
 4 Male customers are contributing more in revenue 31M, female 26M
 5 Blue & Silver credit card are contributing to 93% of overall transactions
 6 TX, NY & CA is contributing to 68%
 7 Overall Activation rate is 57.5%
 8 Overall Delinquent rate is 6.06%

# Credit card financial dashboard using Power BI:
Developed an interactive dashboard using transaction and customer data from a SQL database, to provide real-time insights.
Streamlined data processing & analysis to monitor key performance metrics and trends.
Shared actionable insights with stakeholders based 	on dashboard findings to support decision-making processes.
