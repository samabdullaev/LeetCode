# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find how many times each student attended each exam.

# Approach
<!-- Describe your approach to solving the problem. -->


1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

2. Count how many times each student attended each exam.

    > `COUNT()` → This function returns the number of rows

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

3. Combine other tables to include all students and subjects, even if they didn't attend any exams.

    > `JOIN` → This command returns records that have matching values in both tables

    > `LEFT JOIN` → This command returns all rows from the left table (table 1), and the matching rows from the right table (table 2). The result is `NULL` from the right side, if there is no match.

    > `ON` → This allows to specify the column names for join keys in both tables. It is used to join tables where the column names don’t match in both tables.

    > `AND` → This operator filters records based on more than one condition

4. Group and arrange the results based on specific columns.

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

    > `ORDER BY` → This command sorts the result-set in ascending (smallest to largest) order

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes each row in the table once to count the number of times each student attended each exam.

# Code
```
SELECT 
    s.student_id, 
    s.student_name, 
    u.subject_name, 
    COUNT(e.subject_name) AS attended_exams
FROM Students s
JOIN Subjects u
LEFT JOIN Examinations e ON s.student_id = e.student_id AND u.subject_name = e.subject_name
GROUP BY s.student_id, u.subject_name
ORDER BY s.student_id, u.subject_name;
```
