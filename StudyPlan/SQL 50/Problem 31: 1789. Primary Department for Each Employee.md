# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Pre-defined term:
- `Primary department` → the department to which the employee belongs

There are two types of employees:
1. Employees who belong to only one department.
    > `primary_flag = 'N'` → the only department for the employee

2. Employees who belong to multiple departments.

    > `primary_flag = 'Y'` → the department is primary for the employee
    > `primary_flag = 'N'` → the department is not the primary

###### Our task is to find the primary department for each employee.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Find the primary department for employees who belong to multiple departments.

    > `SELECT` → This command retrieves data from a database

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

2. Find employees who belong to only one department.

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

    > `HAVING` → This clause allows filtering of aggregated results produced by `GROUP BY` clause (`WHERE` keyword cannot be used with aggregate functions)

    > `COUNT()` → This function returns the number of rows

3. Combine the results to provide the list of all employees with their primary department.

    > `UNION` → This operator combines the result-set of two or more `SELECT` statements (every `SELECT` statement must have the same number/data type/order of columns)

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes each row in the table to find the primary department for each employee.

# Code
```
SELECT employee_id, department_id FROM Employee WHERE primary_flag = 'Y'
UNION
SELECT employee_id, department_id FROM Employee
GROUP BY employee_id
HAVING COUNT(department_id) = 1;
```
