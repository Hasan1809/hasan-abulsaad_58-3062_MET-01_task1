# Task 1: Club Signups Cleaning

## Files

- `task_1.ipynb`: pandas notebook containing the full cleaning workflow.
- `club_signups.csv`: original raw data, left unchanged.
- `club_signups_clean.csv`: final cleaned output.

## Cleaning Explanation

I first profiled the raw `club_signups.csv` before making changes, checking its shape, dtypes, nulls, category counts, date formats, and key uniqueness. The file started with 39 rows and had inconsistent faculty, city, and club spellings, messy name capitalization and spacing, mixed-case emails, text values for `fee_paid`, mixed date formats, exact duplicate rows, and repeated same-student same-club signups. I kept the raw dataframe unchanged and cleaned a copy. The workflow was: standardize column names, clean names and emails, map faculty/city/club variants to canonical values, convert `fee_paid` to booleans, parse `signed_up_at` as datetime, remove exact duplicates, then remove repeated `student_id + club` signups. I mapped values such as `Media Engineering and Technology` to `MET`, `Soccer` to `Football`, and `El Giza` to `Giza`. I removed 3 exact duplicates, leaving 36 rows, then removed 4 repeated same-club signups by keeping the latest submission because later rows usually updated the fee status from unpaid to paid. The final table has 32 rows. If repeated signups were removed before fixing club spellings, only 2 would be found and 34 rows would remain. I avoided merging by name because two students are named Mohamed Adel; duplicates were identified using `student_id + club`, not `full_name`.
