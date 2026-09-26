## Week 10 Audit — Aggregate Functions, GROUP BY, HAVING
**Date:** September 2026

**Task given to AI:**
Give AI the business questions in plain English — do not mention
GROUP BY or HAVING by name. See whether AI correctly identifies when
grouping is needed versus when a plain aggregate is enough, and
whether it reaches for HAVING instead of WHERE when filtering a
group result.

---

**AUDIT 1 — Plain aggregate (no grouping needed)**

Task given to AI: How many total customers does Vantree have?

Exact query AI produced: SELECT COUNT(*) AS total_customers
FROM customers;

Was AI correct? Yes / No / Partially: Yes

What was wrong or missing: Nothing

Error type: Wrong function / Wrong column / Unnecessary GROUP BY / Syntax / Logic: Nothing

How I caught it: Running the query on SQL editor

What this taught me: Ai knows the aggregate fuctions very well

---

**AUDIT 2 — GROUP BY**

Task given to AI: How many customers are in each region? Return region and the count.

Exact query AI produced: SELECT region, COUNT(*) AS customer_count
FROM customers
GROUP BY region;

Was AI correct? Yes / No / Partially: Yes

What was wrong or missing: Nothing

Error type: Wrong function / Wrong column / Missing GROUP BY column / Syntax / Logic: Nothing

How I caught it: Running the query on SQL editor

What this taught me: Ai can add GROUP BY with following the syntax protocol

---

**AUDIT 3 — WHERE vs HAVING (the critical test)**

Task given to AI:
Describe a task that requires filtering a GROUP result — like "which
regions have more than 2 customers" — without saying the word HAVING.
See if AI correctly uses HAVING instead of incorrectly trying WHERE
on an aggregate.

Exact query AI produced: SELECT category, AVG(unit_price) AS avg_unit_price
FROM products
GROUP BY category
HAVING AVG(unit_price) > 500;

Was AI correct? Yes / No / Partially: Yes

What was wrong or missing: Nothing

Error type: Used WHERE instead of HAVING / Wrong column / Syntax / Logic: Nothing

How I caught it: Running the query on SQL editor

What this taught me: Ai names the aggregate columns by itself to keep it perfect and recognizable

---

**AUDIT 4 — Revenue calculation across two tables**

Task given to AI:
"Calculate total revenue for each product category." (Requires
combining order_items and products — quantity lives in one table,
price lives in the other.)

Exact query AI produced: SELECT oi.order_id, SUM(oi.quantity * p.unit_price) AS total_revenue
FROM order_items oi
JOIN products p ON oi.product_id = p.product_id
GROUP BY oi.order_id;

Was AI correct? Yes / No / Partially: Yes

What was wrong or missing: Nothing

Error type: Wrong join / Wrong aggregate / Wrong grouping column / Syntax / Logic: Nothing

How I caught it: Running the query on SQL editor

What this taught me: Ai is pretty fast on JOIN where i would spend X amount of time on JOIN before learning it Ai can write a JOIN query in 5X less time than me

---

## WEEKLY SUMMARY

Overall AI accuracy this week: 4 out of 4 tested correctly

Did AI correctly distinguish WHERE from HAVING without being told
the keyword? This is the single most important check this week. Yes

Pattern observed in errors (if any): Not in error but in queries that ai names the aggregate columns by itself to keep the output clean and recognizable

Most important finding: Nothing

Lesson carrying into Week 11 (JOINs): Joins can make the work way more easy by connecting the query's logic accross multiple tables
