# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find the number of transactions and their total amount, as well as the number of approved transactions and their total amount for each month and country.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

2. Calculate the count and total amount of all transactions & approved transactions.

    > `DATE_FORMAT(date, format)` → This function formats a `date` in the specified `format`

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

    > `COUNT()` → This function returns the number of rows

    > Asterisk (`*`) → This symbol specifies that the query should return all columns of the queried tables

    > `SUM()` → This function returns the total sum of a numeric column

    > `IF(condition, value_if_true, value_if_false)` → This function returns a value if a `condition` is `TRUE`, or another value if it is `FALSE`

3. Group the results based on specific columns.

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. The query needs to examine each row to calculate the aggregate values for each group.

# Code
```
SELECT 
    DATE_FORMAT(trans_date, '%Y-%m') AS month, 
    country, 
    COUNT(*) AS trans_count,
    SUM(IF(state = 'approved', 1, 0)) AS approved_count, 
    SUM(amount) AS trans_total_amount,
    SUM(IF(state = 'approved', amount, 0)) AS approved_total_amount
FROM Transactions
GROUP BY DATE_FORMAT(trans_date, '%Y-%m'), country;
```
