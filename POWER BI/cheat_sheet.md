# POWER BI CHEAT SHEET

## 1. WHAT IS POWER BI?

Power BI is Microsoft's business intelligence and data visualization platform.

Used to:
- Connect to different data sources.
- Clean and transform data.
- Build data models.
- Create interactive reports.
- Analyze business performance.
- Share dashboards and reports.

MAIN COMPONENTS:
- Power BI Desktop: Build reports and data models.
- Power BI Service: Publish, share, and manage reports online.
- Power BI Mobile: View reports on mobile devices.
- Power Query: Clean and transform data.
- DAX: Create calculations and measures.
- Power BI Gateway: Connect cloud services to on-premises data.

## 2. POWER BI WORKFLOW

Typical analyst workflow:

1. Connect to data.
2. Transform and clean data using Power Query.
3. Load data into Power BI.
4. Build relationships between tables.
5. Create calculated columns and measures using DAX.
6. Build visualizations.
7. Add filters and slicers.
8. Publish reports.
9. Configure refresh and sharing.

## 3. CONNECTING TO DATA

COMMON DATA SOURCES:
- Excel
- CSV
- SQL Server
- PostgreSQL
- SharePoint
- Web
- APIs
- Azure
- Other databases

IMPORT VS DIRECTQUERY:

IMPORT:
- Data is loaded into Power BI's model.
- Generally faster report performance.
- Data must be refreshed to reflect source changes.
- Uses in-memory storage.

DIRECTQUERY:
- Data remains in the source system.
- Queries are sent to the source when needed.
- Can provide more current data.
- Performance depends on the source and query design.
- Some modeling and transformation limitations apply.

IMPORTANT:
- Import = Data stored in Power BI.
- DirectQuery = Data queried from source.
- Choose based on data volume, freshness, source capability, and performance requirements.

## 4. POWER QUERY (DATA CLEANING)

Power Query is used to extract, transform, and load data (ETL).

COMMON TRANSFORMATIONS:
- Remove duplicates.
- Remove errors.
- Replace values.
- Change data types.
- Filter rows.
- Rename columns.
- Split columns.
- Merge columns.
- Append queries.
- Merge queries.
- Group by.
- Pivot columns.
- Unpivot columns.
- Remove unnecessary columns.
- Handle missing values.

IMPORTANT OPERATIONS:

MERGE QUERIES:
- Combines tables horizontally.
- Matches records using common columns.
- Similar to SQL JOIN.

APPEND QUERIES:
- Combines tables vertically.
- Stacks rows from multiple tables.
- Similar to SQL UNION ALL.

PIVOT:
- Turns unique values into columns.

UNPIVOT:
- Turns columns into rows.
- Useful when data is stored in a wide format.

M LANGUAGE:
Power Query uses the M language.

Example:

```powerquery
let
    Source = Excel.CurrentWorkbook(){[Name="Sales"]}[Content],
    ChangedType = Table.TransformColumnTypes(
        Source,
        {{"Sales", type number}}
    ),
    RemovedDuplicates = Table.Distinct(ChangedType)
in
    RemovedDuplicates
```

IMPORTANT:
- Applied Steps record transformation steps.
- Query folding pushes transformations back to the source when supported.
- Disable load for staging queries when appropriate.
- Power Query transformations happen before data is loaded into the model.

## 5. DATA MODELING

Data modeling defines how tables relate to each other.

COMMON RELATIONSHIPS:

ONE-TO-MANY (1:*):
- One customer can have many orders.
- Most common relationship in analytical models.

ONE-TO-ONE (1:1):
- One record relates to one record.

MANY-TO-MANY (*:*):
- Multiple records on both sides can match.
- Requires careful modeling to avoid ambiguous results.

RELATIONSHIP CONCEPTS:
- Primary key: Unique identifier.
- Foreign key: References another table.
- Cardinality: Defines relationship type.
- Cross-filter direction: Determines how filters propagate.
- Active relationship: Used by default.
- Inactive relationship: Can be activated in specific calculations.

## 6. STAR SCHEMA

A star schema is a recommended structure for analytical data models.

FACT TABLE:
Contains measurable business events.

Examples:
- Sales transactions.
- Orders.
- Revenue.
- Quantity.
- Profit.

DIMENSION TABLES:
Contain descriptive attributes.

Examples:
- Customers.
- Products.
- Dates.
- Regions.
- Employees.

Example:

FactSales:
- OrderID
- CustomerID
- ProductID
- DateID
- SalesAmount
- Quantity

DimCustomer:
- CustomerID
- CustomerName
- Country

DimProduct:
- ProductID
- ProductName
- Category

DimDate:
- DateID
- Date
- Month
- Quarter
- Year

IMPORTANT:
- Fact tables contain measures and foreign keys.
- Dimension tables contain descriptive attributes.
- Dimension tables generally have unique keys.
- Star schemas improve usability and often improve performance.
- Avoid unnecessary many-to-many relationships.

## 7. DAX FUNDAMENTALS

DAX = Data Analysis Expressions.

Used to create:
- Measures.
- Calculated columns.
- Calculated tables.

MEASURE:
Calculated dynamically based on filter context.

```dax
Total Sales = SUM(FactSales[SalesAmount])

Total Orders = COUNTROWS(FactSales)

Average Sales = AVERAGE(FactSales[SalesAmount])

Total Quantity = SUM(FactSales[Quantity])

Total Profit = SUM(FactSales[Profit])

Profit Margin =
DIVIDE([Total Profit], [Total Sales], 0)
```

CALCULATED COLUMN:
Calculated row by row and stored in the model.

```dax
Sales Category =
IF(
    FactSales[SalesAmount] >= 1000,
    "High",
    "Low"
)
```

CALCULATED TABLE:

```dax
HighValueSales =
FILTER(
    FactSales,
    FactSales[SalesAmount] >= 1000
)
```

IMPORTANT:
- Measures are calculated when used in a visual or query.
- Calculated columns are stored in the model.
- Prefer measures for aggregations and dynamic calculations.
- Calculated columns increase model storage.

## 8. COMMON DAX FUNCTIONS

AGGREGATION:

```dax
Total Sales = SUM(FactSales[SalesAmount])

Average Sales = AVERAGE(FactSales[SalesAmount])

Minimum Sales = MIN(FactSales[SalesAmount])

Maximum Sales = MAX(FactSales[SalesAmount])

Order Count = COUNTROWS(FactSales)

Customer Count = DISTINCTCOUNT(FactSales[CustomerID])
```

CONDITIONAL:

```dax
High Sales =
CALCULATE(
    [Total Sales],
    FactSales[SalesAmount] > 1000
)

Completed Orders =
CALCULATE(
    [Order Count],
    FactSales[Status] = "Completed"
)
```

LOGICAL:

```dax
Sales Category =
IF([Total Sales] > 10000, "High", "Low")

Sales Status =
SWITCH(
    TRUE(),
    [Total Sales] >= 10000, "High",
    [Total Sales] >= 5000, "Medium",
    "Low"
)
```

FILTERING:

```dax
High Value Sales =
CALCULATE(
    [Total Sales],
    FILTER(
        FactSales,
        FactSales[SalesAmount] > 1000
    )
)
```

## 9. CALCULATE — MOST IMPORTANT DAX FUNCTION

CALCULATE evaluates an expression under modified filter context.

Syntax:

```dax
CALCULATE(
    expression,
    filter1,
    filter2
)
```

Example:

```dax
US Sales =
CALCULATE(
    [Total Sales],
    DimCustomer[Country] = "USA"
)
```

Remove filters:

```dax
All Sales =
CALCULATE(
    [Total Sales],
    REMOVEFILTERS(DimProduct)
)
```

Keep only selected filters:

```dax
Sales All Regions =
CALCULATE(
    [Total Sales],
    REMOVEFILTERS(DimCustomer[Country])
)
```

IMPORTANT:
- CALCULATE modifies filter context.
- Existing filters may be replaced by new filters on the same columns.
- REMOVEFILTERS removes filters.
- ALL can return an unfiltered table or remove filters.
- ALLEXCEPT removes filters except those on specified columns.

## 10. FILTER CONTEXT VS ROW CONTEXT

ROW CONTEXT:
- Evaluates calculations for an individual row.
- Common in calculated columns and iterator functions.

FILTER CONTEXT:
- Determines which rows are included in a calculation.
- Created by slicers, filters, visuals, and CALCULATE.

EXAMPLE:

```dax
Total Sales = SUM(FactSales[SalesAmount])
```

If a report is filtered to USA, the measure calculates sales for USA.

IMPORTANT:
- Row context = Current row.
- Filter context = Current set of filtered data.
- CALCULATE can perform context transition.

## 11. ITERATOR FUNCTIONS

Iterator functions evaluate an expression row by row, then aggregate the results.

COMMON ITERATORS:
- SUMX
- AVERAGEX
- COUNTX
- MINX
- MAXX
- RANKX

Example:

```dax
Total Revenue =
SUMX(
    FactSales,
    FactSales[Quantity] * FactSales[UnitPrice]
)
```

Difference:

```dax
SUM(FactSales[SalesAmount])
```

Adds an existing column.

```dax
SUMX(
    FactSales,
    FactSales[Quantity] * FactSales[UnitPrice]
)
```

Calculates an expression for each row and then sums the results.

## 12. TIME INTELLIGENCE

Requires a properly configured date table with continuous dates.

COMMON FUNCTIONS:

```dax
Total Sales = SUM(FactSales[SalesAmount])

Previous Year Sales =
CALCULATE(
    [Total Sales],
    SAMEPERIODLASTYEAR(DimDate[Date])
)

Year to Date Sales =
TOTALYTD(
    [Total Sales],
    DimDate[Date]
)

Previous Month Sales =
CALCULATE(
    [Total Sales],
    DATEADD(DimDate[Date], -1, MONTH)
)

Month to Date Sales =
TOTALMTD(
    [Total Sales],
    DimDate[Date]
)

Quarter to Date Sales =
TOTALQTD(
    [Total Sales],
    DimDate[Date]
)
```

YEAR-OVER-YEAR CHANGE:

```dax
YoY Change =
[Total Sales] - [Previous Year Sales]

YoY Growth % =
DIVIDE(
    [YoY Change],
    [Previous Year Sales],
    0
)
```

MONTH-OVER-MONTH:

```dax
Previous Month Sales =
CALCULATE(
    [Total Sales],
    DATEADD(DimDate[Date], -1, MONTH)
)

MoM Growth % =
DIVIDE(
    [Total Sales] - [Previous Month Sales],
    [Previous Month Sales],
    0
)
```

IMPORTANT:
- Mark your date table as a date table.
- Use a continuous date column.
- Understand calendar vs fiscal year.
- Check how partial periods affect comparisons.

## 13. RANKING & PERCENTAGES

RANK PRODUCTS BY SALES:

```dax
Product Rank =
RANKX(
    ALL(DimProduct[ProductName]),
    [Total Sales],
    ,
    DESC,
    DENSE
)
```

PERCENTAGE OF TOTAL:

```dax
Sales % of Total =
DIVIDE(
    [Total Sales],
    CALCULATE(
        [Total Sales],
        REMOVEFILTERS(DimProduct)
    ),
    0
)
```

TOP N:
- Use Top N filters in the visual filter pane.
- Alternatively, use TOPN in DAX for table calculations.

## 14. VISUALIZATIONS

COMMON VISUALS:

- Bar chart: Compare categories.
- Column chart: Compare values.
- Line chart: Trends over time.
- Pie/donut chart: Proportions with few categories.
- Matrix: Hierarchical tabular summaries.
- Table: Detailed records.
- Card: Single KPI.
- KPI visual: Performance against a target.
- Scatter chart: Relationships and distributions.
- Map: Geographic analysis.
- Waterfall: Changes contributing to a total.
- Funnel: Sequential stages.

BEST PRACTICES:
- Choose visuals based on the business question.
- Avoid clutter.
- Use clear titles and labels.
- Keep colors consistent.
- Highlight important KPIs.
- Use appropriate number formatting.
- Avoid unnecessary pie charts.
- Ensure visuals are accessible.

## 15. FILTERS & SLICERS

FILTER LEVELS:

VISUAL FILTER:
Affects one visual.

PAGE FILTER:
Affects all applicable visuals on one page.

REPORT FILTER:
Affects applicable visuals across the report.

SLICERS:
- Interactive filters displayed on report pages.
- Can filter by dates, categories, regions, etc.
- Can synchronize across pages.
- Can use dropdown, list, or date range formats.

DRILL FEATURES:
- Drill down: Explore lower levels of a hierarchy.
- Drill up: Return to higher levels.
- Drill through: Navigate to a detail page filtered by a selected value.
- Cross-filtering: Selecting one visual filters another.
- Cross-highlighting: Selecting one visual highlights related values in another.

## 16. KPI & BUSINESS METRICS

COMMON DATA ANALYST METRICS:

Revenue:
```dax
Revenue = SUM(FactSales[Revenue])
```

Profit:
```dax
Profit = SUM(FactSales[Profit])
```

Profit Margin:
```dax
Profit Margin =
DIVIDE([Profit], [Revenue], 0)
```

Average Order Value:
```dax
AOV =
DIVIDE([Revenue], [Order Count], 0)
```

Customer Count:
```dax
Customers =
DISTINCTCOUNT(FactSales[CustomerID])
```

Average Revenue Per Customer:
```dax
Revenue Per Customer =
DIVIDE([Revenue], [Customers], 0)
```

IMPORTANT:
- Define KPIs consistently.
- Understand numerator and denominator.
- Distinguish revenue from profit.
- Confirm whether metrics are calculated per transaction, customer, or period.

## 17. PERFORMANCE OPTIMIZATION

BEST PRACTICES:
- Use star schemas.
- Remove unnecessary columns.
- Remove unused rows.
- Prefer appropriate data types.
- Avoid excessive calculated columns.
- Prefer measures for dynamic aggregations.
- Use variables in complex DAX.
- Reduce unnecessary visuals.
- Avoid excessive bidirectional relationships.
- Optimize Power Query transformations.
- Use query folding when possible.
- Analyze slow DAX using Performance Analyzer.
- Reduce unnecessary high-cardinality columns.

VARIABLES:

```dax
Profit Margin =
VAR Revenue = [Total Sales]
VAR Profit = [Total Profit]
RETURN
    DIVIDE(Profit, Revenue, 0)
```

IMPORTANT:
- Variables improve readability.
- Variables can avoid repeating expressions.
- Performance Analyzer helps identify slow visuals.

## 18. PUBLISHING & POWER BI SERVICE

COMMON CONCEPTS:

WORKSPACE:
Area for collaborating on reports and datasets/semantic models.

REPORT:
One or more pages of interactive visualizations.

DASHBOARD:
Single-page canvas in Power BI Service that can combine pinned tiles.

SEMANTIC MODEL:
The modeled data, relationships, measures, and metadata used by reports.

GATEWAY:
Connects Power BI Service to on-premises data sources.

REFRESH:
Updates imported data from its source.

SCHEDULED REFRESH:
Automatically refreshes data at configured times.

ROW-LEVEL SECURITY (RLS):
Restricts data visibility based on user identity or assigned roles.

IMPORTANT:
- Publishing sends content to the Power BI Service.
- Refresh updates data, not necessarily the report design.
- RLS controls which rows users can access.
- Workspace roles control permissions and collaboration.

## 19. COMMON INTERVIEW QUESTIONS

WHAT IS POWER BI?
A business intelligence platform used to transform, model, visualize, and share data.

POWER QUERY VS DAX?
- Power Query: Data preparation and transformation before loading.
- DAX: Calculations and analysis within the data model.

MEASURE VS CALCULATED COLUMN?
- Measure: Evaluated dynamically based on filter context.
- Calculated column: Evaluated row by row and stored.

IMPORT VS DIRECTQUERY?
- Import: Data stored in Power BI.
- DirectQuery: Data queried from the source.

MERGE VS APPEND?
- Merge: Join tables horizontally.
- Append: Stack tables vertically.

STAR SCHEMA?
A model with a central fact table connected to dimension tables.

CALCULATE?
Evaluates an expression in modified filter context.

SUM VS SUMX?
- SUM: Adds values in a column.
- SUMX: Iterates rows, evaluates an expression, and sums the results.

ROW VS FILTER CONTEXT?
- Row context: Current row evaluation.
- Filter context: Filters determining which data is included.

WHAT IS RLS?
Row-Level Security restricts records users can see.

## 20. INTERVIEW REMINDERS

- Understand Power Query and ETL.
- Know Merge vs Append.
- Understand data types and cleaning.
- Know star schema and relationships.
- Understand fact vs dimension tables.
- Master measures vs calculated columns.
- Practice SUM, COUNTROWS, DISTINCTCOUNT.
- Master CALCULATE and FILTER.
- Understand row vs filter context.
- Practice SUMX and other iterators.
- Learn time intelligence.
- Understand slicers and filter context.
- Know how to build KPI dashboards.
- Understand Import vs DirectQuery.
- Learn basic performance optimization.
- Understand publishing, refresh, and RLS.
- Always connect visuals to business questions.