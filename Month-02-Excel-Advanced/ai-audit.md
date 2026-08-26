# AI Audit Log — Month 02 Excel Advanced

---

## Week 5 Audit — SUMIFS, COUNTIFS, XLOOKUP
**Date:** August 2026

**Task given to AI:** Solve four business questions using SUMIFS,
COUNTIFS, and a VLOOKUP vs XLOOKUP comparison all tested directly
inside the Excel file with AI having access to the actual table.

**Results:**
AI answered 3 out of 4 correctly with no issues two SUMIFS
questions and one COUNTIFS business flagging question all produced
accurate formulas on the first attempt. The fourth, comparing
VLOOKUP against XLOOKUP for the same lookup, is where the finding
gets interesting.

AI's VLOOKUP formula selected a range starting one column earlier
than the actual lookup column. Technically this means the formula
was searching the wrong column for the lookup value. However,
since the specific value being searched for did not exist anywhere
in the dataset, both the flawed VLOOKUP and the correctly built
XLOOKUP returned the same Not Found result so the error was
invisible in this specific test.

**Error type:**
Range the VLOOKUP table array did not start at the correct
column for the lookup value, though the output was not affected
in this particular case.

**Why this matters:**
AI performs noticeably more reliably when it has direct access to
the actual Excel file rather than working from a described table.
But a correct-looking result does not always mean a correct
formula. This week's finding showed that a formula can have a
structural range issue and still return the right answer purely
by coincidence of the test data used — a different lookup value
that actually existed in the dataset could have exposed the same
flaw as a wrong result instead of a harmless one.

**Lesson:**
Passing a single test case is not proof a formula is correct.
Auditing AI output means checking the formula's logic itself, not
just whether the number that came back looks reasonable. A bug
that does not surface on one input can still surface on the next.


## Week 6 Audit — Combo Charts, Histograms, Trendlines, KPI Classification
**Date:** August 2026

**Task given to AI:** Build the combo chart, choose histogram bin
width, interpret the trendline's R-squared value, and classify all
8 Week 4 KPIs as Vanity, Diagnostic, or Actionable.

**Results:**
Combo chart and histogram bin width were both correct with nothing
significant to flag.

The R-squared interpretation was where the first real issue showed
up. AI stated the trend was "STATISTICALLY SIGNIFICANT" based on a
p-value of 0.0190 from only 6 months of data. Confidently labeling
a 6-point dataset as statistically significant is the kind of claim
that sounds authoritative but does not hold up to scrutiny a
sample that small makes any significance test fragile, and a real
analyst should question that confidence before repeating it to a
CEO.

The clearest finding came from the KPI classification task. AI
classified Total Revenue as pure Vanity, reasoning that it is a
lagging indicator that does not explain why revenue moved. My own
classification was a mix of Vanity and Actionable, since Total
Revenue can still drive real decisions depending on business
context. AI and I reached opposite conclusions on the exact same
question.

**Error type:**
Business judgment and conceptual

**Why this error happened:**
As I gave AI options in series like Vanity, Diagnostic and
Actionable it first checked for Vanity as Vanity was valid on KPI
type, it confirmed and considered it as the only answer without
checking whether another option can also be valid if checked
further. Once it finds any option valid it doesn't move further
and declares the first valid condition met as true.

**How I caught it:**
Comparing the answer with business and analysis logic.

**Lesson:**
An AI answer that is technically correct is not the same as an
answer that reflects real business judgment. Auditing AI output on
subjective classification tasks requires imagining the downstream
consequences of the answer, not just checking whether it followed
the instructions.

# AI Audit Log — Month 02 Excel Advanced

---

## Week 7 Audit — Text Functions and Duplicate Detection
**Date:** August 2026

**Task given to AI:** Clean the Region-Store Code split, split
Product Code and Name, standardize phone numbers, and remove
duplicates from the customer feedback dataset.

**Results:**
Two tasks splitting Region-Store Code and Product Code/Name
produced the strongest findings of the week. AI nested FIND
directly inside LEFT's num_chars argument rather than writing it
as two separate formulas the way I did. For the product split, it
used LEN(A2) as a self-referencing "return everything remaining"
trick instead of a hardcoded number. Both approaches were valid,
and both revealed something real: AI does not default to the most
obvious step-by-step logic — it finds dynamic mathematical
shortcuts that solve the problem more efficiently, working off
possibilities rather than copying the exact method I would have
used.

The phone number standardization task surfaced a genuine knowledge
gap AI used TEXT(VALUE(...), "000-000-0000") to reformat digits
into a standard pattern, a function combination I had not learned
yet and could not fully evaluate at the time.

The two simplest tasks basic name cleaning and the plain "remove
duplicates" instruction with no further specification had nothing
meaningful to audit. The tasks were basic enough that only one
correct answer existed, leaving no real decision for AI to make
differently or better.

**Error type:**
Not applicable for the strong findings, AI was correct, just
structured differently. The weak audits had no error to identify,
which is itself worth noting as a limitation of testing AI on
tasks with only one possible right answer.

**Why this matters:**
The clearest signal this week was that auditing AI is only valuable
when the task has room for multiple valid approaches. When AI finds
a smarter path than the one I would have written, that is worth
understanding and learning from not just confirming the output
matched. When a task is too simple to have more than one correct
answer, there is nothing left to audit beyond correctness itself.

**Lesson:**
The real skill this week was not catching AI being wrong. It was
recognizing when AI found a better, more dynamic solution than my
own and being honest enough to learn from it instead of just
checking whether the final number matched.
