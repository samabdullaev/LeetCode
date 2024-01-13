# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to calculate the sum of all total investment values in 2016 `tiv_2016` for policyholders who meet two criteria:

1. Have the same `tiv_2015` value as one or more other policyholders

2. Are not located in the same city as any other policyholder

# Approach
<!-- Describe your approach to solving the problem. -->
1. Find the `tiv_2015` values that have more than one occurrence in the table.

    > `SELECT` → This command retrieves data from a database

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

    > `HAVING` → This clause allows filtering of aggregated results produced by `GROUP BY` clause (`WHERE` keyword cannot be used with aggregate functions)

    > `COUNT()` → This function returns the number of rows

    > Asterisk (`*`) → This symbol specifies that the query should return all columns of the queried tables

    > `>` → This operator compares if one value is greater than another value

2. Find the unique pairs to include policyholders located in unique cities.

    > `AND` → This operator filters records based on more than one condition

    > `=` → This operator compares if one value is equal to another value

3. Filter the rows to select the rows meeting the first and the second criteria. 

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

    > `IN` → This operator allows to specify multiple values

4. Calculate the sum of `tiv_2016` values for these filtered rows.

    > `ROUND(number, decimal)` → This function rounds a `number` to a specified number of `decimal` places

    > `SUM()` → This function returns the total sum of a numeric column

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes all the rows in the table to count the sum of all total investment values in 2016.

# Code
```
SELECT ROUND(SUM(tiv_2016), 2) AS tiv_2016
FROM insurance
WHERE tiv_2015 IN 
    (SELECT tiv_2015 FROM insurance GROUP BY tiv_2015 HAVING COUNT(*) > 1)
AND (lat, lon) IN 
    (  SELECT lat, lon FROM insurance GROUP BY lat, lon HAVING COUNT(*) = 1)
```
