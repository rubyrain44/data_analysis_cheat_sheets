# DATA MANAGEMENT & ANALYTICAL THINKING CHEAT SHEET

# 3. DATA MANAGEMENT & FUNDAMENTALS

## Types of Data

STRUCTURED DATA:
Organized into predefined rows and columns.

Examples:
- SQL tables.
- Excel spreadsheets.
- Transaction databases.

SEMI-STRUCTURED DATA:
Has some organizational structure but doesn't follow a rigid table format.

Examples:
- JSON.
- XML.
- Log files.

UNSTRUCTURED DATA:
Doesn't follow a predefined tabular structure.

Examples:
- Images.
- Videos.
- Audio.
- Free-form documents.

## Common Data Types

- INTEGER: Whole numbers.
- DECIMAL/FLOAT: Numbers with decimal places.
- STRING/VARCHAR: Text.
- BOOLEAN: TRUE/FALSE.
- DATE: Calendar date.
- TIMESTAMP: Date and time.

IMPORTANT:
Correct data types are essential for calculations, comparisons and analysis.

## Database Concepts

DATABASE:
Organized collection of data.

TABLE:
Stores related records.

ROW:
One individual record.

COLUMN:
An attribute or field.

PRIMARY KEY:
Uniquely identifies each record in a table.

FOREIGN KEY:
References a key in another table to establish a relationship.

RELATIONSHIP:
Defines how tables connect.

COMMON RELATIONSHIPS:

ONE-TO-ONE:
One record relates to one record.

ONE-TO-MANY:
One record relates to multiple records.

MANY-TO-MANY:
Multiple records relate to multiple records, usually through a junction table.

## Database vs Data Warehouse

DATABASE:
Often designed to store and manage operational transactions.

Example:
An online store recording customer orders.

DATA WAREHOUSE:
Designed to consolidate historical data for reporting and analysis.

Example:
Combining sales, customer and product data for business reporting.

OLTP:
Online Transaction Processing.
Supports daily operational transactions.

OLAP:
Online Analytical Processing.
Supports analytical queries and reporting.

## Data Warehouse Concepts

FACT TABLE:
Contains measurable business events and foreign keys.

Examples:
- Sales amount.
- Quantity sold.
- Transaction count.
- Revenue.

DIMENSION TABLE:
Contains descriptive information used to analyze facts.

Examples:
- Customer.
- Product.
- Date.
- Region.

STAR SCHEMA:
A central fact table connected directly to dimension tables.

SNOWFLAKE SCHEMA:
A dimensional model where dimension tables are further normalized into related tables.

GRAIN:
Defines exactly what one row in a fact table represents.

Example:
One row per individual sales transaction line.

IMPORTANT:
Always understand the grain before analyzing or joining tables.

## ETL vs ELT

ETL:
Extract → Transform → Load.

Data is extracted from sources, transformed, then loaded into the destination.

ELT:
Extract → Load → Transform.

Data is extracted, loaded into the destination, then transformed there.

IMPORTANT:
Both processes prepare data for reporting and analysis.

## Data Pipelines

A data pipeline moves data between systems and may transform it along the way.

Typical process:

1. Extract data.
2. Validate data.
3. Transform data.
4. Load data.
5. Monitor pipeline.
6. Handle failures.

Example:
Sales data from an online store is extracted, cleaned and loaded into a data warehouse for Power BI reporting.

## Data Governance, Privacy & Security

DATA GOVERNANCE:
Policies, standards and processes ensuring data is managed properly.

DATA PRIVACY:
Protecting personal and sensitive information.

DATA SECURITY:
Protecting data from unauthorized access or misuse.

DATA LINEAGE:
Tracking where data originated and how it changed.

DATA CATALOG:
An organized inventory of available datasets and their descriptions.

IMPORTANT:
- Follow access controls.
- Protect personal information.
- Maintain data quality.
- Document transformations.
- Follow applicable privacy regulations.

---

# 7. DATA QUALITY & CLEANING

## Common Data Quality Problems

MISSING VALUES:
Blank or NULL fields.

DUPLICATES:
Repeated records.

INCONSISTENT FORMATS:
Different representations of the same information.

Example:
USA, U.S.A., United States.

INVALID VALUES:
Values that violate defined business rules.

INCORRECT DATA TYPES:
Numbers stored as text or invalid dates.

OUTLIERS:
Unusually high or low observations.

INCONSISTENT RECORDS:
Conflicting information across datasets.

## Data Quality Dimensions

ACCURACY:
Does the data correctly represent reality?

COMPLETENESS:
Are required fields populated?

CONSISTENCY:
Does data agree across systems?

VALIDITY:
Does data follow defined rules and formats?

UNIQUENESS:
Are records free from unintended duplication?

TIMELINESS:
Is data available when needed and sufficiently up to date?

## Data Cleaning Process

1. Inspect the dataset.
2. Understand the business meaning of fields.
3. Identify missing values.
4. Check duplicates.
5. Validate data types.
6. Standardize formats.
7. Investigate outliers.
8. Apply appropriate corrections.
9. Validate the cleaned data.
10. Document changes.

IMPORTANT:
Never change data without understanding the reason for the issue.

## Handling Missing Values

COMMON APPROACHES:

REMOVE RECORDS:
When missing information makes a record unusable and removal is justified.

MEAN IMPUTATION:
Replace missing numerical values with the mean when appropriate.

MEDIAN IMPUTATION:
Replace missing numerical values with the median, often useful for skewed data.

MODE IMPUTATION:
Replace missing categorical values with the most common category when appropriate.

UNKNOWN CATEGORY:
Use a separate category when missing information is meaningful.

FORWARD FILL:
Use the previous observation in suitable time-series data.

BACKWARD FILL:
Use the next observation in suitable time-series data.

IMPORTANT:
- Investigate why values are missing.
- Don't automatically replace missing values with zero.
- Consider whether missingness itself contains useful information.
- Document assumptions and changes.

## Data Standardization

Ensures values follow consistent formats.

Examples:

DATES:
2026-01-15 vs 15/01/2026

COUNTRY:
USA vs United States

TEXT:
john smith vs John Smith

CURRENCY:
$100 vs USD 100

UNITS:
Kilograms vs Pounds.

IMPORTANT:
Standardization makes comparisons and analysis more reliable.

## Data Validation

Checks whether data meets expected rules.

Examples:
- Customer IDs should be unique where required.
- Dates should fall within valid ranges.
- Quantity should not be negative unless returns are represented that way.
- Revenue should follow the agreed calculation.
- Foreign keys should match valid records.
- Required fields should not be blank.

## Data Integrity

Ensures data remains accurate and consistent throughout its lifecycle.

ENTITY INTEGRITY:
Primary keys must uniquely identify records and cannot be NULL.

REFERENTIAL INTEGRITY:
Foreign keys should reference valid records when required.

DOMAIN INTEGRITY:
Values must follow defined data types, formats and permitted ranges.

IMPORTANT:
Always check whether joins create unexpected duplicate rows.

## Root Cause Analysis

A method used to identify why a business problem occurred.

Example:

Problem:
Revenue has declined by 15%.

Possible contributing factors:
- Lower order volume.
- Lower average order value.
- Customer churn.
- Product availability.
- Reduced marketing effectiveness.
- Changes in pricing.

Analytical approach:

1. Validate the revenue calculation.
2. Compare current and previous periods.
3. Segment by product, region and customer.
4. Investigate order volume and average order value.
5. Identify the biggest contributors.
6. Recommend actions.

IMPORTANT:
Identify the underlying cause rather than only describing the symptom.

## The 5 Whys

A technique that involves repeatedly asking WHY to uncover potential root causes.

Example:

Problem:
Orders are being delivered late.

1. Why? Orders aren't dispatched on time.
2. Why? Warehouse processing is delayed.
3. Why? There is insufficient staffing.
4. Why? Staffing schedules don't match demand.
5. Why? Demand forecasting is inaccurate.

Potential root cause:
Ineffective demand forecasting.

IMPORTANT:
The 5 Whys is a starting point for investigation, not proof that the final answer is the only root cause.

## Pareto Principle (80/20 Rule)

The principle suggests that a large proportion of outcomes may come from a relatively small proportion of causes.

Example:
80% of revenue may come from 20% of products.

Used for:
- Identifying high-value customers.
- Prioritizing product performance.
- Identifying major complaint categories.
- Focusing improvement efforts.

IMPORTANT:
80/20 is a heuristic, not a universal mathematical rule.

## SWOT Analysis

A framework used to assess a business or strategy.

STRENGTHS:
Internal advantages.

WEAKNESSES:
Internal disadvantages.

OPPORTUNITIES:
External possibilities for growth.

THREATS:
External risks.

Example:
A retailer may have strong brand recognition but face increasing competition and rising supplier costs.

## Segmentation

Dividing data into meaningful groups to identify patterns and differences.

COMMON SEGMENTATION TYPES:

GEOGRAPHIC:
Country, region, city.

DEMOGRAPHIC:
Age, income, gender where appropriate and lawfully collected.

BEHAVIORAL:
Purchase behavior, browsing activity and engagement.

TRANSACTIONAL:
Spending, order frequency and purchase history.

CUSTOMER VALUE:
High, medium or low value customers.

Used to:
- Understand customer behavior.
- Identify profitable segments.
- Personalize marketing.
- Compare regional performance.
- Identify opportunities.

## Trend Analysis

Examines how metrics change over time.

Examples:
- Revenue growth.
- Customer acquisition.
- Seasonal sales.
- Churn trends.
- Operating costs.
- Website traffic.

IMPORTANT:
Consider:
- Seasonality.
- Unusual events.
- Changes in pricing.
- Changes in reporting periods.
- Changes in business operations.

## Hypothesis Development

A hypothesis is a specific, testable explanation for an observed pattern.

Example:

Observation:
Customer churn increased.

Hypothesis:
Customers on monthly subscriptions have a higher churn rate than annual subscribers.

Test:
Compare churn rates between the two groups over the same period, using consistent definitions.

IMPORTANT:
A hypothesis should be specific, measurable and testable.

---

# 9. ANALYTICAL THINKING & DECISION MAKING

## The Analytical Process

A typical process for approaching a business problem:

1. Define the business problem.
2. Identify the objective.
3. Determine the required data.
4. Form hypotheses.
5. Analyze the data.
6. Identify patterns.
7. Validate findings.
8. Draw conclusions.
9. Recommend actions.
10. Monitor results.

IMPORTANT:
Don't start analyzing data without understanding the business question.

## Types of Analytics

DESCRIPTIVE ANALYTICS:
What happened?

Example:
Revenue decreased by 10% compared with last month.

DIAGNOSTIC ANALYTICS:
Why did it happen?

Example:
Sales declined primarily in two regions.

PREDICTIVE ANALYTICS:
What might happen?

Example:
Forecasting next quarter's revenue using historical trends.

PRESCRIPTIVE ANALYTICS:
What should we do?

Example:
Recommend inventory or pricing changes based on analysis.

## Common Analytical Approaches

COMPARISON ANALYSIS:
Compare groups, periods or categories.

Example:
Compare monthly sales across regions.

TREND ANALYSIS:
Identify patterns over time.

Example:
Track revenue growth over 12 months.

SEGMENTATION:
Compare different customer or business groups.

Example:
Compare purchasing behavior across customer segments.

COHORT ANALYSIS:
Track groups of users who share a starting characteristic over time.

Example:
Compare customer retention by month of first purchase.

FUNNEL ANALYSIS:
Measure progression through stages of a process.

Example:
Website visitors → Product views → Add to cart → Checkout → Purchase.

ROOT CAUSE ANALYSIS:
Identify contributing factors behind a problem.

Example:
Investigate why customer complaints increased.

FORECASTING:
Estimate future outcomes using historical patterns and assumptions.

Example:
Predict sales for the next quarter.

## Correlation vs Causation

CORRELATION:
Two variables move together or are statistically associated.

CAUSATION:
A change in one variable contributes to a change in another.

Example:

Ice cream sales and swimming incidents may both increase in summer.

This doesn't mean ice cream causes swimming incidents.

A third factor, such as warmer weather, may influence both.

IMPORTANT:
- Correlation does not establish causation.
- Other variables may influence the relationship.
- Experiments and appropriate causal methods can help establish causal effects.

## Bias in Data Analysis

SELECTION BIAS:
The sample isn't representative of the target population.

SURVIVORSHIP BIAS:
Only successful or surviving cases are considered.

CONFIRMATION BIAS:
Favoring information that supports an existing belief.

SAMPLING BIAS:
Some groups are more likely to be included in the sample.

MEASUREMENT BIAS:
The data collection method systematically distorts results.

RESPONSE BIAS:
People provide inaccurate or influenced answers.

IMPORTANT:
- Consider whether the data represents the population.
- Check how data was collected.
- Question assumptions.
- Look for missing groups or perspectives.
- Avoid cherry-picking results.

---

# 10. COMMON DATA MANAGEMENT & ANALYTICS INTERVIEW QUESTIONS

Q: What is the difference between structured and unstructured data?

A: Structured data follows a predefined format, such as SQL tables. Unstructured data doesn't follow a fixed tabular structure, such as images or audio.

Q: What is a primary key?

A: A column or combination of columns that uniquely identifies each record in a table.

Q: What is a foreign key?

A: A column that references a key in another table to establish a relationship.

Q: What is the difference between a database and a data warehouse?

A: Databases commonly support operational transactions, while data warehouses consolidate data for reporting and analysis.

Q: What is a fact table?

A: A table containing measurable business events, such as sales transactions, along with keys connecting to dimensions.

Q: What is a dimension table?

A: A table containing descriptive attributes such as customer, product, date or region.

Q: What is ETL?

A: Extract, Transform, Load. A process of extracting data, preparing it and loading it into a target system.

Q: What is data governance?

A: Policies and processes that ensure data is managed securely, consistently and responsibly.

Q: What is data quality?

A: How well data meets requirements for accuracy, completeness, consistency, validity, uniqueness and timeliness.

Q: How do you handle duplicate records?

A: Identify duplicates, understand why they exist, determine the correct record to retain and validate the results.

Q: How do you handle missing data?

A: Investigate why values are missing, assess their impact and choose an appropriate treatment based on the business context.

Q: What is root cause analysis?

A: A structured approach to identifying the underlying reasons a problem occurred.

Q: What is the Pareto principle?

A: The idea that a large proportion of outcomes may be driven by a relatively small proportion of causes.

Q: What is cohort analysis?

A: Analyzing groups of users or customers who share a common characteristic over time, such as their first purchase date.

Q: What is funnel analysis?

A: Measuring how users progress through stages of a process and identifying where drop-offs occur.

Q: What is the difference between descriptive and predictive analytics?

A: Descriptive analytics explains what happened. Predictive analytics estimates what might happen.

Q: How would you investigate declining sales?

A: Validate the data, compare sales across periods, segment by product and region, investigate order volume and average order value, identify contributing factors and recommend actions.

---

# 11. FINAL STUDY REMINDERS

DATA MANAGEMENT:
- Know structured, semi-structured and unstructured data.
- Understand databases and data warehouses.
- Know primary and foreign keys.
- Understand fact and dimension tables.
- Know star and snowflake schemas.
- Understand ETL vs ELT.
- Know the purpose of data pipelines.
- Understand governance, privacy and security.

DATA QUALITY:
- Know accuracy, completeness and consistency.
- Understand validity, uniqueness and timeliness.
- Identify duplicates and missing values.
- Understand data standardization.
- Know how to validate data.
- Understand referential integrity.
- Document cleaning decisions.

BUSINESS ANALYSIS:
- Understand root cause analysis.
- Know the 5 Whys.
- Understand the Pareto principle.
- Know SWOT analysis.
- Understand customer segmentation.
- Practice trend analysis.
- Learn to develop testable hypotheses.

ANALYTICAL THINKING:
- Understand descriptive, diagnostic, predictive and prescriptive analytics.
- Know comparison, cohort and funnel analysis.
- Understand forecasting.
- Distinguish correlation from causation.
- Recognize common forms of bias.
- Validate findings before making recommendations.