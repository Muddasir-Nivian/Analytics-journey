# Week Notes - Month 03 SQL

## Week 9 — SQL Basics: SELECT, WHERE, ORDER BY, DISTINCT, LIMIT
**Date:** September 2026
**Focus:** Querying a real relational database for the first time

**What I built:**
Set up a 4-table SQLite database customers, products, orders,
order_items connected through foreign keys. Completed 25 questions
across SELECT, WHERE with AND/OR, ORDER BY, DISTINCT, and LIMIT,
building up to real business questions combining multiple keywords
in one query.  
To access the Week 9 workbook [click here](./Work%20Files/Week9_SQL_Challenges.md/)

**What clicked:**
Honestly, nothing felt new. Every logic here filtering with WHERE,
combining conditions with AND/OR, sorting with ORDER BY, removing
duplicates with DISTINCT is logic I already built in Excel through
IF, COUNTIF, and Sort. SQL this week was the same thinking wearing
different syntax, not a new way of thinking.


**Confidence:** 4.8/5

**Carrying into Week 10:**
The instinct that querying two tables together requires explicitly
telling SQL how they relate — not just placing them side by side and
hoping the filter does the work.

## Week 10 — Aggregate Functions, GROUP BY, HAVING
**Date:** September 2026
**Focus:** Grouping data and filtering on aggregated results

**What I built:**
Completed 17 questions across plain aggregates (COUNT, AVG, MAX, MIN),
GROUP BY splitting data into buckets, HAVING filtering group results,
and revenue calculations joining order_items with products.  
To access the Week 10 workbook [click here](./Work%20Files/Month-3%20Week-10%20Practice%20File.md/)

**What clicked:**
GROUP BY with HAVING is efficient for putting conditions directly on
grouped results — filtering a summary after it's built, not the raw
rows before.

**Confidence:** 4.5/5

## Week 11 — JOINs and Subqueries
**Date:** September 2026
**Focus:** Connecting multiple tables and filtering with subqueries

**What I built:**
Completed 10 questions across INNER JOIN, LEFT JOIN, RIGHT JOIN,
FULL JOIN, subqueries with IN, and multi-table chains connecting
4 tables in one query. Added Karen White and Yeti Cooler to the
database specifically to give LEFT and RIGHT JOIN something
meaningful to show — a customer who never ordered and a product
that was never sold.  
To access the Week 11 workbook [click here](./Work%20Files/Week11_SQL_Challenges%20(1).md/)

**What clicked:**
LEFT JOIN is useful for extracting and compiling data across
multiple tables into one result, including rows that have no match
on the other side — the ones INNER JOIN would silently drop.
Multi-table chains connecting 4 tables in sequence give bigger
queries more result accuracy because every link uses the right
connecting column, and nothing gets paired with the wrong rows.

**The connection back to Week 9:**
The Q23 bug in Week 9 — where every customer got paired with every
order because there was no connecting condition — was exactly the
problem JOIN formally solves. Writing the fix as a WHERE condition
that week was already a JOIN in everything but name.

**Confidence:** 4.5/5
