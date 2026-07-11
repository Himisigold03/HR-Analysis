# HR Data Analysis: Attrition, Salary & Employee Trends

## Introduction
This capstone project is an HR data analysis that shows trends across years, attrition rate, salaries, employment status, and other relevant information about employees.

**Aim:** My aim is to analyze this data and generate actionable insights through storytelling visuals.

**Tools used:** Microsoft Excel (data cleaning, formulas, pivot tables, dashboard)

## Methodology
1. Data Exploration
2. Data Cleaning
3. Insights Generation
4. Dashboard

## Data Exploration
The data was messy, consisting of inconsistencies and formatting issues that were not palatable for analysis. It initially consisted of 8 columns and 158 rows (including the header), and contained missing values and misspelled words that made analysis difficult.
<img width="561" height="266" alt="Raw data" src="https://github.com/user-attachments/assets/c657bb5a-e449-41c1-88a9-d07b5a59b153" />


## Data Cleaning Process
1. Checked the quality of the data to understand how messy it was.
2. Removed duplicates to avoid bias in the analysis.
3. Used filters to identify blank cells in each column.
4. Used Find & Replace to correct misspelled words and maintain consistency, especially in the Employment Status column.
5. Used `TRIM` and `PROPER` formulas to remove unwanted spaces and standardize text formatting.
6. Merged the first and last names to create a Full Name column, using flash fill/autofill.
7. Used `TRIM` to eliminate leading/trailing spaces in cells.
8. Handled missing Performance Score values:
   `=IF(ISBLANK(H2), AVERAGE($H$2:$H$158), H2)`
9. Handled missing Salary values:
   `=IF(ISBLANK(K2), AVERAGE($K$2:$K$158), K2)`
10. Calculated the average salary using `=AVERAGE(G2:G158)` and used `IFERROR` to replace errors:
    `=IFERROR(K2, 82713)` — done in a helper column, then pasted as values into the original column.
11. Converted all Performance Score values to whole numbers, since the calculated averages were in decimals.
12. Corrected improperly named columns (e.g., "Dept Code" → "Department Code", "Perf Score" → "Performance Score").
13. Standardized the Date column using Data → Text to Columns, converting text to a proper date format for consistency.
14. Replaced missing First Name values with the most frequently occurring first name (since missing values were about 20% of the column), and replaced missing numerical values with their column mean.
15. Created a Department column using `VLOOKUP`:
    `=VLOOKUP(W2, lookup_department!$A$1:$B$7, 2, FALSE)`
16. Used `VLOOKUP` with an approximate match to find performance score ranges and bonus tiers:
    `=VLOOKUP(H2, lookup_department!$A$1:$D$6, 3, TRUE)`
    `=VLOOKUP(H2, lookup_department!$A$1:$D$6, 4, TRUE)`
17. Bonus values were also derived using `VLOOKUP` (approximate match, based on performance score ranges).
18. Calculated Years of Service by extracting the year from the Hire Date and subtracting it from the current year.
19. Structured the cleaned data into a table, ready for analysis.
20. Final dataset: 151 rows and 13 columns, including the header.
<img width="569" height="225" alt="HR Data" src="https://github.com/user-attachments/assets/2c24f46f-179d-4676-bea6-3167ebc6d264" />

## Insights Generation
- **Total employees:** 150
- **Total Salary:** $12,451,486
- **Average salary:** $83,010 per person
- **Total attrition rate:** 23% (16% terminated, 7% resigned)
- The **Information Technology** department has the highest total salary spend among all departments, at $3,042,552 — the sum of salaries paid to all employees within that department.
- Bonuses were not given to employees with a performance score below 49 — meaning bonus eligibility is tied directly to performance, leaving room for improvement among lower scorers.
- Comparing average performance score with employment status: employees who **resigned** had the highest average performance score, and the average score of those who **left** was close to that of **active** employees. This suggests attrition was **not** primarily driven by performance.
<img width="567" height="262" alt="HR anlysis" src="https://github.com/user-attachments/assets/e3019925-759e-4f64-a15c-4d62bd237705" />

## Dashboard
<img width="886" height="513" alt="image" src="https://github.com/user-attachments/assets/b40b6f61-1dbb-4b93-86bc-731fd77ea6c2" />






## Recommendations
- Investigate the underlying reasons for attrition further, since performance does not appear to be the driving factor. Exit interviews or engagement surveys could help surface causes such as compensation, work-life balance, or career growth opportunities.
- Encourage employees with low performance scores through mentorship, training, and clear improvement plans, so they can grow and become eligible for bonuses.
- Given the Information Technology department's high salary spend, review compensation structure and retention strategy for that department specifically, to ensure the investment translates into retention and output.

## Conclusion
This project goes beyond surface-level numbers — it's an exploration of the human story behind the data. The findings show that attrition at this organization isn't a performance problem; it's likely tied to factors the current dataset doesn't fully capture, such as compensation satisfaction, career development, or workplace culture. This reframes the conversation for decision-makers: rather than focusing retention efforts on performance management alone, the organization should dig deeper into the qualitative "why" behind employees leaving. Data cleaning and analysis are only the starting point — the real value lies in asking the right questions the data reveals.
