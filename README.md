# Credit_card_financial_dashboard

**OBJECTIVE**: To develop a comprehensive credit card weekly dashboard that provides real time insights into key performance indicators and trends enabling stakeholders to monitor and analyse credit card operations effectively

**STEPS**:

1.Using PostgreSQL:Creating tables,credit card detail table and customer detail table ,Then importing data from csv file by writing query or by import option available in schema

2.Importing database to powerbi

3.Data processing in powerquery,DAX fuctions

**DAX queries**

AgeGroup = SWITCH(TRUE(),
'public cust_detail'[customer_age]<30,"20-30",
'public cust_detail'[customer_age]>=30 && 'public cust_detail'[customer_age]<40,"30-40",
'public cust_detail'[customer_age]>=40 && 'public cust_detail'[customer_age]<50,"40-50",
'public cust_detail'[customer_age]>=50 && 'public cust_detail'[customer_age]<60,"50-60",
'public cust_detail'[customer_age]>=60,"60+",
"unknown")

IncomeGroup = SWITCH(TRUE(),
 'public cust_detail'[income]<35000,"low",
 'public cust_detail'[income]>=3500 && 'public cust_detail'[income]<70000,"Med",
  'public cust_detail'[income]>=70000,"High",
  "unknown")

Current_Week_Revenue = CALCULATE(
  SUM('public cc_detail'[Revenue]),
    FILTER(
        ALL('public cc_detail'[Week_num2]) ,
        'public cc_detail'[Week_num2]=MAX('public cc_detail'[Week_num2])))

Previous_Week_Revenue = CALCULATE(
   SUM('public cc_detail'[Revenue]),
    FILTER(
        ALL('public cc_detail'[Week_num2]) ,
        'public cc_detail'[Week_num2]=MAX('public cc_detail'[Week_num2])-1))

wow_revenue = DIVIDE(([Current_Week_Revenue]-[Previous_Week_Revenue]),[Previous_Week_Revenue])

4.Designing Dashboard



**INSIGHTS**

Overview YTD(Year to date):

• Overall revenue is 57M

• Total interest is 8M

• Total transaction amount is 46M

• Male customers are contributing more in revenue 31M, female 26M

• Blue & Silver credit card are contributing to 93% of overall transactions

• TX, NY & CA is contributing to 68%

• Overall Activation rate is 57.5%

• Overall Delinquent rate is 6.06%

