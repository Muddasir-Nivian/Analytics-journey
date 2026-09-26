# Week 10 — SQL Challenges
## Aggregate Functions, GROUP BY, HAVING

**Same database as Week 9 — no new setup needed.** If you cleared your
browser tab, re-run Week9_Database_Setup.sql first.

---

## CONCEPT FIRST — This Week Is Your SUMIFS and COUNTIFS, Renamed

Everything this week is logic you already built in Excel. The names
change. The thinking does not.

| Excel | SQL | What it does |
|---|---|---|
| COUNT / COUNTA | COUNT() | Counts rows |
| SUM | SUM() | Adds values |
| AVERAGE | AVG() | Averages values |
| MAX | MAX() | Highest value |
| MIN | MIN() | Lowest value |
| A Pivot Table's Rows field | GROUP BY | Splits data into groups before aggregating |
| Filtering AFTER a pivot is built | HAVING | Filters groups after aggregation, not rows before it |

The one genuinely new idea this week is **HAVING**, because Excel
never needed a separate word for it — a Pivot Table lets you filter
the finished summary visually. SQL needs a specific keyword for that,
since WHERE only filters raw rows *before* grouping happens.

---

## SECTION 1 — Aggregate Functions Alone (no GROUP BY yet)

**Syntax:**
```sql
SELECT COUNT(*) FROM table_name;
SELECT AVG(column_name) FROM table_name;
```

Used alone, an aggregate function collapses the ENTIRE table into
one single number.

---

**Q1.** How many total customers does Vantree have?  
**Answer:** select count(DISTINCT customer_name) from customers;

**Q2.** How many total products does Vantree sell?  
**Answer:** select count(DISTINCT product_id) AS Total_products from order_items;

**Q3.** What is the average unit_price across all products?  
**Answer:** select AVG(unit_price) from products;

**Q4.** What is the most expensive product's price? (Just the number,
not the product name yet.)  
**Answer:** select MAX(unit_price) from products;

**Q5.** What is the cheapest product's price?  
**Answer:** select MIN(unit_price) from products;

---

## SECTION 2 — GROUP BY (splitting into groups before aggregating)

**What GROUP BY does:** Before SQL calculates an aggregate, it first
splits every row into buckets based on a column you choose — then
calculates the aggregate separately for each bucket.

**This is exactly your Excel Pivot Table's Rows field.** If you put
Region in Rows and Sum of Revenue in Values, you were doing GROUP BY
without knowing the word for it.

**Syntax:**
```sql
SELECT column_to_group_by, AGGREGATE_FUNCTION(other_column)
FROM table_name
GROUP BY column_to_group_by;
```

**The rule that trips people up:** every column in your SELECT list
must either be inside an aggregate function, or be the exact column
you're grouping by. You cannot mix in a random third column.

---

**Q6.** How many customers are in each region? Return region and the count.  
**Answer:** select DISTINCT region, count(DISTINCT customer_id) from customers GROUP BY region;

**Q7.** What is the average unit_price for each product category?  
**Answer:** select DISTINCT category, avg(unit_price) from products GROUP BY category;

**Q8.** How many customers are in each segment (Premium, Standard, Budget)?  
**Answer:** select DISTINCT segment, count(DISTINCT customer_id) from customers GROUP BY segment;

**Q9.** How many orders were placed with each payment method?  
**Answer:** select DISTINCT payment_method, count(order_id) from orders GROUP BY payment_method;

**Q10.** For each product_id in order_items, what is the total quantity
sold? (Group by product_id, sum the quantity.)  
**Answer:** select DISTINCT product_id, sum(quantity) from order_items GROUP BY product_id;

---

## SECTION 3 — HAVING (filtering AFTER grouping)

**The critical distinction:**

**WHERE** filters individual rows *before* any grouping happens.
**HAVING** filters entire groups *after* the aggregate has been calculated.

You cannot write `WHERE COUNT(*) > 2` — WHERE runs too early to even
know what COUNT(*) is yet. HAVING exists specifically to filter on
the aggregate result itself.

**Syntax:**
```sql
SELECT column_to_group_by, AGGREGATE_FUNCTION(other_column)
FROM table_name
GROUP BY column_to_group_by
HAVING AGGREGATE_FUNCTION(other_column) > some_value;
```

---

**Q11.** Which product categories have an average unit_price above 500?  
**Answer:** select DISTINCT category, avg(unit_price) from products GROUP BY category HAVING avg(unit_price)>500;

**Q12.** Which regions have more than 2 customers?  
**Answer:** select DISTINCT region, count(DISTINCT customer_id) from customers GROUP BY region HAVING count(DISTINCT customer_id)>2;

**Q13.** Which payment methods were used more than 4 times?  
**Answer:** select DISTINCT payment_method, count(DISTINCT order_id) from orders GROUP BY payment_method HAVING count(DISTINCT order_id)>4;

**Q14.** Which customers placed more than 1 order? Return customer_id
and their order count.  
**Answer:** select DISTINCT customer_id,order_id, count(DISTINCT order_id) from orders GROUP BY customer_id HAVING count(DISTINCT order_id)>1;

---

## SECTION 4 — Real Revenue Calculations (combining tables + aggregates)

This is where SQL starts doing something Excel genuinely struggled
with — calculating revenue that depends on TWO different tables at
once (order_items has quantity, products has price), without you
manually building a lookup column first.

**You'll need a JOIN here** — one line, don't worry about mastering
it yet, Week 11 covers this properly:
```sql
FROM order_items oi
JOIN products p ON oi.product_id = p.product_id
```
This just temporarily glues the two tables together so quantity and
unit_price sit in the same row, letting you multiply them.

---

**Q15.** Calculate total revenue (quantity × unit_price) for each order_id.  
**Answer:** select DISTINCT order_id, SUM(quantity * unit_price) AS Total_Revenue from order_items oi JOIN products p ON oi.product_id = p.product_id GROUP BY order_id;

**Q16.** Calculate total revenue for each product category, sorted
highest to lowest.  
**Answer:** select DISTINCT category, SUM(quantity * unit_price) from order_items oi JOIN products p ON oi.product_id = p.product_id GROUP BY category ORDER BY SUM(quantity * unit_price) desc;

**Q17.** Which product categories generated more than 1000 in total revenue?  
**Answer:** select DISTINCT category, SUM(quantity * unit_price) from order_items oi JOIN products p ON oi.product_id = p.product_id GROUP BY category HAVING SUM(quantity * unit_price)>1000;


---


---

## VERIFIED ANSWERS

| Q# | Expected Result |
|---|---|
| Q1 | 10 |
| Q2 | 10 |
| Q3 | 617.5 |
| Q4 | 1495 |
| Q5 | 42 |
| Q6 | East=3, North=2, South=2, West=3 |
| Q7 | Beauty=83.5, Clothing=84, Electronics=1132.33, Home Appliances=474, Sports=1495 |
| Q8 | Budget=3, Premium=3, Standard=4 |
| Q9 | Credit Card=7, Debit Card=4, PayPal=4 |
| Q10 | product_id 8 sold the most (6 units total) |
| Q11 | Electronics (1132.33), Sports (1495) |
| Q12 | East (3), West (3) |
| Q13 | Credit Card (7) |
| Q14 | customer_id 1 (3 orders), 2 (2), 3 (2), 5 (2) |
| Q15 | Order 101=1083, 106=1299, 112=1495, 114=1495... 15 orders total |
| Q16 | Electronics=6694, Sports=2990, Home Appliances=1497, Clothing=603, Beauty=502 |
| Q17 | Electronics, Home Appliances, Sports |

---

*After completing all questions, give the same set to AI and document
findings in Week10_AI_Audit.md*
