# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find the IDs of products that are both low fat and recyclable.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select the IDs of the products.

    > `SELECT` → This command retrieves data from a database

2. Check if the product is both low fat and recyclable.

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

    > `=` → This operator compares if one value is equal to another value

    > `AND` → This operator filters records based on more than one condition

3. Return the IDs of products that meet both of these criteria.

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. The query needs to examine each row to determine if it meets the conditions.

# Code
```
SELECT product_id
FROM Products
WHERE low_fats = 'Y' AND recyclable = 'Y';
```
