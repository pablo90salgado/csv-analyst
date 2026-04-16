---
name: csv-analyst
description: |
  Analyzes, cleans and describes CSV files and tabular data.
  Use this skill when the user says: "analyze this CSV", "what is in this file",
  "clean the data", "find outliers", "describe the columns", "how many nulls",
  "process this spreadsheet", "summarize this dataset", "data quality check",
  "what columns do I have", "find duplicates", "data profiling". Detects data types,
  null values, duplicates and statistical anomalies. Generates executive summaries
  in plain text or markdown. Works with pandas, polars or SQL depending on context.
---

# CSV Analyst

Skill for analyzing, profiling and cleaning tabular data files.

## When to use this skill

- User uploads or references a CSV, TSV or Excel file
- User asks about data quality or structure
- User wants to understand what is in a dataset before using it
- User needs to find and fix data issues before processing
- User wants a summary or report of a dataset

## Analysis process

### 1. Profile the dataset

For every column, report:
- Data type (string, integer, float, date, boolean)
- Number of non-null values
- Number of null values and null percentage
- Number of unique values
- For numeric columns: min, max, mean, median, std deviation
- For string columns: most frequent values

### 2. Detect data quality issues

Check for:
- **Nulls** — columns with > 10% nulls need attention
- **Duplicates** — exact duplicate rows
- **Outliers** — values beyond 3 standard deviations from mean
- **Type mismatches** — numbers stored as strings
- **Inconsistent formatting** — mixed date formats, inconsistent capitalization
- **Leading/trailing whitespace** — common in string columns

### 3. Generate the summary

Produce a concise report with:
1. Dataset shape (rows x columns)
2. Column inventory with types
3. Top data quality issues found
4. Recommended cleaning steps
5. Key statistics for numeric columns

## Cleaning recommendations

| Issue | Recommended action |
|---|---|
| Null values | Fill with median (numeric) or mode (categorical), or drop if > 50% null |
| Duplicates | Drop duplicate rows, keep first occurrence |
| Outliers | Flag for review, do not remove without confirmation |
| Type mismatches | Cast to correct type, log conversion errors |
| Whitespace | Strip leading/trailing whitespace from all string columns |

## Compatibility

Claude Code, Cursor, Windsurf, Cline, Roo and any agent compatible with the Agent Skills standard.
