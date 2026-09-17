## Top 50 SQL Interview Questions & Answers
🟢 SQL Basics
1. What is SQL?

Answer:
SQL stands for Structured Query Language. It is used to store, retrieve, manipulate, and analyze data in relational databases.

2. What is a database?

Answer:
A database is an organized collection of data that can be easily stored, accessed, and managed.

3. What is a table?

Answer:
A table stores data in the form of rows and columns.

Example:

SELECT * FROM employees;
4. What is a primary key?

Answer:
A primary key uniquely identifies each row in a table. It cannot contain NULL values and should be unique.

CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    name VARCHAR(100)
);
5. What is a foreign key?

Answer:
A foreign key is a column that creates a relationship between two tables by referring to the primary key of another table.

FOREIGN KEY (department_id)
REFERENCES departments(department_id)
6. What is the difference between DELETE, DROP, and TRUNCATE?

Answer:

Command	Purpose
DELETE	Deletes selected rows
TRUNCATE	Removes all rows
DROP	Removes the entire table

Example:

DELETE FROM employees WHERE employee_id = 10;
TRUNCATE TABLE employees;
DROP TABLE employees;
7. What is NULL in SQL?

Answer:
NULL means the value is missing or unknown. It is different from 0 or an empty string.

To check NULL:

SELECT *
FROM employees
WHERE salary IS NULL;
8. What is the difference between WHERE and HAVING?

Answer:
WHERE filters rows before grouping, while HAVING filters groups after GROUP BY.

SELECT department_id, AVG(salary)
FROM employees
WHERE salary > 30000
GROUP BY department_id
HAVING AVG(salary) > 50000;
9. What is DISTINCT?

Answer:
DISTINCT removes duplicate values from the result.

SELECT DISTINCT department_id
FROM employees;
10. What is an alias?

Answer:
An alias gives a temporary name to a column or table.

SELECT salary AS employee_salary
FROM employees;
🟡 Filtering & Sorting
11. What is the ORDER BY clause?

Answer:
ORDER BY is used to sort query results.

SELECT *
FROM employees
ORDER BY salary DESC;

ASC = ascending
DESC = descending

12. What is the LIMIT clause?

Answer:
LIMIT restricts the number of rows returned.

SELECT *
FROM employees
LIMIT 5;
13. What is the LIKE operator?

Answer:
LIKE is used for pattern matching.

SELECT *
FROM employees
WHERE name LIKE 'Ram%';

% means any number of characters.

14. What is the difference between IN and BETWEEN?

Answer:

IN checks multiple specific values:

WHERE department_id IN (1, 2, 3)

BETWEEN checks a range:

WHERE salary BETWEEN 30000 AND 60000
15. What is CASE in SQL?

Answer:
CASE is used to implement conditional logic.

SELECT name,
       salary,
       CASE
           WHEN salary >= 60000 THEN 'High'
           WHEN salary >= 40000 THEN 'Medium'
           ELSE 'Low'
       END AS salary_category
FROM employees;
🟠 Aggregate Functions
16. What are aggregate functions?

Answer:
Aggregate functions perform calculations on multiple rows.

Common functions:

COUNT()
SUM()
AVG()
MIN()
MAX()

Example:

SELECT AVG(salary)
FROM employees;
17. What is GROUP BY?

Answer:
GROUP BY groups rows having the same values so aggregate functions can be applied.

SELECT department_id, COUNT(*)
FROM employees
GROUP BY department_id;
18. Find the highest salary.
SELECT MAX(salary)
FROM employees;
19. Find the average salary.
SELECT AVG(salary)
FROM employees;
20. Find the number of employees in each department.
SELECT department_id, COUNT(*) AS employee_count
FROM employees
GROUP BY department_id;
🔵 SQL Joins — VERY IMPORTANT

For AI/ML/Data Science interviews, JOIN questions are extremely important.

21. What is a JOIN?

Answer:
A JOIN combines data from multiple tables using a related column.

Example:

SELECT e.name, d.department_name
FROM employees e
JOIN departments d
ON e.department_id = d.department_id;
22. What is an INNER JOIN?

Answer:
It returns only records that have matching values in both tables.

SELECT *
FROM employees e
INNER JOIN departments d
ON e.department_id = d.department_id;
23. What is a LEFT JOIN?

Answer:
It returns all rows from the left table and matching rows from the right table.

SELECT *
FROM employees e
LEFT JOIN departments d
ON e.department_id = d.department_id;

If there is no match, the right-side columns contain NULL.

24. What is a RIGHT JOIN?

Answer:
It returns all rows from the right table and matching rows from the left table.

SELECT *
FROM employees e
RIGHT JOIN departments d
ON e.department_id = d.department_id;
25. What is a FULL OUTER JOIN?

Answer:
It returns all matching and non-matching rows from both tables.

SELECT *
FROM employees e
FULL OUTER JOIN departments d
ON e.department_id = d.department_id;
26. What is a SELF JOIN?

Answer:
A self join joins a table with itself.

For example, finding employees and their managers:

SELECT e.name AS employee,
       m.name AS manager
FROM employees e
JOIN employees m
ON e.manager_id = m.employee_id;
27. What is a CROSS JOIN?

Answer:
A cross join produces every possible combination of rows from two tables.

If table A has 5 rows and table B has 4 rows:

5 × 4 = 20 rows

SELECT *
FROM employees
CROSS JOIN departments;
🔴 Subqueries
28. What is a subquery?

Answer:
A subquery is a query written inside another query.

Example:

SELECT *
FROM employees
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
);

This finds employees earning more than the average salary.

29. Find employees earning more than the average salary.
SELECT name, salary
FROM employees
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
);

This is a very common interview question.

30. What is a correlated subquery?

Answer:
A correlated subquery depends on the outer query and is executed for each row processed by the outer query.

Example:

SELECT e.name, e.salary
FROM employees e
WHERE e.salary > (
    SELECT AVG(e2.salary)
    FROM employees e2
    WHERE e2.department_id = e.department_id
);

This finds employees earning more than their department average.

🟣 Window Functions — VERY IMPORTANT

For your target AI/ML/Data Science roles, learn these properly.

31. What is a window function?

Answer:
A window function performs calculations across related rows without combining them into a single row.

Example:

SELECT name,
       salary,
       AVG(salary) OVER() AS average_salary
FROM employees;
32. What is ROW_NUMBER()?

Answer:
ROW_NUMBER() assigns a unique sequential number to each row.

SELECT name,
       salary,
       ROW_NUMBER() OVER(ORDER BY salary DESC) AS rank_no
FROM employees;
33. What is RANK()?

Answer:
RANK() assigns the same rank to tied values but leaves gaps after ties.

Example:

Salary    Rank
100000     1
90000      2
90000      2
80000      4
34. What is DENSE_RANK()?

Answer:
DENSE_RANK() also gives the same rank to tied values but does not leave gaps.

Salary    Rank
100000     1
90000      2
90000      2
80000      3
35. Difference between ROW_NUMBER, RANK, and DENSE_RANK?

Answer:

Function	Handles ties	Gaps
ROW_NUMBER()	No same rank	No
RANK()	Same rank	Yes
DENSE_RANK()	Same rank	No
36. Find the second-highest salary.

One approach:

SELECT salary
FROM (
    SELECT salary,
           DENSE_RANK() OVER (ORDER BY salary DESC) AS rnk
    FROM employees
) x
WHERE rnk = 2;
37. Find the top 3 salaries in each department.
SELECT *
FROM (
    SELECT name,
           department_id,
           salary,
           DENSE_RANK() OVER (
               PARTITION BY department_id
               ORDER BY salary DESC
           ) AS rnk
    FROM employees
) x
WHERE rnk <= 3;

Important concept: PARTITION BY.

38. What is PARTITION BY?

Answer:
PARTITION BY divides the data into groups for a window function without actually grouping the rows.

AVG(salary) OVER (
    PARTITION BY department_id
)

This calculates the average salary separately for each department.

🟤 CTEs
39. What is a CTE?

Answer:
CTE stands for Common Table Expression. It creates a temporary named result that can be used within a query.

WITH high_salary AS (
    SELECT *
    FROM employees
    WHERE salary > 60000
)
SELECT *
FROM high_salary;
40. Why do we use CTEs?

Answer:
CTEs make complex SQL queries easier to read, maintain, and debug.

They are especially useful when working with multiple steps of data transformation.

🟢 Intermediate SQL
41. What is a view?

Answer:
A view is a virtual table based on a SQL query.

CREATE VIEW employee_view AS
SELECT name, salary
FROM employees;

Then:

SELECT *
FROM employee_view;
42. What is an index?

Answer:
An index improves the speed of data retrieval from a table.

CREATE INDEX idx_employee_name
ON employees(name);

However, indexes require additional storage and can make INSERT, UPDATE, and DELETE operations more expensive.

43. What is normalization?

Answer:
Normalization is the process of organizing data to reduce redundancy and improve data integrity.

Common normal forms include:

1NF
2NF
3NF
BCNF

For a one-year role, you should understand 1NF, 2NF, and 3NF clearly.

44. What is denormalization?

Answer:
Denormalization intentionally introduces some redundancy to improve read/query performance.

It is commonly used in analytical systems where fast reads are important.

45. What is a transaction?

Answer:
A transaction is a group of database operations treated as a single unit.

Example:

BEGIN;

UPDATE accounts
SET balance = balance - 1000
WHERE id = 1;

UPDATE accounts
SET balance = balance + 1000
WHERE id = 2;

COMMIT;
46. What is ACID?

Answer:
ACID represents four properties of reliable database transactions:

Atomicity — all operations succeed or none do.
Consistency — data remains valid.
Isolation — transactions don't improperly interfere with each other.
Durability — committed changes are preserved.
🔥 Practical Interview Questions
47. Find duplicate records.

Suppose you want to find duplicate email addresses:

SELECT email, COUNT(*) AS count
FROM employees
GROUP BY email
HAVING COUNT(*) > 1;
48. Find employees who don't belong to any department.
SELECT e.*
FROM employees e
LEFT JOIN departments d
ON e.department_id = d.department_id
WHERE d.department_id IS NULL;

This is a common JOIN interview problem.

49. Find the highest salary in each department.
SELECT department_id, MAX(salary) AS highest_salary
FROM employees
GROUP BY department_id;

If they ask for the employee details as well:

SELECT *
FROM (
    SELECT e.*,
           RANK() OVER (
               PARTITION BY department_id
               ORDER BY salary DESC
           ) AS rnk
    FROM employees e
) x
WHERE rnk = 1;
50. Find employees whose salary is greater than their department's average salary.

This is an excellent interview question because it combines subqueries/window functions.

Using a window function:

SELECT *
FROM (
    SELECT e.*,
           AVG(salary) OVER (
               PARTITION BY department_id
           ) AS dept_avg_salary
    FROM employees e
) x
WHERE salary > dept_avg_salary;
