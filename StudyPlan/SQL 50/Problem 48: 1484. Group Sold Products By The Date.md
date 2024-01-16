# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find the name and the number of different products sold on each date.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result


2. Count how many different products were sold on each date.

    > `COUNT()` → This function returns the number of rows

    > `DISTINCT` → This statement returns only distinct (different) values

3. Concatenate the product names in lexicographical order for each date.

    > `GROUP_CONCAT()` → This function concatenates and aggregates values from multiple rows within a specific column into a single string

    > `ORDER BY` → This command sorts the result-set in ascending (smallest to largest) order by default

4. Group and arrange the results to show the number of products sold on each date in chronological order.

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

# Complexity
- Time complexity: $O(n log n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query involves sorting all the products in the worst case.

# Code
```
SELECT 
    sell_date, 
    COUNT(DISTINCT product) AS num_sold,
    GROUP_CONCAT(DISTINCT product ORDER BY product) AS products
FROM Activities
GROUP BY sell_date
ORDER BY sell_date;
```
