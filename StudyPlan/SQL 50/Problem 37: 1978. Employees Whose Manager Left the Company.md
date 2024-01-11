# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find employees with a salary less than 30,000 whose managers have left the company.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

2. Filter employees based on a salary condition and exclude employees whose managers are still in the company.

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

    > `<` → This operators compares if one value is less than another value

    > `AND` → This operator filters records based on more than one condition

    > `NOT IN` → This operator returns all records that are `NOT` any of the values in the list

3. Group and arrange the results based on the `employee_id` to obtain the final list of employees meeting the specified criteria.

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

    > `ORDER BY` → This command sorts the result-set in ascending (smallest to largest) order by default

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes each row in the table to find employees who meet the specified criteria.

# Code
```
SELECT e.employee_id 
FROM Employees e 
WHERE e.salary < 30000 AND e.manager_id NOT IN (
    SELECT m.employee_id 
    FROM Employees m)
GROUP BY e.employee_id 
ORDER BY e.employee_id
```
