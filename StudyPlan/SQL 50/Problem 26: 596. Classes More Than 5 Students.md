# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
We need to find classes with at least 5 students.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Select specific columns from the table.

    > `SELECT` → This command retrieves data from a database

2. Check if classes have at least 5 students.

    > `HAVING` → This clause allows filtering of aggregated results produced by `GROUP BY` clause (`WHERE` keyword cannot be used with aggregate functions)

    > `COUNT()` → This function returns the number of rows

    > `DISTINCT` → This statement returns only distinct (different) values

3. Group the results by the class to find the number of students in each class.

    > `GROUP BY` → This command groups rows that have the same values into summary rows, typically to perform aggregate functions on them

# Complexity
- Time complexity: $O(n)$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
`n` is the number of rows in the table. This is because the query processes each row in the table once to count the number of students in each class.

# Code
It is possible to create various combinations of solutions by mixing and matching different elements from the provided solutions.

### Solution 1:
```
SELECT class
FROM courses
GROUP BY class
HAVING COUNT(DISTINCT student) >= 5;
```

### Solution 2:
```
SELECT class
FROM courses
GROUP BY class
HAVING COUNT(student) >= 5;
```

### Solution 3:
```
SELECT class
FROM courses
GROUP BY class
HAVING COUNT(class) >= 5;
```

### Solution 4:
```
SELECT class
FROM courses
GROUP BY class
HAVING COUNT(*) >= 5;
```

### Solution 5:
```
SELECT class
FROM courses
GROUP BY class
HAVING COUNT(class) > 4;
```
