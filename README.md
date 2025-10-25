# Power-BI-Project-2

# Credit Card Weekly Dashboard – Data Analysis Project

📋 Project Objective

To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.

📊 Project Overview

Tools Used: Power BI / SQL 
Dataset: Credit card transactions dataset (weekly data)
Duration: Week 53 (ending 31st Dec)

--------------Metrics Analyzed:-----------

Revenue
Transaction amount and count
Customer growth
Interest income
Activation and delinquency rates

💡 Key Insights

------------Week-over-Week (WoW) Changes:------------

Revenue increased by 28.8%

--------------Year-to-Date (YTD) Overview:------------------

Overall revenue: $57M
Total interest: $8M
Total transactions: $46M

-----------Male vs Female contribution: $31M vs $26M-----------
------------Blue & Silver credit cards contribute 93% of transactions---------
-----------------TX, NY & CA contribute 68% of overall revenue---------------
--------------Activation rate: 57.5%-----------------
------------------Delinquent rate: 6.06%---------------------

========DAX============

**--AgeGroup** = SWITCH(TRUE(),
 customer[Customer_Age]<=30, "20-30",
 customer[Customer_Age]>=30 && customer[Customer_Age]<40, "31-40",
 customer[Customer_Age]>=40 && customer[Customer_Age]<50, "41-50",
 customer[Customer_Age]>=50 && customer[Customer_Age]<60, "51-60",
 customer[Customer_Age]>=60, "60+"
)
**--IncomeGroup** = SWITCH(TRUE(),
 customer[Income]<=35000, "Low",
 customer[Income]>35000 && customer[Income]<=70000, "Medium",
 customer[Income]>70000, "High", "Unknown"
)

**--previous_week_revenue** = CALCULATE(SUM(credit_card[Revenue]),
 FILTER(ALL(credit_card), credit_card[Week_Num]=MAX(credit_card[Week_Num])-1)
)

**--wow_change** = DIVIDE([current_week], [previous_week_revenue], [previous_week_revenue])



# 💳 Power BI Project 2  
## Credit Card Weekly Dashboard – Data Analysis Project  

---

### 📋 Project Objective  
To develop a comprehensive **credit card weekly dashboard** that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.

---

### 📊 Project Overview  

**Tools Used:** Power BI, SQL  
**Dataset:** Credit card transactions dataset (weekly data)  
**Duration:** Week 53 (ending 31st Dec)  

#### Metrics Analyzed:
- Revenue  
- Transaction amount and count  
- Customer growth  
- Interest income  
- Activation and delinquency rates  

---

### 💡 Key Insights  

#### 📈 Week-over-Week (WoW) Changes:
- Revenue increased by **28.8%**

#### 📅 Year-to-Date (YTD) Overview:
- Overall revenue: **$57M**  
- Total interest: **$8M**  
- Total transactions: **$46M**  

#### 👥 Customer Insights:
- Male vs Female contribution: **$31M vs $26M**  
- Blue & Silver credit cards contribute **93%** of total transactions  
- TX, NY & CA contribute **68%** of overall revenue  
- Activation rate: **57.5%**  
- Delinquent rate: **6.06%**

---
📈 Dashboard Features

Interactive filters for region, card type, and customer demographics
Dynamic KPI cards showing revenue, transactions, and interest
Trend lines for WoW performance
State-level contribution map visualization


<img width="1365" height="627" alt="Screenshot 2025-10-15 193622" src="https://github.com/user-attachments/assets/c968e1d0-67dc-4733-a5d8-85b57ff58d38" />

<img width="1364" height="663" alt="Screenshot 2025-10-15 193514" src="https://github.com/user-attachments/assets/54e0ceb2-1d7d-4e0e-a280-0e7b90a2bb4f" />

### 🧮 DAX Measures  

```DAX
-- AgeGroup  
AgeGroup = 
SWITCH(
    TRUE(),
    customer[Customer_Age] <= 30, "20-30",
    customer[Customer_Age] >= 30 && customer[Customer_Age] < 40, "31-40",
    customer[Customer_Age] >= 40 && customer[Customer_Age] < 50, "41-50",
    customer[Customer_Age] >= 50 && customer[Customer_Age] < 60, "51-60",
    customer[Customer_Age] >= 60, "60+"
)

-- IncomeGroup  
IncomeGroup = 
SWITCH(
    TRUE(),
    customer[Income] <= 35000, "Low",
    customer[Income] > 35000 && customer[Income] <= 70000, "Medium",
    customer[Income] > 70000, "High",
    "Unknown"
)

-- Previous Week Revenue  
previous_week_revenue = 
CALCULATE(
    SUM(credit_card[Revenue]),
    FILTER(
        ALL(credit_card),
        credit_card[Week_Num] = MAX(credit_card[Week_Num]) - 1
    )
)

-- WoW Change  
wow_change = 
DIVIDE([current_week], [previous_week_revenue], [previous_week_revenue])



