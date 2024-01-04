# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find all numbers that appear at least 3 times consecutively in the given table.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select unique consecutive numbers from the result table.

    > `SELECT` → This command retrieves data from a database

    > `DISTINCT` → This statement returns only distinct (different) values

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

2. Self join table to link numbers in all three rows (`l1` represents the current row, `l2.id + 1` represents the next row, `l3.id + 2` represents the row that comes after the next row).

    > `JOIN` → This command returns records that have matching values in both tables

    > `ON` → This allows to specify the column names for join keys in both tables. It is used to join tables where the column names don’t match in both tables.

3. Check if the number in the current row is the same as the number in the two consecutive rows.

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

    > `AND` → This operator filters records based on more than one condition

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes each row in the table to find all numbers that appear at least 3 times consecutively.

# Code
```
SELECT DISTINCT l1.num AS ConsecutiveNums
FROM Logs l1
JOIN Logs l2 ON l1.id = l2.id + 1
JOIN Logs l3 ON l1.id = l3.id + 2
WHERE l1.num = l2.num AND l2.num = l3.num;
```
