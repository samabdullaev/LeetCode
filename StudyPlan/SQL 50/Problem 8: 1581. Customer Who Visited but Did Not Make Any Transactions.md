# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find the number of times customers visited and did not make any transactions.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

2. Count how many visits for each customer doesn't have corresponding transactions.

    > `COUNT()` → This function returns the number of rows

    > `AS` → This command renames a column with an alias

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

    > `NOT IN` → This command returns all records that are `NOT` any of the values in the list

4. Group the results based on specific columns.

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them.

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. It is proportional to the number of rows because it scans all visit records once.

# Code
```
SELECT 
    customer_id, 
    COUNT(visit_id) AS count_no_trans 
FROM visits
WHERE visit_id NOT IN (
    SELECT visit_id 
    FROM transactions
)
GROUP BY customer_id
```
