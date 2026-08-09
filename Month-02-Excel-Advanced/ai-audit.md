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
