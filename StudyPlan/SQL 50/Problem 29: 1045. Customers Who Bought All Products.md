# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find customers who bought all the products in the given table.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Find the total number of distinct products in the `Product` table.

    > `SELECT` → This command retrieves data from a database

    > `COUNT()` → This function returns the number of rows

    > `DISTINCT` → This statement returns only distinct (different) values

2. Filter the customers who have bought the same count of products as the total distinct products.

    > `HAVING` → This clause allows filtering of aggregated results produced by `GROUP BY` clause (`WHERE` keyword cannot be used with aggregate functions)

3. Group the results by customer id to identify customers who bought all the products.

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes each row in the table once to find customers who bought all the products.

# Code
```
SELECT customer_id 
FROM Customer
GROUP BY customer_id
HAVING COUNT(DISTINCT product_key) = (
    SELECT COUNT(DISTINCT product_key) 
    FROM Product
);
```
