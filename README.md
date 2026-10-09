# Task 1 — Inconsistencies and duplicates

**Name:** Ghaydaa Medhat Mohamed Amer
**ID:** 58-5281
**Major:** IET

## Cleaning explanation

I started with 39 rows. Faculty, club and city were written many ways (`Pharma`, `Alex`, `El Giza`, `Debating`, `Chess Club`, `Soccer`, full faculty names), so I stripped, lower-cased and collapsed spaces, then used explicit dictionaries (Media Engineering and Technology → MET, Soccer → Football) and asserted only canonical values remain. Names had extra spaces and mixed capitalisation, so I collapsed spaces and used title case; emails were trimmed and lower-cased. `fee_paid` (yes/Y/TRUE/1/no/N/false/0) was mapped to a real boolean column. `signed_up_at` mixed ISO (`YYYY-MM-DD`, 25 rows) and slash dates (14 rows); the slash ones are day-first because the first number reaches 18, so I parsed each format separately into one datetime column. Removing 3 exact duplicate submissions left 36 rows, and keeping one row per student_id and club removed 4 more, leaving 32. I kept the latest submission because students came back to update their fee status, so the later row is the current truth. Order matters: on the raw data, after the exact duplicates, only 2 student+club duplicates are found instead of 4, because `Chess` vs `Chess Club`, `Debate` vs `Debating` and `Football` vs `Soccer` look like different clubs, so 2 stale rows would survive. Two different students share a name (Mohamed Adel, 61-4844 and 55-2992), so I matched on student_id and club, never on name, and both are kept.
