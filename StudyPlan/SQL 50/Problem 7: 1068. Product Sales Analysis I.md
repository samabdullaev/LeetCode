# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to retrieve specified rows from the database.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

2. Join the second table.

    > `LEFT JOIN` → This command returns all rows from the left table (table 1), and the matching rows from the right table (table 2). The result is `NULL` from the right side, if there is no match.

### Difference Between `USING` and `ON` in SQL Joins

1. The **USING** clause

    > `USING` → This allows to specify the join key by name. It is used if several columns share the same name but you don’t want to join using all of these common columns. The columns can’t have any qualifiers in the statement, including the `WHERE` clause.

2. The **ON** clause

    > `ON` → This allows to specify the column names for join keys in both tables. It is used to join tables where the column names don’t match in both tables. The join conditions are removed from the filter conditions in the `WHERE` clause.

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of records in the table. This is because the query processes each row in the table to find the specified rows.

# Code
```
SELECT product_name, year, price 
FROM Sales 
LEFT JOIN  Product USING (product_id);
```
