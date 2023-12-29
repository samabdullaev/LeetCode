# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Pre-defined term:
- `Single number` → a number that appeared only once in the given table

Our task is to find the largest single number (`NULL` if there is not any)

# Approach
<!-- Describe your approach to solving the problem. -->
1. Find numbers that appear exactly once in the table.

    > `SELECT` → This command retrieves data from a database

    > `COUNT()` → This function returns the number of rows

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

    > `HAVING` → This clause allows filtering of aggregated results produced by `GROUP BY` clause (`WHERE` keyword cannot be used with aggregate functions)

2. Get the largest number among these single numbers.

    > `MAX()` → This function returns the maximum value in a set of values

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes each row in the table once to find the largest single number.

# Code
```
SELECT MAX(num) AS num 
FROM (
    SELECT num 
    FROM MyNumbers
    GROUP BY num
    HAVING COUNT(num) = 1
) AS t;
```
