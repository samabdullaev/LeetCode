# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Pre-defined terms:
1. `Quality` → the average of the ratio between query rating and its position

2. `Poor Query Percentage` → the percentage of all queries with rating less than 3

Our task is to calculate the quality and poor quality percentage for each query based on the given conditions.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

2. Calculate the quality and poor quality percentage for each query.

    > `ROUND(number, decimal)` → This function rounds a `number` to a specified number of `decimal` places

    > `AVG()` → This function returns the average value of an expression

    > `SUM()` → This function returns the total sum of a numeric column

    > `IF(condition, value_if_true, value_if_false)` → This function returns a value if a `condition` is `TRUE`, or another value if it is `FALSE`

    > `COUNT()` → This function returns the number of rows

    > Asterisk (`*`) → This symbol specifies that the query should return all columns of the queried tables

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

3. Group the results based on specific columns.

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. The query needs to examine each row to calculate the quality and poor quality percentage for each query.

# Code
```
SELECT 
    query_name,
    ROUND(AVG(rating/position), 2) AS quality,
    ROUND(SUM(IF(rating < 3, 1, 0)) / COUNT(*) * 100, 2) AS poor_query_percentage
FROM Queries
GROUP BY query_name;
```
