# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find the second highest salary (`NULL` if there is no second highest salary) from the given table.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

2. Find the highest salary in the table.

    > `MAX()` → This function returns the maximum value in a set of values

3. Exclude the highest salary and get the second highest salary.

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

    > `NOT IN` → This operator returns all records that are `NOT` any of the values in the list

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query needs to scan through all the rows in the given table to find the maximum salary.

# Code
```
SELECT MAX(Salary) AS SecondHighestSalary 
FROM Employee
WHERE Salary NOT IN (
    SELECT MAX(Salary) FROM Employee
)
```
