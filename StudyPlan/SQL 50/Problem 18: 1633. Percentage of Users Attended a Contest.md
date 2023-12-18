# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find the percentage of the users registered in each contest. To find this, we can count the number of users registered for each contest and divide it by the total number of users.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

2. Calculate the percentage for each contest.

    > `COUNT()` → This function returns the number of rows

    > Asterisk (`*`) → This symbol specifies that the query should return all columns of the queried tables

    > `ROUND(number, decimal)` → This function rounds a `number` to a specified number of `decimal` places

3. Group and arrange the results based on specific columns.

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

    > `ORDER BY` → This command sorts the result-set in ascending (smallest to largest) order by default

    > `DESC` → This keyword sorts the records in descending (largest to smallest) order

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes each row in the table once to calculate the percentage of users registered in each contest.

# Code
```
SELECT 
    r.contest_id, 
    ROUND(COUNT(r.user_id) / (SELECT COUNT(*) FROM users) * 100, 2) AS percentage
FROM Register r
GROUP BY r.contest_id
ORDER BY percentage DESC, r.contest_id
```
