# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find the product id, year, quantity, and price for the first year of every product sold.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Find the earliest year each product was sold by grouping sales data.

    > `MIN()` → This function returns the smallest value of the selected column

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

2. Select and display product details for those earliest years.

    > `SELECT` → This command retrieves data from a database

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

    > `IN` → This operator allows to specify multiple values

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes each row in the table once to find the first year of every product sold.

# Code
```
SELECT product_id, year AS first_year, quantity, price 
FROM Sales
WHERE (product_id, year) IN (
    SELECT product_id, MIN(year) 
    FROM Sales 
    GROUP BY product_id
);
```
