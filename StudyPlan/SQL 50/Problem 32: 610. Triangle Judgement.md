# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find whether the given three line segments can form a triangle.

> `Triangle Inequality Theorem` → for a triangle to be formed, the sum of the lengths of any two sides must be greater than (or equal to) the length of the third side.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

2. Check if the given segments can form a triangle.

    > `IF(condition, value_if_true, value_if_false)` → This function returns a value if a `condition` is `TRUE`, or another value if it is `FALSE`

    > `AND` → This operator filters records based on more than one condition

    > `>` → This operator compares if one value is greater than another value

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes each row in the table once to check the conditions.

# Code
```
SELECT x, y, z, IF(((x+y)>z AND (y+z)>x AND (x+z)>y), "Yes", "No") AS triangle 
FROM Triangle
```
