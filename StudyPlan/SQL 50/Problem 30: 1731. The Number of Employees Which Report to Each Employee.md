# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Pre-defined term:
- `Manager` → an employee who has at least 1 other employee reporting to them.

We need to find the number of employees who report directly to each `manager`, along with the average age of those employees.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

2. Count the number and average age of reports for each manager.
    > `COUNT()` → This function returns the number of rows

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

    > `ROUND(number, decimal)` → This function rounds a `number` to a specified number of `decimal` places. If `decimal` omitted, it rounds a `number` to the nearest integer

3. Self join table to link managers and employees (`emp1` represents the `managers`, and `emp2` represents the `employees` reporting to those managers).

    > `JOIN` / `INNER JOIN` → These commands return records that have matching values in both tables

    > `ON` → This allows to specify the column names for join keys in both tables. It is used to join tables where the column names don’t match in both tables.

4. Group and arrange the results to display employees reporting to each manager.

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

    > `ORDER BY` → This command sorts the result-set in ascending (smallest to largest) order by default

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes each row in the table once to find the number of employees who report directly to each manager.

# Code
```
SELECT
    emp1.employee_id,
    emp1.name,
    COUNT(emp2.employee_id) AS reports_count,
    ROUND(AVG(emp2.age)) AS average_age
FROM Employees emp1
INNER JOIN Employees emp2 ON emp1.employee_id = emp2.reports_to
GROUP BY emp1.employee_id
ORDER BY emp1.employee_id
```
