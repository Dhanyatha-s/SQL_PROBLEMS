###  Sales Database has 1. customers 2. date, 3.market 4.product, 5.transcations Tables.
#### check on database here [db_dump.sql](https://github.com/Dhanyatha-s/SQL_PROBLEMS/blob/d614775dd1535e772fe8353dca3ffce93d26f8dd/Databases/db_dump.sql)
> -- QUERIES  
1 . How many transaction has happened  
2 . How many transaction has happened in 'Chennai'  
3 . Show the transcation of yr 2020  
4 . What is the total revenue in yr 2020  
5 . What is the total revenue of chennai sales in yr 2020  
6 . what are the products sold in chennai in yr 2020  

 1 . How many transaction has happened 
```
 select count(*) from sales.transactions -- 150283
```
```
select * from sales.transactions
```
2 . How many transaction has happened in 'Chennai'
```
select count(*) from sales.transactions where market_code = 'Mark001'
```
 3 . Show the transcation of yr 2020
 ```
 select sales.transactions.*, sales.date.* from sales.transactions
 inner join sales.date
 on sales.transactions.order_date = sales.date.date 
 where sales.date.year = 2020
```
 4 . What is the total revenue in yr 2020
```
select sum(sales.transactions.sales_amount) as revenue
from sales.transactions
inner join sales.date
on sales.transactions.order_date = sales.date.date 
where sales.date.year = 2020
```
5 . What is the total revenue of chennai sales in yr 2020
```
select sum(sales.transactions.sales_amount) as revenue
from sales.transactions
inner join sales.date
on sales.transactions.order_date = sales.date.date 
where sales.date.year = 2020
and market_code= 'Mark001'
```
6 . what are the products sold in chennai in yr 2020
```
select product_code from sales.transactions 
where market_code= 'Mark001'
```
```
select product_code from sales.transactions inner join sales.date  on sales.transactions.order_date = sales.date.date 
where sales.date.year = 2020 and market_code= 'Mark001'
```
