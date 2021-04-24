# Datacamp Introduction to SQL

```sql
select 'hello world' as result;
select column from table
```

-   Databases = many tables
-   Entity - attribute :

    -   Each **row (record)** of a table
        -   contains information about a single entity
    -   Each **column (field)** of a table
        -   contains a single attribute for all rows in the table

-   BETWEEN, IN
-   IS NULL
-   **LIKE** %, \_
-   **LIKE NOT =**
-   **LIKE NOT =**
-   **LIKE NOT =**
-   **LIKE NOT =**
-   In SQL, aggregate functions can't be used in WHERE clauses
    -   use HAVING
-   INNER JOIN ... ON/USING()
-   SELF JOIN are used to compare values in a field to other values of the same field from within the same table
-   [big question : how join actually works?](https://www.sqlservercentral.com/forums/topic/left-join-with-duplicate-records)

```sql
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    WHEN conditionN THEN resultN
    ELSE result
END;
```

```sql
SELECT name, continent, code, surface_area,
    -- 1. First case
    CASE
        WHEN surface_area > 2000000 THEN 'large'
        -- 2. Second case
        WHEN surface_area > 350000 THEN 'medium'
        -- 3. Else clause + end
        ELSE 'small'
    END
        -- 4. Alias name
        AS geosize_group
-- 5. From table
FROM countries;
```

-   use CASE to define new grouping field
-   cross join performs cross product between two tables

## types of joins

-   INNER JOIN
    -   self-joins
-   OUTER JOIN
    -   LEFT JOIN
    -   RIGHT JOIN
    -   FULL JOIN
-   CROSS JOIN
-   semi-join/anti-join

> self-joins, semi-joins, anti-joins don't have built-in sql syntax

## set theory clauses

-   UNION
-   UNION ALL (replicate)
-   INTERCEPT
-   EXCEPT

## subqueries
- inside WHERE clauses
- inside SELECT clauses
- inside FROM clauses
