# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find managers with at least five direct reports, which can be done by counting the number of employees who have a particular manager. 

# Approach
<!-- Describe your approach to solving the problem. -->
There might be several approaches to solve this problem, but the logic behind all is similar:

1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

    > `AS` → This command renames a column with an alias (temporary name). In most database languages, we can skip the `AS` keyword and get the same result

2. Combine the same table with itself (self-join) to create relationships between employees and their managers.

> `JOIN` / `INNER JOIN` → These commands return records that have matching values in both tables

> `LEFT JOIN` → This command returns all rows from the left table (table 1), and the matching rows from the right table (table 2). The result is `NULL` from the right side, if there is no match.

> `ON` → This allows to specify the column names for join keys in both tables. It is used to join tables where the column names don’t match in both tables.

3. Group the results based on specific columns to count how many employees report to each manager.

> `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

4. Filter managers with 5 or more direct reports.

> `HAVING` → This clause is used with aggregate functions instead of `WHERE` keyword

> `COUNT()` → This function returns the number of rows

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes each row in the table once to count managers with 5 or more direct reports.

# Code
## Solution 1:
```
SELECT e1.name
FROM employee e1
LEFT JOIN employee e2 ON e1.id=e2.managerId
GROUP BY e1.id
HAVING COUNT(e2.name) >= 5;
```

## Solution 2:
```
SELECT a.name 
FROM Employee a 
JOIN Employee b ON a.id = b.managerId 
GROUP BY b.managerId 
HAVING COUNT(*) >= 5
```

## Solution 3:
```
SELECT name 
FROM Employee 
WHERE id IN (
    SELECT managerId 
    FROM Employee 
    GROUP BY managerId 
    HAVING COUNT(*) >= 5)
```

## Solution 4:
```
SELECT e.name
FROM Employee AS e 
INNER JOIN Employee AS m ON e.id=m.managerId 
GROUP BY m.managerId 
HAVING COUNT(m.managerId) >= 5
```

## Solution 5:
```
SELECT emp1.Name 
FROM Employee emp1
JOIN (
  SELECT managerId 
	FROM Employee
	GROUP BY managerId
	HAVING COUNT(managerId) >= 5
) emp2
ON emp1.id = emp2.managerId;
```
