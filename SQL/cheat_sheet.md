
# SQL CHEAT SHEET

## 1. BASIC QUERIES

```sql
-- Select specific columns
SELECT column1, column2
FROM table_name;

-- Select all columns
SELECT *
FROM table_name;

-- Remove duplicates
SELECT DISTINCT column_name
FROM table_name;

-- Rename columns
SELECT column_name AS new_name
FROM table_name;

-- Limit results
SELECT *
FROM table_name
LIMIT 10;

-- Sort results
SELECT *
FROM table_name
ORDER BY column_name ASC;  -- ASC = ascending
                           -- DESC = descending
```

## 2. FILTERING DATA (WHERE)

```sql
SELECT *
FROM customers
WHERE age > 25;

-- Comparison operators
=       -- Equal
!=      -- Not equal
<>      -- Not equal
>       -- Greater than
<       -- Less than
>=      -- Greater than or equal
<=      -- Less than or equal

-- Multiple conditions
WHERE country = 'USA' AND age > 25;
WHERE country = 'USA' OR country = 'UK';
WHERE NOT country = 'USA';

-- Match multiple values
WHERE country IN ('USA', 'UK', 'Canada');

-- Range (inclusive)
WHERE age BETWEEN 20 AND 40;

-- Pattern matching
WHERE name LIKE 'A%';   -- Starts with A
WHERE name LIKE '%a';   -- Ends with a
WHERE name LIKE '%an%'; -- Contains an
WHERE name ILIKE 'a%';  -- Case-insensitive

-- NULL values
WHERE column_name IS NULL;
WHERE column_name IS NOT NULL;
```

## 3. AGGREGATE FUNCTIONS

```sql
SELECT
    COUNT(*) AS total_rows,
    COUNT(column_name) AS non_null_count,
    COUNT(DISTINCT column_name) AS unique_count,
    SUM(sales) AS total_sales,
    AVG(sales) AS average_sales,
    MIN(sales) AS minimum_sales,
    MAX(sales) AS maximum_sales
FROM orders;
```

IMPORTANT:
- COUNT(*) counts all rows.
- COUNT(column) ignores NULL values.
- SUM, AVG, MIN, MAX generally ignore NULL values.

## 4. GROUP BY & HAVING

```sql
-- Aggregate by category
SELECT
    country,
    COUNT(*) AS customers,
    AVG(age) AS average_age
FROM customers
GROUP BY country;

-- Filter aggregated results
SELECT
    country,
    COUNT(*) AS customers
FROM customers
GROUP BY country
HAVING COUNT(*) > 10;

-- Filter rows before aggregation
SELECT country, COUNT(*)
FROM customers
WHERE age > 25
GROUP BY country
HAVING COUNT(*) > 5;
```

IMPORTANT:
- WHERE filters individual rows.
- HAVING filters aggregated groups.
- Non-aggregated SELECT columns generally must appear in GROUP BY.

## 5. JOINS

```sql
-- INNER JOIN: matching rows in both tables
SELECT *
FROM customers c
INNER JOIN orders o
    ON c.customer_id = o.customer_id;

-- LEFT JOIN: all left rows + matching right rows
SELECT *
FROM customers c
LEFT JOIN orders o
    ON c.customer_id = o.customer_id;

-- RIGHT JOIN: all right rows + matching left rows
SELECT *
FROM customers c
RIGHT JOIN orders o
    ON c.customer_id = o.customer_id;

-- FULL JOIN: all rows from both tables
SELECT *
FROM customers c
FULL OUTER JOIN orders o
    ON c.customer_id = o.customer_id;

-- CROSS JOIN: every possible combination
SELECT *
FROM customers
CROSS JOIN products;
```

IMPORTANT:
- INNER = matching records only.
- LEFT = keep everything from left table.
- RIGHT = keep everything from right table.
- FULL = keep everything from both.
- Unmatched columns are filled with NULL.
- Watch for duplicate rows caused by one-to-many relationships.

## 6. SET OPERATIONS

```sql
-- Combine results and remove duplicates
SELECT city FROM customers
UNION
SELECT city FROM suppliers;

-- Combine results and keep duplicates
SELECT city FROM customers
UNION ALL
SELECT city FROM suppliers;

-- Values appearing in both results
SELECT city FROM customers
INTERSECT
SELECT city FROM suppliers;

-- Values in first result but not second
SELECT city FROM customers
EXCEPT
SELECT city FROM suppliers;
```

IMPORTANT:
- Queries must return the same number of columns.
- Corresponding columns must have compatible data types.
- UNION ALL is generally faster than UNION because it doesn't remove duplicates.

## 7. CASE WHEN (CONDITIONAL LOGIC)

```sql
SELECT
    customer_id,
    sales,
    CASE
        WHEN sales >= 1000 THEN 'High'
        WHEN sales >= 500 THEN 'Medium'
        ELSE 'Low'
    END AS sales_category
FROM orders;
```

Conditional aggregation:

```sql
SELECT
    COUNT(*) AS total_orders,
    SUM(CASE WHEN status = 'Completed' THEN 1 ELSE 0 END)
        AS completed_orders
FROM orders;
```

## 8. SUBQUERIES

```sql
-- Find customers with above-average age
SELECT *
FROM customers
WHERE age > (
    SELECT AVG(age)
    FROM customers
);

-- IN subquery
SELECT *
FROM customers
WHERE customer_id IN (
    SELECT customer_id
    FROM orders
);

-- EXISTS
SELECT *
FROM customers c
WHERE EXISTS (
    SELECT 1
    FROM orders o
    WHERE o.customer_id = c.customer_id
);
```

IMPORTANT:
- A subquery is a query inside another query.
- EXISTS checks whether matching records exist.
- Correlated subqueries reference the outer query.
- NOT IN can behave unexpectedly if the subquery contains NULL; consider NOT EXISTS.

## 9. COMMON TABLE EXPRESSIONS (CTEs)

```sql
WITH customer_sales AS (
    SELECT
        customer_id,
        SUM(amount) AS total_sales
    FROM orders
    GROUP BY customer_id
)

SELECT *
FROM customer_sales
WHERE total_sales > 500;
```

Multiple CTEs:

```sql
WITH sales AS (
    SELECT customer_id, SUM(amount) AS total
    FROM orders
    GROUP BY customer_id
),
high_value AS (
    SELECT *
    FROM sales
    WHERE total > 1000
)
SELECT *
FROM high_value;
```

IMPORTANT:
- CTEs improve readability.
- Defined using WITH.
- Exist only for the duration of the query.
- Useful for breaking complex queries into steps.

## 10. WINDOW FUNCTIONS

```sql
-- Calculate totals without collapsing rows
SELECT
    customer_id,
    amount,
    SUM(amount) OVER (
        PARTITION BY customer_id
    ) AS customer_total
FROM orders;

-- Rank records
SELECT
    customer_id,
    amount,
    ROW_NUMBER() OVER (
        ORDER BY amount DESC
    ) AS row_num
FROM orders;

-- Rank within groups
SELECT
    customer_id,
    amount,
    RANK() OVER (
        PARTITION BY customer_id
        ORDER BY amount DESC
    ) AS sales_rank
FROM orders;

-- Running total
SELECT
    order_date,
    amount,
    SUM(amount) OVER (
        ORDER BY order_date
        ROWS BETWEEN UNBOUNDED PRECEDING
        AND CURRENT ROW
    ) AS running_total
FROM orders;

-- Previous row's value
LAG(amount) OVER (ORDER BY order_date);

-- Next row's value
LEAD(amount) OVER (ORDER BY order_date);
```

IMPORTANT:
- GROUP BY collapses rows.
- Window functions preserve individual rows.
- PARTITION BY defines groups.
- ORDER BY defines sequence within a window.

RANKING DIFFERENCES:
- ROW_NUMBER: Always unique sequence.
- RANK: Ties receive same rank; gaps follow.
- DENSE_RANK: Ties receive same rank; no gaps.

## 11. DATE FUNCTIONS (POSTGRESQL)

```sql
-- Current date and timestamp
SELECT CURRENT_DATE;
SELECT NOW();

-- Extract date parts
SELECT
    EXTRACT(YEAR FROM order_date) AS year,
    EXTRACT(MONTH FROM order_date) AS month,
    EXTRACT(DAY FROM order_date) AS day
FROM orders;

-- Filter date ranges
WHERE order_date >= '2025-01-01'
  AND order_date < '2026-01-01';

-- Date arithmetic
SELECT order_date + INTERVAL '7 days'
FROM orders;

-- Difference between dates
SELECT AGE(CURRENT_DATE, order_date)
FROM orders;

-- Group by month
SELECT
    DATE_TRUNC('month', order_date) AS month,
    SUM(amount) AS revenue
FROM orders
GROUP BY 1
ORDER BY 1;
```

## 12. STRING FUNCTIONS

```sql
SELECT
    UPPER(name),
    LOWER(name),
    LENGTH(name),
    TRIM(name),
    LEFT(name, 3),
    RIGHT(name, 3),
    SUBSTRING(name FROM 1 FOR 3),
    REPLACE(name, 'old', 'new')
FROM customers;

-- Concatenate strings
SELECT first_name || ' ' || last_name AS full_name
FROM customers;

-- Handle NULL values
SELECT COALESCE(phone, 'Unknown')
FROM customers;
```

## 13. NUMERIC FUNCTIONS

```sql
SELECT
    ROUND(price, 2),
    CEIL(price),
    FLOOR(price),
    ABS(price),
    MOD(price, 2)
FROM products;

-- Percentage calculation
SELECT
    SUM(profit) / NULLIF(SUM(revenue), 0) * 100
        AS profit_margin
FROM sales;
```

IMPORTANT:
- NULLIF prevents division by zero.
- COALESCE replaces NULL with a fallback value.
- Use ROUND to control decimal places.

## 14. DATA CLEANING

```sql
-- Identify NULL values
SELECT *
FROM customers
WHERE email IS NULL;

-- Find duplicates
SELECT email, COUNT(*)
FROM customers
GROUP BY email
HAVING COUNT(*) > 1;

-- Remove surrounding whitespace
SELECT TRIM(name)
FROM customers;

-- Replace NULL
SELECT COALESCE(age, 0)
FROM customers;

-- Conditional data cleaning
SELECT
    CASE
        WHEN age < 0 THEN NULL
        ELSE age
    END AS cleaned_age
FROM customers;
```

IMPORTANT:
- Always inspect missing values.
- Check duplicates before removing them.
- Don't automatically replace NULL with 0; understand what NULL represents.
- Check data types and inconsistent formats.

## 15. SQL QUERY EXECUTION ORDER

1. FROM / JOIN
2. WHERE
3. GROUP BY
4. HAVING
5. SELECT
6. DISTINCT
7. ORDER BY
8. LIMIT

Written query order is different:

SELECT → FROM → WHERE → GROUP BY → HAVING → ORDER BY → LIMIT

## 16. DATABASE FUNDAMENTALS

- PRIMARY KEY: Uniquely identifies each row.
- FOREIGN KEY: References a key in another table.
- UNIQUE: Prevents duplicate values.
- NOT NULL: Requires a value.
- DEFAULT: Sets a default value.
- INDEX: Helps speed up data retrieval.
- NULL: Represents missing or unknown information.

## 17. COMMON INTERVIEW PATTERNS

-- Find the second-highest salary
```sql
SELECT MAX(salary)
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

-- Find top 3 salaries per department
```sql
WITH ranked AS (
    SELECT *,
        DENSE_RANK() OVER (
            PARTITION BY department
            ORDER BY salary DESC
        ) AS rnk
    FROM employees
)
SELECT *
FROM ranked
WHERE rnk <= 3;
```

-- Find customers with no orders
```sql
SELECT c.*
FROM customers c
LEFT JOIN orders o
    ON c.customer_id = o.customer_id
WHERE o.order_id IS NULL;
```

-- Find duplicate records
```sql
SELECT email, COUNT(*)
FROM customers
GROUP BY email
HAVING COUNT(*) > 1;
```

-- Calculate percentage of total sales
```sql
SELECT
    category,
    SUM(sales) AS category_sales,
    SUM(sales) * 100.0 /
        SUM(SUM(sales)) OVER () AS percentage
FROM orders
GROUP BY category;
```

-- Month-over-month sales comparison
```sql
WITH monthly_sales AS (
    SELECT
        DATE_TRUNC('month', order_date) AS month,
        SUM(amount) AS revenue
    FROM orders
    GROUP BY 1
)
SELECT
    month,
    revenue,
    LAG(revenue) OVER (ORDER BY month) AS previous_month,
    revenue - LAG(revenue) OVER (ORDER BY month) AS change
FROM monthly_sales;
```

## 18. INTERVIEW REMINDERS

- Understand the business question before writing SQL.
- Identify the correct table and join keys.
- Check whether joins create duplicate records.
- Know the difference between WHERE and HAVING.
- Know INNER JOIN vs LEFT JOIN.
- Understand NULL handling.
- Know GROUP BY vs window functions.
- Practice CTEs and subqueries.
- Understand ROW_NUMBER, RANK and DENSE_RANK.
- Check for division by zero.
- Use readable aliases and formatting.
- Validate your results.
