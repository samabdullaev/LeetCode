# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find the IDs of dates that had higher temperatures compared to the previous day.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table. Give 2 aliases to the table to refer to the same table multiple times in the same query.
    > `SELECT` → This command retrieves data from a database

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

2. Compare each date with the date one day before.
    > `INTERVAL 1 DAY` → This expression subtracts 1 day from a date. It is used to calculate the date of the previous day

3. Check if the temperature on the current date is higher than on the previous day.
    > `AND` → This operator filters records based on more than one condition

    > `<` → This operators compares if one value is less than another value

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. The query needs to examine each row to determine if it meets the conditions.

# Code
```
SELECT w2.id FROM Weather w1, Weather w2
WHERE w1.recordDate = (w2.recordDate - INTERVAL 1 DAY) AND w1.Temperature < w2.Temperature
```
