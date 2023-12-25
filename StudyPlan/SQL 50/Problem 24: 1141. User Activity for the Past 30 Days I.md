# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Pre-defined term:
1. `Active` → a user is considered `active` if they made at least one activity on that day.

Our task is to find the count of daily active users for a period of 30 days ending on a specific date.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

2. Count the number of active users.

    > `COUNT()` → This function returns the number of rows

    > `DISTINCT` → This statement returns only distinct (different) values

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

3. Filter the rows where the date is within the range of the last 30 days.

    > `BETWEEN` → This operator selects values within a given range (begin and end values are included)

    > `DATE_ADD(date, INTERVAL value addunit)` → This function returns the added `unit value interval` to the given `date`

    > `AND` → This operator filters records based on more than one condition

4. Group the results by date to get the count of active users for each day.

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. The query needs to examine each row to calculate the count of distinct active users for each day.

# Code
```
SELECT
    activity_date AS day,
    COUNT(DISTINCT user_id) AS active_users
FROM Activity
WHERE activity_date BETWEEN DATE_ADD('2019-07-27', INTERVAL -29 day) AND '2019-07-27'
GROUP BY activity_date
```
