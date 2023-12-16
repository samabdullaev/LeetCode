# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find the average selling price for each product, which can be solved by calculating the total price of each product sold and dividing it by the total number of units sold. 

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

2. Calculate the average selling price for each product.

    > `SUM()` → This function returns the total sum of a numeric column

    > `ROUND(number, decimal)` → This function rounds a `number` to a specified number of `decimal` places

    > `IFNULL(expression, alt_value)` → This function returns the `alt_value` if the `expression` is `NULL`

3. Combine other tables to check if the `purchase_date` falls within the date range defined by `start_date` and `end_date`.

    > `LEFT JOIN` → This command returns all rows from the left table (table 1), and the matching rows from the right table (table 2). The result is `NULL` from the right side, if there is no match.

    > `ON` → This allows to specify the column names for join keys in both tables. It is used to join tables where the column names don’t match in both tables.

    > `BETWEEN` → This operator selects values within a given range (it is inclusive: begin and end values are included).

    > `AND` → This operator filters records based on more than one condition

4. Group the results based on specific columns.

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the joined result. This is because the query processes each row in the table once to calculate the average price for each product.

# Code
```
SELECT 
    product_id, 
    IFNULL(ROUND(SUM(prices_sum) / SUM(units), 2), 0) AS average_price
FROM (
    SELECT 
        p.product_id AS product_id, 
        units, 
        price * units AS prices_sum
    FROM Prices p 
    LEFT JOIN UnitsSold u ON p.product_id = u.product_id AND purchase_date BETWEEN start_date AND end_date
    ) AS temp
GROUP BY product_id;
```
