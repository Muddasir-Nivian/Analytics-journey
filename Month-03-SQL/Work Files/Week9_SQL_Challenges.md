# Week 9 SQL Practice File

**Q1.** Return every column from the customers table.  
**Answer:**  
```sql
SELECT * FROM customers;
```

**Q2.** Return only customer_name and region from the customers table.
**Answer:**  
```sql
SELECT customer_name, region FROM customers;
```

**Q3.** Return product_name and unit_price from the products table.  
**Answer:**  
```sql
SELECT product_name, unit_price FROM products;
```

**Q4.** Return order_id and order_date from the orders table.  
**Answer:**  
```sql
SELECT order_id, order_date FROM orders;
```

**Q5.** Return the names of all customers in the North region.  
**Answer:**  
```sql
SELECT * FROM customers WHERE region='North';
```

**Q6.** Return all products with a unit_price below 200.  
**Answer:**  
```sql
SELECT * FROM Products WHERE unit_price<200;
```

**Q7.** Return all orders placed using Credit Card as the payment method.  
**Answer:**  
```sql
SELECT * FROM orders WHERE payment_method='Credit Card';
```

**Q8.** Return all customers who are NOT in the North region.  
**Answer:**  
```sql
SELECT * FROM customers WHERE region!='North';
```

**Q9.** Return all customers who are in the North region AND in the
Premium segment.  
**Answer:**  
```sql
SELECT * FROM customers WHERE region='North' AND
segment='Premium';
```

**Q10.** Return all products that are in the Electronics category AND cost
more than 1000.  
**Answer:**  
```sql
SELECT * FROM products WHERE category='Electronics' AND
unit_price>1000;
```

**Q11.** Return all customers who are either in the South OR the West
region.  
**Answer:**  
```sql
SELECT * FROM customers WHERE region='South' OR region='West';
```

**Q12.** Return all orders placed via Credit Card OR PayPal.  
**Answer:**  
```sql
SELECT * FROM orders WHERE payment_method='Credit Card' OR
'Paypal';
```

**Q13.** Return all products sorted by unit_price from cheapest to most
expensive.  
**Answer:**  
```sql
SELECT * FROM products ORDER BY unit_price asc;
```

**Q14.** Return all orders sorted by order_date from most recent to oldest.  
**Answer:**  
```sql
SELECT * FROM orders ORDER BY order_date desc;
```

**Q15.** Return customer_name and region sorted alphabeƟcally by
customer_name.  
**Answer:**  
```sql
SELECT customer_name, region FROM customers ORDER BY
customer_name asc;
```

**Q16.** Return a list of all unique regions in the customers table — no
repeats.  
**Answer:**  
```sql
SELECT DISTINCT region FROM customers;
```

**Q17.** Return a list of all unique payment methods used across all orders.  
**Answer:**  
```sql
SELECT DISTINCT payment_method FROM orders;
```

**Q18.** Return a list of all unique categories in the products table.  
**Answer:**  
```sql
SELECT DISTINCT category FROM products;
```

**Q19.** Return the first 3 customers from the customers table.  
**Answer:**  
```sql
SELECT * FROM customers LIMIT 3;
```

**Q20.** Return the 5 cheapest products by unit_price.  
**Answer:** 
```sql
SELECT * FROM products ORDER BY unit_price ASC LIMIT 5;
```

**Q21.** The sales director wants a list of all Premium customers sorted
alphabetically. Return their names only.  
**Answer:**  
```sql
SELECT customer_name FROM customers WHERE
segment='Premium' ORDER BY customer_name ASC;
```

**Q22.** Find all products that cost between 50 and 500 dollars inclusive.
Sort them by price highest to lowest.  
**Answer:**  
```sql
SELECT * FROM products WHERE unit_price>=50 AND
unit_price<=500 ORDER BY unit_price DESC;
```

**Q23.** How many unique customers placed orders using a Credit Card?
Think carefully — orders and customers are in separate tables.
You need order_items? No — which two tables do you need here?  
**Answer:**  
```sql
SELECT DISTINCT customer_name, payment_method FROM
customers,orders WHERE payment_method='Credit Card';
```

**Q24.** Return the names and prices of all products in either the Beauty
or Sports category, sorted by price from lowest to highest.  
**Answer:**  
```sql
SELECT product_name,unit_price FROM products WHERE
category='Beauty' OR category='Sports' ORDER BY unit_price ASC;
```

**Q25.** The finance team wants to see every order placed in January 2026
via Credit Card. Return order_id and order_date. Hint: dates are stored
as text — use LIKE '2026-01%' to match the January pattern.  
**Answer:**  
```sql
SELECT order_id,order_date FROM orders WHERE
order_date>='2026-01-05' AND order_date<='2026-01-28' AND
payment_method='Credit Card';
```
