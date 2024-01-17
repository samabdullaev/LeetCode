# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find the name and the amount of products with at least 100 units ordered in February 2020.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

2. Calculate the total units ordered.

    > `SUM()` → This function calculates the sum of a set of values

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

3. Combine the other table to link each product with its corresponding order data.

    > `LEFT JOIN` → This command returns all rows from the left table (table 1), and the matching rows from the right table (table 2). The result is `NULL` from the right side, if there is no match.

    #### Difference Between `USING` and `ON` in SQL Joins
    1. The **USING** clause
        > `USING` → This allows to specify the join key by name. It is used if several columns share the same name but you don’t want to join using all of these common columns. The columns can’t have any qualifiers in the statement, including the `WHERE` clause.

    2. The **ON** clause
        > `ON` → This allows to specify the column names for join keys in both tables. It is used to join tables where the column names don’t match in both tables. The join conditions are removed from the filter conditions in the `WHERE` clause.

4. Filter to include only orders from February 2020.

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

    > `MONTH(date)` → This function returns the month part for a given `date` (a number from 1 to 12)

    > `=` → This operator compares if one value is equal to another value

    > `AND` → This operator filters records based on more than one condition

    > `YEAR(date)` → This function returns the year part for a given `date` (a number from 1000 to 9999)

5. Group the results by `product_name` to obtain the total order quantity for each product.

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

6. Choose products with a total order quantity of at least 100 units.

    > `HAVING` → This clause allows filtering of aggregated results produced by `GROUP BY` clause (`WHERE` keyword cannot be used with aggregate functions)

    > `>=` → This operator compares if one value is greater than or equal to another value

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of records in the table. This is because the query processes each row in the table to perform the join, filter and group operations.

# Code
```
SELECT 
    p.product_name, 
    SUM(o.unit) AS unit 
FROM Products p
LEFT JOIN Orders o USING(product_id)
WHERE MONTH(o.order_date) = '02' AND YEAR(o.order_date) = '2020'
GROUP BY p.product_name
HAVING SUM(o.unit) >= 100
```
