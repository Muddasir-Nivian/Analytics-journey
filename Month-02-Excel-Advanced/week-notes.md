# Week Notes - Month 02 Excel Advanced

---

## Week 5 — SUMIFS, COUNTIFS, XLOOKUP
**Date:** August 2026
**Focus:** Multi-condition formulas and modern lookup

**What I studied:**
SUMIFS sums numbers based on multiple conditions, either across
columns or within a column.  
COUNTIFS counts cells based on
multiple conditions, same flexibility as SUMIFS.  
XLOOKUP essentially VLOOKUP and HLOOKUP combined into one function.

**What I built:**
Completed SUMIFS practice across two condition and three condition
business scenarios.  
To access week 5 excel file [Click Here](./Work%20files/Month2%20Week5%20Practice.xlsx/)  
Completed COUNTIFS practice including combining
it with IF for business flagging. Tested XLOOKUP directly in Excel
comparing it against VLOOKUP with IFERROR and INDEX MATCH.

**What clicked:**
XLOOKUP can search both horizontally and vertically, unlike VLOOKUP
which only searches vertically. XLOOKUP also has built-in error
handling that separates it from both VLOOKUP and INDEX MATCH 
no need to wrap it in IFERROR separately.

**Looking back at earlier practice:**
Revisiting a Week 2 project where I was manually filtering data row
by row to find answers,  
SUMIFS and COUNTIFS made the exact same
questions solvable in a single formula. A clear reminder of how
much easier each new tool makes the work that used to take
significant manual effort.

**What I'd revisit:**
Want to go deeper with XLOOKUP specifically with real scenarios
to build fluency beyond the basic comparison tasks.

**Confidence:** 4.8/5

## Week 6 — Combo Charts, Histograms, Trendlines, KPI Deep Dive
**Date:** August 2026
**Focus:** Advanced chart types and KPI classification systems

**What I studied:**
Combo charts combining two metrics with different scales on
primary and secondary axes. Histograms showing distribution of a
single number rather than comparison across categories. Trendlines
with linear regression, equations, and R-squared values. A deeper
KPI framework classifying metrics as Vanity, Diagnostic, or
Actionable.

**What I built:**
Built a combo chart comparing monthly revenue against order count.
Built two histograms and revenue distribution and units sold
distribution and interpreted the shape of both. Added a
trendline to the monthly revenue trend with equation and R-squared
displayed. Reclassified all 8 KPIs from Week 4 using the Vanity,
Diagnostic, Actionable framework.  
To access week 6 excel file [Click Here](./Work%20files/Month2%20Week6%20Practice%20(1).xlsx/)

**What I actually learned — not just completed:**
KPIs carry different types that show what to focus on in a
presentation. Vanity is just a number that does not diagnose
anything or direct any action. Diagnostic shows why something
happened the reasoning behind another metric. Actionable directs
a specific action, whether for growth, improvement, diagnosis, or
analysis.

**Creative thinking on the KPI framework:**
I treated the KPIs as a real life scenario and asked myself — what
if a KPI I am calling Vanity is actually the reason behind a bigger
change, or what if it needs to exist just to make a Diagnostic KPI
make logical sense on the dashboard? Thinking as the CEO, I realized
any KPI I initially label Vanity could still lead to an action, so
it cannot always be purely Vanity. That is why I mixed classifications
for some KPIs instead of forcing them into one rigid category.

**AI Audit highlight:**
Caught AI classifying Total Revenue as pure Vanity when it is
actually a mix of Vanity and Actionable depending on context.
Theorized that AI checks classification options in sequence and
stops at the first valid match rather than evaluating all
possibilities before choosing.

**Confidence:** 5/5

## Week 7 — Data Cleaning, Text Functions, Duplicate Removal
**Date:** August 2026
**Focus:** Cleaning messy real world text data

**What I studied:**
TRIM, PROPER, LOWER, UPPER, LEFT, RIGHT, MID, FIND, and SUBSTITUTE.
Also duplicate detection using COUNTIFS before using Excel's built-in
Remove Duplicates tool.

**What I built:**
Cleaned a deliberately messy customer feedback dataset, trimmed and
properly capitalized names, standardized emails, split combined
fields like Region-Store Code and Product Code + Name into separate
columns, and standardized phone numbers written in three different
formats. Flagged duplicate entries with COUNTIFS before removing
them, to see exactly what would be deleted before committing to it.

**What clicked:**
TRIM only removes extra spaces. SUBSTITUTE can replace any value
with whatever you want to change it to. That distinction is the
difference between cleaning up spacing and actually rewriting
content.

**A question that came up mid-practice:**
If Excel can handle almost every business scenario I imagined, why
learn SQL and Power BI at all? The answer Excel is mostly used for
cleaning and formatting, and if the dataset is not too large, the
analysis itself can be done in Excel too. But scale, automation, and
multi-user access are where Excel's limits show up, which is where
SQL and Power BI take over.

**AI Audit highlight:**
Caught AI nesting FIND directly inside LEFT's argument instead of
splitting it into two separate steps. What made this audit
worthwhile was that AI found a genuinely smarter, more dynamic
mathematical approach to the same problem not just a different
way of writing the same logic, but a better one. Simpler tasks in
the same audit had nothing to dig into, since there was no
intellectual ground to cover beyond the one obvious correct answer.

**Confidence:** 4.9/5
