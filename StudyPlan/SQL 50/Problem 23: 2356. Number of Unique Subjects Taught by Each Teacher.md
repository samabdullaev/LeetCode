# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find how many unique subjects each university teacher teaches.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.
    > `AS` → This command renames a column with an alias.

2. Count the number of unique values.
    > `COUNT()` → This function returns the number of rows.

    > `DISTINCT` → This statement returns only distinct (different) values.

3. Group the results based on specific columns.
    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them.

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the total number of rows in the table. This is because we process each row in the table once.

# Code
```
SELECT 
    teacher_id, 
    COUNT(DISTINCT subject_id) AS cnt
FROM Teacher
GROUP BY teacher_id;
```
