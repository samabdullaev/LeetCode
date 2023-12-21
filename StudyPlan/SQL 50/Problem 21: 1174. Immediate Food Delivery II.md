# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Pre-defined terms:
1. `Immediate` → the order which has the same order date as customer's preferred delivery date
2. `Scheduled` → the order which doesn't have the same order date as customer's preferred delivery date

Our task is to calculate the percentage of `immediate` orders in the first orders of all customers.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

2. Calculate the number and percentage of `immediate` orders in the first orders.

    > `ROUND(number, decimal)` → This function rounds a `number` to a specified number of `decimal` places

    > `SUM()` → This function returns the total sum of a numeric column

    >         CASE
    >             WHEN conditionN THEN resultN
    >             ELSE result
    >         END;
    > This expression returns the `resultN` when the `conditionN` is met (like an if-then-else statement). So, once a condition is `TRUE`, it will stop reading and return the `resultN`. If no conditions are `TRUE`, it returns the value in the `ELSE` clause. If there is no `ELSE` part and no conditions are `TRUE`, it returns `NULL`

    > `COUNT()` → This function returns the number of rows

    > Asterisk (`*`) → This symbol specifies that the query should return all columns of the queried tables

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result


3. Find the earliest order date and preferred delivery date for each customer.
    > `MIN()` → This function returns the smallest value of the selected column

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. The query needs to examine each row to calculate the percentage of `immediate` orders in the first orders of all customers.

# Code
```
SELECT ROUND(100 * SUM(
    CASE 
        WHEN b.min_order_date = b.min_delivery_date THEN 1 
        ELSE 0 
    END
) / COUNT(*), 2) AS immediate_percentage
FROM (
    SELECT 
        MIN(order_date) AS min_order_date, 
        MIN(customer_pref_delivery_date) AS min_delivery_date
    FROM delivery
    GROUP BY customer_id
) b;
```
