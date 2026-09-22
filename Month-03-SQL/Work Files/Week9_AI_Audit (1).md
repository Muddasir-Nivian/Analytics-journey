AI Audit Log — Month 03 SQL

---

Week 9 Audit — SELECT, WHERE, ORDER BY, DISTINCT, LIMIT
Date: September 2026

**Task given to AI:**
Give AI the same business questions from Week9_SQL_Challenges.md.
Do NOT tell AI which SQL keywords to use — describe the business
question in plain English and let AI decide the syntax, the same way
a real business user would describe a data need to an analyst.

---

**AUDIT 1 — Basic SELECT and WHERE**

Task given to AI: Q1. Return every column from the customers table

Exact query AI produced: SELECT * FROM customers;

Was AI correct? Yes / No / Partially: Yes

What was wrong or missing: Nothing

Error type: Wrong column / Wrong table / Wrong operator / Syntax / Logic: Nothing

How I caught it: Comparing to my answer

What this taught me: ai can immediately run SELECT queries if tables structure is given to it

---

**AUDIT 2 — WHERE with AND / OR**

Task given to AI: Q5. Return the names of all customers in the North region.

Exact query AI produced: SELECT customer_name FROM customers WHERE region = 'North';

Was AI correct? Yes / No / Partially: Yes

What was wrong or missing: Nothing

Error type: Wrong column / Wrong table / Wrong operator / Syntax / Logic: Nothing

How I caught it: Comparing to my answer

What this taught me: ai is pretty good at WHERE logic along with the operators

---

**AUDIT 3 — ORDER BY**

Task given to AI: Q13. Return all products sorted by unit_price from cheapest to most expensive.

Exact query AI produced: SELECT * FROM products ORDER BY unit_price ASC;

Was AI correct? Yes / No / Partially: Yes

What was wrong or missing: Nothing

Error type: Wrong column / Wrong table / Wrong operator / Syntax / Logic: Nothing

How I caught it: Comparing to my answer

What this taught me: ai can perform ORDER BY on basic tasks easily not sure about complex queries with ORDER BY

---

**AUDIT 4 — Real Business Question (Q25 — January Credit Card orders)**

Task given to AI:
"Show me every order placed in January 2026 that was paid by Credit Card.
I need the order ID and the date."

Exact query AI produced: SELECT order_id, order_date FROM orders WHERE payment_method = 'Credit Card' AND order_date LIKE '2026-01%';

Was AI correct? Yes / No / Partially: Yes

What was wrong or missing: Not wrong but ai used different approach than mine ai used LIKE in Q25
where i used manuall finding while first finding the end date of January then first date then setting manuall '<','>' logic with first and last date with AND 

Error type: Wrong column / Wrong table / Wrong operator / Syntax / Logic: Syntax and approach not wrong but different than mine

How I caught it: Comparing to mine and by understanding the logic of LIKE in query

What this taught me: ai can take different approaches while keeping the focus one data that need and its center point at the same time

---

## WEEKLY SUMMARY

Overall AI accuracy this week: 4 out of 4 tested correctly

Pattern observed in errors (if any): Not error but approach while keeping the focus on the center point at the same time

Most important finding: Q25 

Lesson carrying into Week 10: ai can give you what you need but the approach can be different.
