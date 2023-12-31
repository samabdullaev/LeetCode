# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find customers who are not referred by the customer with id = 2. This might include customers who are not referered by anyone (customers with no referee IDs).

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.
    > `SELECT` → This command retrieves data from a database

2. Check if they meet the given conditions.

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

    > `<>` / `!=` →  These operators compare if one value is not equal to another value 

    > `OR` → This operator displays a record if any of the conditions separated by it are `TRUE`

    > `IS NULL` → This operator tests for empty (`NULL`) values


Since the table includes `NULL` values:
- we have to test for those values as well using `IS NULL`
- we have to use `OR` operator to add empty-value test cases (comparison operators, such as `!=`, `<>`, can't test for `NULL` values)

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query examines each row in the table once to check the conditions.

# Code
## Solution 1:
```
SELECT name
FROM Customer
WHERE referee_id <> 2 OR referee_id IS NULL
```

## Solution 2:

```
SELECT name
FROM Customer
WHERE referee_id != 2 OR referee_id IS NULL
```
