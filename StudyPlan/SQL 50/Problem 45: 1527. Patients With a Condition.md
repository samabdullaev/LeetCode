# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find patients with Type I Diabetes.

- Type I Diabetes always starts with `DIAB1` prefix.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

    > Asterisk (`*`) → This symbol specifies that the query should return all columns of the queried tables

2. Filter the results to include only those patients with `DIAB1` prefix.

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

    > `OR` → This operator displays a record if any of the conditions separated by it are `TRUE`

    > `LIKE` → This operator searches for a specified pattern in a column

    > `%` → This symbol (wildcard) matches any sequence of characters

    > `wildcard characters` → These characters are used to substitute one or more characters in a string

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes each row in the table to check the conditions.

# Code
```
# Write your MySQL query statement below
SELECT *
FROM Patients
WHERE conditions LIKE '% DIAB1%' OR 
      conditions LIKE 'DIAB1%'
```
