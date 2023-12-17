# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find the average experience years of employees for each project.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database
    
    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

2. Calculate the average experience years of all employees for each project.

    > `ROUND(number, decimal)` → This function rounds a `number` to a specified number of `decimal` places

    > `AVG()` → This function returns the average value of an expression

3. Combine the other table to include all projects.

    > `LEFT JOIN` → This command returns all rows from the left table (table 1), and the matching rows from the right table (table 2). The result is NULL from the right side, if there is no match.

    > `ON` → This allows to specify the column names for join keys in both tables. It is used to join tables where the column names don’t match in both tables.

4. Group the results based on specific columns.

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the joined result. This is because the query processes each row in the table once to calculate the average experience years for each project.

# Code
```
SELECT project_id, ROUND(AVG(experience_years), 2) AS average_years
FROM Project p
LEFT JOIN Employee e ON p.employee_id=e.employee_id
GROUP BY project_id;
```
