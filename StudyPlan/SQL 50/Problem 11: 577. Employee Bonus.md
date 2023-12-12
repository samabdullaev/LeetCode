# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find the names and bonus amounts of employees with a bonus less than 1000.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

2. Join the second table.

    > `LEFT JOIN` → This command returns all rows from the left table (table 1), and the matching rows from the right table (table 2). The result is `NULL` from the right side, if there is no match.

    > `ON` → This allows to specify the column names for join keys in both tables. It is used to join tables where the column names don’t match in both tables.

3. Check if they meet the given conditions.

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

    > `<` → This operator compares if one value is less than another value

    > `IS NULL` → This operator tests for empty (`NULL`) values

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query examines each row in the table once to check the conditions.

# Code
```
SELECT name, bonus
FROM Employee
LEFT JOIN Bonus ON Employee.empId=Bonus.empId
WHERE Bonus.bonus < 1000 OR Bonus.bonus IS NULL;
```
