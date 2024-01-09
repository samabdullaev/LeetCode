# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find the most recent prices of all products at a specific date, with the assumption that the price of all products before any change is 10.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Find the most recent price change for all products as of the given date.

    > `SELECT` → This command retrieves data from a database

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

    > `IN` → This operator allows to specify multiple values

    > `MAX()` → This function returns the maximum value in a set of values

    > `<=` → This operator compares if one value is less than or equal to another value

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

2. Find products with no price changes before the given date and assign a default price of 10 to these products.

    > `DISTINCT` → This statement returns only distinct (different) values

    > `NOT IN` → This operator returns all records that are `NOT` any of the values in the list

3. Combine these two sets of results into a single table, providing the prices of all products on `2019-08-16`.

    > `UNION` → This operator combines the result-set of two or more `SELECT` statements (every `SELECT` statement must have the same number/data type/order of columns)

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes each row in the table to find the most recent prices of all products at a given date.

# Code
```
SELECT product_id, new_price AS price 
FROM Products
WHERE (product_id, change_date) IN (
    SELECT product_id, MAX(change_date) 
    FROM Products
    WHERE change_date <= '2019-08-16'
    GROUP BY product_id
)
UNION
SELECT DISTINCT product_id, 10 AS price 
FROM Products
WHERE product_id NOT IN (
    SELECT product_id 
    FROM Products
    WHERE change_date <= '2019-08-16'
);
```
