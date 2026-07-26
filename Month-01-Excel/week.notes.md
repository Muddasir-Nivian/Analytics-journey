# Week Notes - Month 01 Excel Fundamentals

----

## Week 1 - Basic Formulas
**Date:** July 2026
**Focus:** SUM, AVERAGE, COUNT, MAX, MIN

**What I studied:**
Rows, Columns, Basic Formatting.
Five core aggregation formulas
practiced on a real retail sales
dataset with 25 transactions.

**What I Built**
Practice workbook with 8 business questions
answered using real sales data.
Two Tabs - Sales, Practice week 1.

**What I realized**
I realized that the Formulas like 
SUM, AVERAGE, COUNT, MIN, MAX are now 
pretty easy for AI to execute so Understanding
the formulas's core, How they Works, Logic and Real use
is important than memorizing Syntaxes.

**Confidence:** 5/5

## Week 2 - IF AND OR, Data Validation, Dropdowns, Charts and Storytelling  
**Date:** July 2026
**Focus:** Conditional logic, data restriction, and visual storytelling

**What I studied:**  IF formula and its family AND, OR, IFS, Nested IF. Data Validation and Dropdowns restricting what can be entered in a dataset.
Sort and Filter for navigating large data.
Basic charts and the logic of which audience.

**What I Built:**
Practice IF AND OR formulas across 13 questions including two real business challenges questions combining OR inside AND without hints or tutorial.
Built data validation rules with dropdowns lists, number range restrictions, date vaildation, and custom error messages.

**What took longest to click:**
AND inside IF. The logic of multiple conditions that must all be true simultaneously took more brain processing than OR or Basic IF.
Once I understood that AND is strict every condition must pass and OR is generous any one condition passing is enough the formulas started feeling natural.

**What was geniunely difficult:**
Combining multiple logics and formulas inside IF simultaneously.
Nesting COUNTIF inside IF, ISBLANK inside IF, ISNUMBER inside IF each combination requires the brain to hold multiple logical layers at once.
Difficult but genuinely enjoyable once it started working.

**What clicked most:**
IF formula is the foundation of almost every business condition.
Most real analysis requires custom conditions - flag this, validate that, compare these.
IF is the tool that executes those conditions at scale.
Data Validation is the companion that prevents the wrong data from entering in the first place.

**The biggest realization of the week:**
Storytelling matters more than I expected. If you cannot deliver an accurate story in the right way it will not land with the listener.
the analysis loses almost all its impact no matter how technically correct it is. The insight is only as valuable as the clarity with which it is communicated.

**Confidence:** 4/5
Strong on IF logic and data validaton. Chart selection and storytelling need more practice with real data accross different business scenarios.

## Week 3 - VLOOKUP, HLOOKUP, INDEX, MATCH  
**Date:** July 2026  
**Focus:** Lookup Formulas - finding and retrieving data across tables

**What I studied:**
VLOOKUP - looks vertically in a given column and returns the value from the intersecting row.  
Hlookup - looks horizontally in a given row and returns the value from the intersecting column number.  
INDEX - retrieves a value by validating a given row and column number.  
MATCH - validates whether a given value exists in an array and it works as the row number in INDEX.

**What I built:**
Completed VLOOKUP practice across three sections including basic lookup, IFERROR error handling and a real business order form that auto fills product details from a master table.  
Completed HLOOKUP practice on regional sales targets including IF combined with HLOOKUP to determine which cities hit their target sales.  
Completed INDEX MATCH practice returning employee salary and performance by name including finding the highest earning employee using MAX.  
Completed all four challenge questions combining VLOOKUP, HLOOKUP, INDEX MATCH and nested IF together.

**What caused most confusion:**
Not mistake in formula syntax but confusion with the logic of the task itself.  
Understanding what the data meant and what comparison was actually required took two or three attempts before the logic clicked.  
Once the task logic was clear the formula followed naturally.

**Key distinctions learned:**
INDEX MATCH can return values to the left of the search column. LOOKUP cannot.  
This makes INDEX MATCH the more flexible and professional choice for complex lookups.

**Bug caught and understood:**
IFS evaluates conditions in sequence and stops at the first match.  
Let's say you entered three logics so it will check whether the value intersect with the first logic if not then it will go for the second logic if by any chance the second logic intersect with the value IFS will return it as the true without checking that the third logic also intersects with the value.

**Confidence:** 4.3/5
