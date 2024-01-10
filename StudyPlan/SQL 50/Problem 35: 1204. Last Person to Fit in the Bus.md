# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Pre-defined term:
- `Bus weight limit = 1000 kilograms`

We need to find the last person who can fit on the bus without exceeding the weight limit.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

2. Calculate the cumulative weight of people, starting from the current person's turn.

    > `SUM()` → This function calculates the sum of a set of values

3. Check if the cumulative weight doesn't exceed the weight limit.

    > `WHERE` → This command filters a result set to include only records that fulfill a specified condition

    > `>=` → This operator compares if one value is greater than or equal to another value

4. Arrange the results based on people's turn to find the last eligible person who can board the bus without exceeding the weight limit.

    > `ORDER BY` → This command sorts the result-set in ascending (smallest to largest) order by default

    > `DESC` → This keyword sorts the records in descending (largest to smallest) order

    > `LIMIT` → This clause specifies the number of records to return

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes each row in the table once to calculate and check cumulative weights.

# Code
```
SELECT person_name 
FROM Queue q
WHERE 1000 >= (
    SELECT SUM(weight) 
    FROM Queue 
    WHERE q.turn >= turn
)
ORDER BY turn DESC 
LIMIT 1;
```
