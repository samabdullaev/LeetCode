# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to calculate the moving average of how much the customer paid in a seven-day window, which includes the current day and the six days before.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select unique visit dates where the time span between the chosen date and the earliest visit date is at least 6 days.

    > `SELECT` → This command retrieves data from a database

    > `DISTINCT` → This statement returns only distinct (different) values

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

    > `DATEDIFF(date1, date2)` → This function returns the number of days between two date values

    > `MIN()` → This function returns the smallest value of the selected column

    > `>=` → This operator compares if one value is greater than or equal to another value

2. Combine these selected dates with customer data, including the amount they paid on each visit.

    > `LEFT JOIN` → This command returns all rows from the left table (table 1), and the matching rows from the right table (table 2). The result is `NULL` from the right side, if there is no match.

    > `ON` → This allows to specify the column names for join keys in both tables. It is used to join tables where the column names don’t match in both tables.

    > `BETWEEN` → This operator selects values within a given range (it is inclusive: begin and end values are included)

    > `AND` → This operator filters records based on more than one condition

3. Calculate the total payment amount for each group of customers who visited within a 7-day window.

    > `SUM()` → This function returns the total sum of a numeric column

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

4. Find the average payment for each group of customers.

    > `x / y` → This operator is used for integer division (`x` is divided by `y`)

    > `ROUND(number, decimal)` → This function rounds a `number` to a specified number of `decimal` places

5. Group and sort the results by visit date in ascending order.

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

    > `ORDER BY` → This command sorts the result-set in ascending (smallest to largest) order by default

# Complexity
- Time complexity: $O(n^2)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query scans through all the rows in the tables to calculate the moving average of how much the customer paid in a seven-day window.

# Code
```
SELECT 
    visits.visited_on AS visited_on,
    SUM(c.amount) AS amount, 
    ROUND(SUM(c.amount) / 7.0, 2) AS average_amount
FROM (
    SELECT DISTINCT visited_on 
    FROM Customer
    WHERE DATEDIFF(
        visited_on, 
        (SELECT MIN(visited_on) FROM Customer)
    ) >= 6
) visits 
LEFT JOIN Customer c 
ON DATEDIFF(visits.visited_on, c.visited_on) BETWEEN 0 and 6
GROUP BY visits.visited_on
ORDER BY visited_on;
```
