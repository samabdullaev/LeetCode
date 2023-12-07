# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find all the authors who viewed their own articles.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

    > `DISTINCT` → This statement returns only distinct (different) values

    > `AS` → This command renames a column with an alias (temporary name)

2. Check if they meet the given conditions.

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

3. Arrange the results based on specific columns.

    > `ORDER BY` → This command sorts the result-set in ascending (smallest to largest) order 

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query examines each row in the table once to check the conditions.

# Code
```
SELECT DISTINCT author_id AS id
FROM Views
WHERE author_id = viewer_id
ORDER BY id
```
