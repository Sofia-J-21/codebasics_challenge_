# codebasics_challenge_
## Sales insights data analysis project 

## PROJECT OBJECTIVE
The objective of this project is to analyze sales performance across various markets and customers using SQL for data extraction and Power BI for data visualization. The analysis helps in identifying revenue trends, top-performing regions, products, and customers to support strategic business decisions.

##  Project Insights
Delhi NCR generated the highest revenue of ₹519.51M and contributed the most to sales quantity (1M units).

Total Revenue achieved across all markets: ₹984.81M, with 2M units sold overall.

The top customer, Electricalsara Stores, contributed ₹413.33M in revenue.

A product listed as (Blank) generated the highest product revenue of ₹468.96M, suggesting potential data quality issues.

Revenue trends show a declining pattern post mid-2019, with noticeable peaks in early 2018 and 2019.

Chennai contributed ₹18.04M in revenue but recorded 0 units sold, indicating possible data entry or sales tracking issues.


## Business Questions Answered
1. Which markets generated the highest revenue and sales quantity?

2. Who are the top 5 customers in terms of revenue?

3. What are the top-selling products?

4. How has revenue trended over time?

5. What is the revenue contribution of Chennai and other specific markets?

6. What is the total revenue in 2020 overall, in January, and specifically in Chennai?

7. How many unique product codes were sold in Chennai?

8. What proportion of transactions were conducted in USD vs INR?



## Data Analysis Using SQL 

1. Show all customer records

    `SELECT * FROM customers;`

1. Show total number of customers

    `SELECT count(*) FROM customers;`

1. Show transactions for Chennai market (market code for chennai is Mark001

    `SELECT * FROM transactions where market_code='Mark001';`

1. Show distrinct product codes that were sold in chennai

    `SELECT distinct product_code FROM transactions where market_code='Mark001';`

1. Show transactions where currency is US dollars

    `SELECT * from transactions where currency="USD"`

1. Show transactions in 2020 join by date table

    `SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;`

1. Show total revenue in year 2020,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";`
	
1. Show total revenue in year 2020, January Month,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");`

1. Show total revenue in year 2020 in Chennai

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020
and transactions.market_code="Mark001";`


Data Analysis Using Power BI
============================

1. Formula to create norm_amount column

`= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)`

## Power BI Dashboard
<img width="1076" height="665" alt="Screenshot 2025-08-07 135503" src="https://github.com/user-attachments/assets/7e5c2fdc-21fc-4152-ade2-81fbc1660863" />


## Conclusion
The sales data analysis reveals that a few markets and customers dominate revenue generation, particularly Delhi NCR and Electricalsara Stores. While the overall revenue is high, the downward trend in sales over time is a concern. Data quality issues, such as missing product names and zero sales quantities in some regions, should be addressed for better insights. This project demonstrates how SQL and Power BI can be effectively combined for end-to-end business analysis.







