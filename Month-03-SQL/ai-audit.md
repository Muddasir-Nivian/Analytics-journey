# AI Audit Log — Month 03 SQL

---

## Week 9 Audit — SELECT, WHERE, ORDER BY, DISTINCT, LIMIT
**Date:** September 2026

**Task given to AI:** Given the same 25 business questions in plain
English, with no SQL keywords specified, letting AI decide syntax
the way a real business user would describe a data need without
knowing the underlying query language.

**Results:**
AI answered all 4 tested questions correctly across basic SELECT,
WHERE with region filtering, ORDER BY on price, and a real business
question asking for January Credit Card orders. Every query matched
my own verified answers.

The one genuine difference showed up on the January orders question.
I solved it by manually finding the first and last date in January
and using >= and <= to bound the range. AI used LIKE '2026-01%' to
match the date pattern directly. Both returned identical results
against this dataset, but for a different reason — my version only
worked because no January order happened to fall outside the specific
range I picked. AI's version would still work correctly no matter
which days in January had orders, because it matches the pattern
itself rather than assuming where the range starts and ends.  
To access Week 9 ai audit file [Click here](./Work%20Files/Week9_AI_Audit%20(1).md/)

**Error type:**
Not applicable, AI was correct on every tested question. The finding
this week was about approach, not error: two different paths reaching
the same answer, one more fragile than the other.

**Why this matters:**
AI can take a different approach than mine while still keeping focus
on the exact data the question needs. A correct answer today does not
always mean the same approach stays correct tomorrow, my manual date
range only worked because of what this specific dataset happened to
contain, not because the logic itself was sound for any dataset.

**Lesson:**
AI can give you what you need, but the approach behind it can be
more resilient than yours even when both produce the same result
right now. Worth checking not just whether an answer matches, but
whether the method behind it would still hold up if the data changed.

---

## Week 10 Audit — Aggregate Functions, GROUP BY, HAVING
**Date:** September 2026

**Task given to AI:** Business questions given in plain English, with
GROUP BY and HAVING never named directly — testing whether AI reaches
for HAVING instead of WHERE when a task requires filtering a grouped
result, and whether it correctly identifies the right column to
group by.

**Results:**
AI got the aggregate function, the GROUP BY, and the WHERE-versus-
HAVING distinction correct across every test. Asked to find categories
with an average price above 500 without ever saying the word HAVING,
AI correctly used HAVING rather than incorrectly trying WHERE on an
aggregate — the one thing this week's audit was built specifically to
check.  
To access Week 10 ai audit file [click here](./Work%20Files/Week10_AI_Audit%20(1).md/)

**Lesson:**
Auditing AI on aggregate queries means checking not just whether the
SUM or JOIN is correct, but whether the GROUP BY column actually
matches the question being asked. A wrong grouping column is one of
the quietest possible errors — the query runs, the numbers look real,
and it takes a real comparison against the original ask to catch it.

---

## Week 11 Audit — JOINs and Subqueries
**Date:** September 2026

**Task given to AI:** Business questions given in plain English with
no JOIN type named, testing whether AI correctly picks INNER vs LEFT
based on what the question actually needed.

**Results:**
AI got all four correctly. The findings this week were not about
errors but about additions AI made without being asked.

For INNER JOIN, AI added ORDER BY at the end without being asked.
The result was the same without it. AI structured the output even
when the task did not require it.

For LEFT JOIN, the task only asked for customer_name but AI also
returned customer_id alongside it. Same pattern. AI added a column
to keep the result more structured and recognizable, beyond what was
asked for.

For the subquery versus JOIN comparison, AI correctly reached for a
subquery with IN when the task was framed as a simple membership
check, and reached for INNER JOIN when the task needed data from
multiple columns across both tables. Right tool for each framing.

For the 4-table chain, AI wrote the full chain correctly.
customers, orders, order_items, products — with the right ON
conditions at every link, correct GROUP BY, and correct aggregate.
No wrong column, no missing table, no grouping mismatch.  
To access week 11 ai audit file [click here](./Work%20Files/Week11_AI_Audit%20(2).md/)

**Error type:**
Not applicable — no errors found this week. The pattern was
additions, not mistakes.

**Why this matters:**
AI consistently added structure beyond what was asked — an ORDER BY,
an extra column — without breaking anything. These additions are
worth checking before moving to the next step, not because they
cause errors but because they can quietly change what the output
looks like and create confusion if the extra column or sorting was
not intended.

**Lesson:**
JOINs are fast and easy for AI — faster than a human who is still
building the logic and syntax from scratch. The audit value this
week shifted from catching wrong answers to noticing uninstructed
additions that come standard with AI output whether you asked for
them or not.
