# Credit_Card_Financial_Dashboard
power bi dashboard

**Title:**

Credit Card Financial Dashboard

**Project Objective:** 

To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.

**Steps:**

1. Import the data in SQL, clean and organize the data.
2. Import the data you want to visualize in PowerBi.
3. Select the data source you want to use.
4. Create a data model.
5. Build relationships between tables.
6. Visual your date.
7. Design your dashboard.
8. Find the insights from data.
10. Share and Collaborate.

**Insights:**

WoW change:
• Revenue increased by 28.8%,
• Total Transaction Amt & Count increased by xx% & xx%
• Customer count increased by xx%
Overview YTD:
• Overall revenue is 57M
• Total interest is 8M
• Total transaction amount is 46M
• Male customers are contributing more in revenue 31M, female 26M
• Blue & Silver credit card are contributing to 93% of overall
transactions
• TX, NY & CA is contributing to 68%
• Overall Activation rate is 57.5%
• Overall Delinquent rate is 6.06%

**DAX Queries**

AgeGroup = SWITCH(
 TRUE(),
 'public cust_detail'[customer_age] < 30, "20-30",
 'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
 'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
 'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
 'public cust_detail'[customer_age] >= 60, "60+",
 "unknown"
 )
IncomeGroup = SWITCH(
 TRUE(),
 'public cust_detail'[income] < 35000, "Low",
 'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
 'public cust_detail'[income] >= 70000, "High",
 "unknown"
)

week_num2 = WEEKNUM('public cc_detail'[week_start_date])
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]
Current_week_Reveneue = CALCULATE(
 SUM('public cc_detail'[Revenue]),
 FILTER(
 ALL('public cc_detail'),
 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])))
Previous_week_Reveneue = CALCULATE(
 SUM('public cc_detail'[Revenue]),
 FILTER(
 ALL('public cc_detail'),
 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))
 
