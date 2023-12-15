# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find movies with odd-numbered IDs and non-boring descriptions.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

    > Asterisk (`*`) → This symbol specifies that the query should return all columns of the queried tables

2. Check if they meet the given conditions.

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

    > Modulo (`%`)  → This operator returns the remainder of a number divided by another number

    > `!=`  → This operator compares if one value is not equal to another value

    > `AND` → This operator filters records based on more than one condition

3. Arrange the results based on specific columns.

    > `ORDER BY` → This command sorts the result-set in ascending (smallest to largest) order by default

    > `DESC` → This keyword sorts the records in descending (largest to smallest) order

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes each row in the table once to check the conditions.

# Code
```
SELECT * FROM Cinema
WHERE id%2 != 0 AND description!="boring"
ORDER BY rating DESC
```
