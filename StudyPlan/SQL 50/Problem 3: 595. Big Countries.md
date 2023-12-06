# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find countries that meet the specified conditions.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

2. Check if they meet the given conditions.

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

    > `OR` → This operator displays a record if any of the conditions separated by it are `TRUE`

    > `>=` → This operator compares if one value is greater than or equal to another value

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query examines each row in the table once to check the conditions.

# Code
```
SELECT name, population, area
FROM World
WHERE area >= 3000000 OR population >= 25000000
```
