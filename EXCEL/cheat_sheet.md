
# EXCEL CHEAT SHEET

## 1. BASIC EXCEL FUNCTIONS

```excel
=SUM(A2:A100)           // Add values
=AVERAGE(A2:A100)       // Calculate average
=MIN(A2:A100)           // Minimum value
=MAX(A2:A100)           // Maximum value
=COUNT(A2:A100)         // Count numeric cells
=COUNTA(A2:A100)        // Count non-empty cells
=COUNTBLANK(A2:A100)    // Count empty cells
=ROUND(A2,2)            // Round to 2 decimals
=ABS(A2)                // Absolute value
=SUBTOTAL(9,A2:A100)    // Sum, respecting filters
```

## 2. CELL REFERENCES

```excel
=A2       // Relative reference
=$A$2     // Absolute reference
=$A2      // Fixed column
=A$2      // Fixed row
```

IMPORTANT:
- Relative references change when copied.
- Absolute references remain fixed.
- Press F4 while editing a reference to cycle through reference types.

## 3. CONDITIONAL LOGIC

```excel
=IF(A2>100,"High","Low")

=IFS(
    A2>=90,"Excellent",
    A2>=70,"Good",
    A2>=50,"Average",
    TRUE,"Poor"
)

=AND(A2>50,B2="USA")
=OR(A2>50,B2="USA")
=NOT(A2>50)

=IF(AND(A2>50,B2="USA"),"Qualified","Not Qualified")

=IFERROR(A2/B2,0)
=IFNA(VLOOKUP(A2,F:G,2,FALSE),"Not Found")
```

IMPORTANT:
- IF evaluates one condition.
- IFS evaluates multiple conditions.
- AND requires all conditions to be TRUE.
- OR requires at least one condition to be TRUE.
- IFERROR handles any formula error.
- IFNA handles #N/A errors specifically.

## 4. CONDITIONAL AGGREGATION

```excel
=COUNTIF(A:A,"USA")
=COUNTIFS(A:A,"USA",B:B,">100")

=SUMIF(A:A,"USA",B:B)
=SUMIFS(C:C,A:A,"USA",B:B,">100")

=AVERAGEIF(A:A,"USA",B:B)
=AVERAGEIFS(C:C,A:A,"USA",B:B,">100")

=MAXIFS(C:C,A:A,"USA")
=MINIFS(C:C,A:A,"USA")
```

IMPORTANT:
- COUNTIF: Count based on one condition.
- COUNTIFS: Count based on multiple conditions.
- SUMIF: Sum based on one condition.
- SUMIFS: Sum based on multiple conditions.
- AVERAGEIF / AVERAGEIFS: Conditional averages.

## 5. LOOKUP FUNCTIONS

### XLOOKUP (Preferred)

```excel
=XLOOKUP(
    A2,
    Customers!A:A,
    Customers!B:B,
    "Not Found"
)
```

Syntax:
```excel
=XLOOKUP(lookup_value,lookup_array,return_array,if_not_found)
```

### VLOOKUP

```excel
=VLOOKUP(A2,$F$2:$H$100,3,FALSE)
```

Syntax:
```excel
=VLOOKUP(lookup_value,table_array,col_index_num,FALSE)
```

IMPORTANT:
- FALSE = exact match.
- TRUE = approximate match.
- VLOOKUP searches the first column of the lookup range.
- VLOOKUP returns values to the right.
- XLOOKUP can search in either direction.
- XLOOKUP uses exact match by default.

### INDEX + MATCH

```excel
=INDEX(B:B,MATCH(A2,A:A,0))
```

IMPORTANT:
- MATCH finds the position.
- INDEX returns the value at that position.
- 0 means exact match.
- Useful when XLOOKUP is unavailable.

## 6. TEXT FUNCTIONS

```excel
=CONCAT(A2,B2)
=TEXTJOIN(" ",TRUE,A2,B2)
=LEFT(A2,3)
=RIGHT(A2,4)
=MID(A2,2,5)
=LEN(A2)
=TRIM(A2)
=UPPER(A2)
=LOWER(A2)
=PROPER(A2)
=SUBSTITUTE(A2,"old","new")
=REPLACE(A2,1,3,"New")
=FIND("@",A2)
=SEARCH("abc",A2)
=TEXT(A2,"$#,##0.00")
```

IMPORTANT:
- TRIM removes extra spaces between words and at the ends.
- LEFT extracts characters from the beginning.
- RIGHT extracts characters from the end.
- MID extracts characters from a specified position.
- FIND is case-sensitive.
- SEARCH is not case-sensitive.
- TEXT formats a number as text.

## 7. DATE & TIME FUNCTIONS

```excel
=TODAY()                     // Current date
=NOW()                       // Current date and time
=YEAR(A2)                    // Extract year
=MONTH(A2)                   // Extract month
=DAY(A2)                     // Extract day
=DATE(2025,1,1)              // Create date
=DATEDIF(A2,B2,"Y")          // Difference in years
=EOMONTH(A2,0)               // End of current month
=EOMONTH(A2,1)               // End of next month
=EDATE(A2,3)                 // Add 3 months
=NETWORKDAYS(A2,B2)          // Working days
=WORKDAY(A2,10)              // Add 10 working days
=WEEKDAY(A2)                 // Day of week
```

IMPORTANT:
- Excel stores dates as serial numbers.
- Date formatting changes display, not the underlying value.
- NETWORKDAYS excludes weekends by default.
- TODAY updates automatically.

## 8. DYNAMIC ARRAY FUNCTIONS (EXCEL 365)

```excel
=UNIQUE(A2:A100)
=SORT(A2:A100)
=SORT(A2:A100,1,-1)
=FILTER(A2:C100,B2:B100="USA")
=SEQUENCE(10)
=VSTACK(A2:C10,E2:G10)
=HSTACK(A2:A10,C2:C10)
```

IMPORTANT:
- UNIQUE returns distinct values.
- SORT sorts an array.
- FILTER returns rows matching a condition.
- SEQUENCE generates sequential numbers.
- VSTACK combines ranges vertically.
- HSTACK combines ranges horizontally.
- Results spill into adjacent cells.

## 9. DATA CLEANING

```excel
=TRIM(A2)                  // Remove extra spaces
=CLEAN(A2)                 // Remove non-printable characters
=PROPER(A2)                // Standardize capitalization
=SUBSTITUTE(A2,"-","")     // Replace characters
=VALUE(A2)                 // Convert text to number
=TEXT(A2,"yyyy-mm-dd")     // Format as text
=ISBLANK(A2)               // Check blank cells
=ISNUMBER(A2)              // Check numeric values
=ISTEXT(A2)                // Check text values
=IF(A2="","Missing","OK")  // Identify missing values
```

COMMON DATA CLEANING TASKS:
- Remove duplicates: Data > Remove Duplicates.
- Split columns: Data > Text to Columns.
- Standardize dates and number formats.
- Remove leading/trailing spaces.
- Identify blanks and inconsistent values.
- Find and replace inconsistent categories.
- Check for duplicate IDs.

## 10. PIVOT TABLES

PURPOSE:
Summarize large datasets without writing formulas.

STEPS:
1. Select your dataset.
2. Insert > PivotTable.
3. Drag fields into the appropriate areas.

PIVOT TABLE AREAS:
- ROWS: Categories to group by.
- COLUMNS: Categories across columns.
- VALUES: Metrics to calculate.
- FILTERS: Filter the entire PivotTable.

EXAMPLE:

Dataset:
| Region | Product | Sales |
|---|---|---:|
| East | A | 100 |
| West | B | 200 |
| East | A | 150 |

PivotTable:
- Rows: Region
- Columns: Product
- Values: Sum of Sales

Result:
| Region | A | B |
|---|---:|---:|
| East | 250 | 0 |
| West | 0 | 200 |

IMPORTANT:
- Change Sum to Count or Average when needed.
- Refresh PivotTables after source data changes.
- Use Slicers for interactive filtering.
- Group dates by month, quarter, or year.
- Show Values As % of Grand Total for percentage analysis.

## 11. CONDITIONAL FORMATTING

PURPOSE:
Highlight important values automatically.

COMMON USES:
- Highlight duplicates.
- Identify values above/below thresholds.
- Highlight top/bottom performers.
- Find missing values.
- Apply color scales and data bars.

FORMULA EXAMPLES:

```excel
=A2>100
=COUNTIF($A:$A,A2)>1
=ISBLANK(A2)
=$B2="Overdue"
```

Path:
Home > Conditional Formatting.

## 12. CHARTS & DATA VISUALIZATION

COMMON CHART TYPES:

- Bar chart: Compare categories.
- Column chart: Compare values across categories.
- Line chart: Show trends over time.
- Pie chart: Show proportions (few categories).
- Scatter plot: Show relationships between variables.
- Histogram: Show distributions.
- Combo chart: Compare different metrics/scales.

BEST PRACTICES:
- Use clear titles.
- Label axes.
- Avoid unnecessary visual clutter.
- Use consistent colors.
- Don't use pie charts for too many categories.
- Choose charts based on the business question.

## 13. EXCEL TABLES

Convert data into a Table using Ctrl + T.

BENEFITS:
- Automatic expansion.
- Built-in filtering and sorting.
- Structured references.
- Automatic formula filling.
- Easier PivotTable source management.

Example:

```excel
=SUM(Table1[Sales])
=AVERAGE(Table1[Profit])
=COUNTIF(Table1[Region],"East")
```

## 14. POWER QUERY

PURPOSE:
Import, clean, transform, and combine data.

COMMON OPERATIONS:
- Import Excel, CSV, and database files.
- Remove duplicates.
- Change data types.
- Filter rows.
- Split and merge columns.
- Replace values.
- Append queries (stack datasets).
- Merge queries (join datasets).
- Unpivot columns.
- Group and aggregate data.
- Refresh transformed data.

IMPORTANT:
- MERGE = Join tables using matching columns.
- APPEND = Stack tables vertically.
- UNPIVOT = Convert columns into rows.
- Power Query transformations can be refreshed.

## 15. POWER PIVOT & DATA MODEL

PURPOSE:
Analyze multiple related tables.

KEY CONCEPTS:
- Relationships connect tables.
- Fact tables contain transactions/measures.
- Dimension tables contain descriptive attributes.
- Star schema organizes data around a central fact table.
- DAX is the formula language used in Power Pivot.

EXAMPLE DAX:

```dax
Total Sales = SUM(Sales[Amount])

Average Sales = AVERAGE(Sales[Amount])

Order Count = COUNTROWS(Sales)

Profit Margin =
DIVIDE(
    SUM(Sales[Profit]),
    SUM(Sales[Revenue])
)
```

## 16. COMMON EXCEL ERRORS

- #N/A: Lookup value not found.
- #VALUE!: Incorrect data type or argument.
- #REF!: Invalid cell reference.
- #DIV/0!: Division by zero.
- #NAME?: Unrecognized function or name.
- #NUM!: Invalid numeric calculation.
- #SPILL!: Dynamic array cannot spill into required cells.
- Circular Reference: Formula refers back to itself.

Useful functions:

```excel
=IFERROR(A2/B2,0)
=IFNA(XLOOKUP(A2,F:F,G:G),"Not Found")
```

## 17. COMMON INTERVIEW EXERCISES

### Find duplicate values

```excel
=COUNTIF($A$2:$A$100,A2)>1
```

### Calculate total sales by region

```excel
=SUMIF(A:A,"East",B:B)
```

### Calculate average sales by category

```excel
=AVERAGEIF(A:A,"Electronics",B:B)
```

### Find customer information using ID

```excel
=XLOOKUP(A2,Customers!A:A,Customers!B:B,"Not Found")
```

### Assign performance categories

```excel
=IFS(
    B2>=10000,"High",
    B2>=5000,"Medium",
    TRUE,"Low"
)
```

### Calculate percentage contribution

```excel
=B2/SUM($B$2:$B$100)
```

### Rank sales performance

```excel
=RANK.EQ(B2,$B$2:$B$100,0)
```

### Find top 5 values

```excel
=LARGE(B2:B100,1)
=LARGE(B2:B100,2)
=LARGE(B2:B100,3)
=LARGE(B2:B100,4)
=LARGE(B2:B100,5)
```

## 18. INTERVIEW REMINDERS

- Know SUM, COUNT, AVERAGE, MIN, MAX.
- Understand relative vs absolute references.
- Know IF, AND, OR, IFERROR.
- Master SUMIFS, COUNTIFS, AVERAGEIFS.
- Know XLOOKUP, VLOOKUP, INDEX/MATCH.
- Practice text and date manipulation.
- Understand PivotTables and grouping.
- Know how to identify and remove duplicates.
- Understand Power Query basics.
- Know how to select appropriate charts.
- Be able to explain how you clean messy datasets.
- Validate formulas and check for errors.
- Understand the business question before analyzing data.