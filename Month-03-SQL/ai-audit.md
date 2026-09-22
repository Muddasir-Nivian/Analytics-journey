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
