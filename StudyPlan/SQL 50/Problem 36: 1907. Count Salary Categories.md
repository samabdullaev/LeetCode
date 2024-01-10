# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to categorize each account's income and count the number of accounts in each category.

Salary categories:
- `Low Salary` → salaries strictly less than `20000`

- `Average Salary` → salaries between `20000` and `50000` (inclusive)

- `High Salary` → salaries strictly greater than `50000`

# Approach
<!-- Describe your approach to solving the problem. -->
1. Find the number of all accounts in all 3 salary categories.

    > `SELECT` → This command retrieves data from a database

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

    > `COUNT()` → This function returns the number of rows

    > Asterisk (`*`) → This symbol specifies that the query should return all columns of the queried tables

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

    > `<` → This operators compares if one value is less than another value

    > `>=` → This operator compares if one value is greater than or equal to another value

    > `AND` → This operator filters records based on more than one condition

2. Combine all result sets to show the total number of accounts in each of the three salary categories in one table.

    > `UNION` → This operator combines the result-set of two or more `SELECT` statements (every `SELECT` statement must have the same number/data type/order of columns)

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes each row in the table to count the number of accounts in each salary category.

# Code
```
(SELECT "Low Salary" AS category, COUNT(*) AS accounts_count FROM Accounts WHERE income < 20000)
UNION
(SELECT "Average Salary" AS category, COUNT(*) AS accounts_count FROM Accounts WHERE 20000 <= income AND income <= 50000)
UNION
(SELECT "High Salary" AS category, COUNT(*) AS accounts_count FROM Accounts WHERE 50000 < income)
```
