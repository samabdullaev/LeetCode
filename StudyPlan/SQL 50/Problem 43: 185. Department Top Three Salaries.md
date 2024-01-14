# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find the employees who earn the top three unique salaries in each department.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

2. Combine data from two tables to associate employees with their respective departments.

    > `JOIN` → This command returns records that have matching values in both tables

    > `ON` → This allows to specify the column names for join keys in both tables. It is used to join tables where the column names don’t match in both tables.

    > `=` → This operator compares if one value is equal to another value

3. Filter the results to only include employees whose salary ranks in the top three unique salaries within their respective departments.

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

    > `>` → This operator compares if one value is greater than another value

4. Count the number of distinct salaries greater than the salary of each employee within their department. 

    > `COUNT()` → This function returns the number of rows

    > `DISTINCT` → This statement returns only distinct (different) values

    > `AND` → This operator filters records based on more than one condition

# Complexity
- Time complexity: $O(n^2)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes each row in the table to compare the salary of each employee with every other employee in the same department.

# Code
```
SELECT 
    dept.name AS 'Department', 
    emp1.name AS 'Employee', 
    emp1.salary
FROM Employee emp1
JOIN Department dept ON emp1.departmentId = dept.id
WHERE 3 > (
    SELECT COUNT(DISTINCT emp2.salary)
    FROM Employee emp2
    WHERE emp2.salary > emp1.salary AND emp1.departmentId = emp2.departmentId
);
```
