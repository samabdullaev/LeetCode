# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to swap the seat IDs of every two consecutive students, keeping the last student's ID unchanged if the number of students is odd.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

2. Determine the new seat ID for each student:
   - If they have the maximum ID and the total number of students is odd, keep their seat ID the same.
   - If their seat ID is odd (`id MOD 2 = 1`), add 1 to it to swap with the next student.
   - If their seat ID is even (`id MOD 2 = 0`), subtract 1 from it to swap with the previous student.

    >         CASE
    >             WHEN conditionN THEN resultN
    >             ELSE result
    >         END;
    > This expression returns the `resultN` when the `conditionN` is met (like an if-then-else statement). So, once a condition is `TRUE`, it will stop reading and return the `resultN`. If no conditions are `TRUE`, it returns the value in the `ELSE` clause. If there is no `ELSE` part and no conditions are `TRUE`, it returns `NULL`

    > `=` → This operator compares if one value is equal to another value

    > `MAX()` → This function returns the maximum value in a set of values

    > `x MOD y` → This function returns the remainder of `x` divided by `y`

    > `AND` → This operator filters records based on more than one condition

3. Arrange the results based on specific columns.

    > `ORDER BY` → This command sorts the result-set in ascending (smallest to largest) order by default

## Solution 2

We first find the total number of students and perform the necessary calculations to swap the seat IDs of every two consecutive students.

> `MOD(x, y)` → This function returns the remainder of `x` divided by `y`

> `!=` → This operator compares if one value is not equal to another value

> `COUNT()` → This function returns the number of rows

> Asterisk (`*`) → This symbol specifies that the query should return all columns of the queried tables

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of records in the table. This is because the query needs to scan through all the rows in the given table to calculate the maximum id and perform the necessary calculations for each row.

# Code
### Solution 1:
```
SELECT 
CASE
  WHEN (id = (SELECT MAX(id) FROM Seat) AND id MOD 2 = 1) THEN id
  WHEN (id MOD 2 = 1) THEN id+1
  WHEN (id MOD 2 = 0) THEN id-1
END AS id, student
FROM Seat
ORDER BY id;
```

### Solution 2:
```
SELECT 
    (CASE
        WHEN MOD(id, 2) != 0 AND counts != id THEN id + 1
        WHEN MOD(id, 2) != 0 AND counts = id THEN id
    ELSE id - 1
    END) AS id, 
    student
FROM seat, (SELECT COUNT(*) AS counts FROM seat) AS seat_counts
ORDER BY id;
```
