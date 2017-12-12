# Data Management Systems

[Lecture 6 - SQL Complex Queries, Triggers, Views and Schema Modification ](#Lecture6)
<br>
[Lecture 7 - SQL Programming Techniques ](#Lecture7)
<br>
[Lecture 8 - Web Database Programming Using PHP ](#Lecture8)
<br>
[Lecture 9 - Object and Object-Relational Databases ](#Lecture9)
<br>
[Lecture 11 - Disk Storage, Basic File Structures, Hashing and Modern Storage Architectures ](#Lecture11)
<br>
[Lecture 13 - Distributed Databases, NOSQL Systems, Big Data, Data Mining Concepts ](#Lecture13)
<br>

<a name="Lecture6"></a>
## Lecture 6 - SQL Complex Queries, Triggers, Views and Schema Modification

### Types of NULL
- **Unknown Value**
  - A value that exists but not known
- **Unavailable / Withheld Value**
  - A value that exists but is purposely withheld
- **Not Applicable Attribute**
  - Attribute is undefined for the row
- Hard to determine which type of NULL it is
  - So SQL uses **TRUE**, **FALSE**, **UNKNOWN**
- False > Unknown > True
  - eg. If True & Unknown == Unknown
  - eg. If Unknown & False == False
- **Note** In most queries that have a `WHERE` clause, if the tuples (row) are TRUE then only are they returned in the query (Exceptions = Outer Join)**Note**

### Nested Queries
- Use two select queries
  - Inner Query
    - A `SELECT` query that returns a value to compare with the outer query
  - Outer Query
    - A `SELECT` query that has a `WHERE` clause using the value from the Inner Query
- Can check multiple columns

```sql
SELECT * FROM Table WHERE (col1, col2)
IN (SELECT col1, col2)
```

#### ANY & ALL Clause
- Can use `ANY` & `ALL` to compare a single value to a set of values
  - eg. Select an employee who's salary > `ALL` or `ANY` Employees from a given department

#### Aliases
- `SELECT * FROM TableName AS t`
  - Now you can reference TableName columns as `t.col1`
- If columns in the inner query are not aliased, it is assumed it comes from the table specified in the inner query

#### Correlated Nested Query
- A Nested Query is **Correlated** if you are using an attribute(column) from the outer query within the inner query
  - *Note: For Queries that use 'IN' or '=' they can be written without a nested query (SELECT * FROM Table1, Table2), hence they are not correlated*
- Example of Correlated Nested Query

```sql

SELECT * FROM Employee AS E
WHERE Salary > ( SELECT AVG(Salary)
                 FROM Employee WHERE E.Dept = Dept)
```
- Using `E.Dept = Dept` makes it correlated because the avg(Salary) must be calculated for every row in the outer query

#### EXISTS & NOT EXISTS Clause
- Checks if the correlated nested query returns an empty set
  - `WHERE EXISTS` would return False for an empty set and true otherwise
  - `WHERE NOT EXISTS` would return True for an empty set and false otherwise


- eg. Can use exists to check for an employee that is a manager and has dependents

```sql
SELECT Fname, Lname FROM Employee
WHERE EXISTS ( SELECT *
               FROM DEPENDENT
               WHERE Ssn=Essn )
AND

WHERE EXISTS ( SELECT *
               FROM DEPARTMENT
               WHERE Ssn=Mgr_ssn )

```

#### UNIQUE Clause
- Returns True if there are no duplicate rows in the result of a nested query
  - Can be used to check if the result of a nested query is a
    - a.) Set (no duplicates)
    - b.) Multiset (yes duplicates)

#### Explicit Sets
- In the `WHERE` clause you can specify your own custom values to look for
  - eg. `SELECT columnName FROM tableName WHERE columnName IN (1,2,3)`
  - The above example selects columnName if it has a value of 1, 2 or 3

### INNER JOIN

#### JOIN
- `JOIN` (same as `INNER JOIN`) combines tables on a join condition
  - eg.

```sql
SELECT Fname, Lname, Address FROM Employee
JOIN Department ON Dno=Dnumber
WHERE Dname='Research'
```

  - The result from a `JOIN` query will have all the attributes(columns) from the first table and the second table

#### NATURAL JOIN
- Natural Join, joins two tables based on naming of columns
  - You do not need to specify which column because it will automatically do that
  - If none of the column names for the two tables are the same you can use aliasing to rename them


### OUTER JOIN
- Outer Join returns all rows from both tables regardless of a match
  - There are three types of outer joins
  - Left, Right, Full

#### LEFT JOIN
- Left Join, joins two tables and **returns all the rows from the left table and only matched rows from the right table**
  - `LEFT JOIN table2 ON table1.col1 = table2.col2`
  - The 'Left' table would be table1 in the above example (left side of equal sign)

#### RIGHT JOIN
- Right Join, joins two tables and **returns all the rows from the right table and only matched rows from the left table**
  -   - `RIGHT JOIN table2 ON table1.col1 = table2.col2`
    - The 'Right' table would be table2 in the above example (right side of equal sign)

#### FULL JOIN
- Full Join, joins two tables and **returns a row if there is a match in either of the tables**

#### Multi-way Join
```sql

Example:

SELECT * FROM ((PROJECT JOIN DEPARTMENT ON Dnum=Dnumber)
              JOIN EMPLOYEE ON Mgr_ssn=Ssn)
WHERE Plocation='Stafford'

```

### Aggregate Functions
- Aggregate functions take the value of multiple rows and group them together to get a single value
  - eg. AVG, SUM, COUNT, MAX, MIN etc
- Sometimes rows are grouped (GROUP BY) before using aggregate functions
- Aggregate functions operate on a single column and return a single value
  - `SUM`/`AVG` apply only to numerical domains
  - `COUNT`/`MIN`/`MAX` apply to non-numeric domains as well
  - All of these aggregate functions ignore `NULLs`
- `COUNT(*)` which counts the rows in a table includes `NULL` values
  - `COUNT` can be combined with other clauses
  - eg. `COUNT(DISTINCT Salary)` to get the number of distinct salary values from the database
  - Should know to use count when questions asks for *Number of* something

### Grouping

#### GROUP BY Clause
- Groups rows based on a specified attribute(column)
- The attributes that are being used in the `GROUP BY` clause **must** appear in the `SELECT` clause
- `NULLs` will have their own group

#### HAVING Clause
- Similar to the `WHERE` clause but is used for groups and is applied after the `GROUP BY` clause
- eg. `HAVING COUNT(*) > 2`
  - This will select groups that have more than 2 rows
- If you specify a `WHERE` clause and a `HAVING` clause
  - The `WHERE` clause is executed first to individual rows
  - Then the `HAVING` clause is applied to groups


- Example: Count the total number of employees whose salaries exceed $40,000 in each department, but only for departments where more than 5 employees work

```sql
SELECT Dnumber, COUNT(*) FROM EMPLOYEE
WHERE Salary>4000 AND Dno IN
      (SELECT Dno FROM EMPLOYEE
      GROUP BY Dno
      HAVING COUNT(*) > 5)
GROUP BY Dno;

```

#### WITH Clause
- Define a temporary view using the `WITH` clause to be used later in the query


- Example: Count the total number of employees whose salaries exceed $40,000 in each department, but only for departments where more than 5 employees work

```sql

WITH BIGDEPTS(Dno) AS
      ( SELECT Dno FROM EMPLOYEE
        GROUP BY Dno
        HAVING COUNT(*) > 5)

SELECT Dno, COUNT(*) FROM EMPLOYEE
WHERE Salary>40000
AND Dno IN BIGDEPTS
GROUP BY Dno

```

- The `WITH` clause defines a temporary table called BIGDEPTS that has all the departments and Dno's where there are more than 5 employees
- Now all we need is a `WHERE` clause to see if the employee is part of the any of the departments in BIGDEPT and has a salary > 40000

#### CASE
- Used when values vary based on certain conditions
  - A good example is updating the database
  - Update Employee Salary based on certain cases
    - eg. Increase salary based on dept no.

```sql

UPDATE EMPLOYEE
SET Salary =
CASE  WHEN Dno = 5 THEN Salary + 2000
      WHEN Dno = 4 THEN Salary + 1500
      ELSE Salary + 0

```

### Assertions & Triggers
- Assertions
  - Specify additional constraints outside of built-in ones
- Triggers
  - Specify automatic actions the dbms will perform when certain conditions are met or when certain events occur

#### Assertions
- Create a query that selects rows that violate your custom condition
  - eg. A Salary Constraint where employee salaries cannot be higher than the managers in the same department

```sql
CREATE ASSERTION SALARY_CONSTRAINT
CHECK (NOT EXISTS ( SELECT *
                    FROM EMPLOYEE E, EMPLOYEE M, DEPARTMENT D
                    WHERE E.Salary > M.Salary
                    AND E.Dno = D.Dnumber
                    AND D.Mgr_ssn=M.Ssn));
```

#### Triggers
- Has 3 components
  - Event(s)
  - Condition
  - Action
- eg. Same Salary Violation example, but using triggers

```sql
CREATE TRIGGER SALARY_VIOLATION
BEFORE INSERT OR UPDATE OF SALARY, SUPERVISOR_SSN ON EMPLOYEE
FOR EACH ROW
  WHEN (NEW.SALARY > (SELECT SALARY FROM EMPLOYEE
                      WHERE SSN = NEW.SUPERVISOR_SSN))
                      INFORM_SUPERVISOR(NEW.Supervisor_ssn, NEW.Ssn);

```

### Views in SQL
- A 'Virtual' Table that is derived from other tables
  - Basically the result of a query is a view
  - It can be created using the `CREATE VIEW` command and the corresponding query
  - You can then just use `SELECT * FROM ViewName` to return all the results from the view you just created
- Can remove views by using `DROP VIEW  nameOfView`
- DBMS should auto-update views upon new data entry

```sql
CREATE VIEW WORKS_ON1
AS SELECT Fname, Lname, Pname, Hours
FROM EMPLOYEE, PROJECT, WORKS_ON
WHERE Ssn=Essn AND Pno=Pnumber

```

**Note:** View definitions should end with `WITH CHECK OPTION` otherwise the view will not update


#### View Implementation
- 2 Main Approaches
  - Query Modification
    - When Querying a view, modify it to add extra clauses
    - Disadvantageous because it becomes inefficient for complex-query-views
  - View Materialization
    - Create a temp view table when the view is first queried
    - Keep the table assuming you're going to use it again for the following queries
      - Needs to be efficiently updated when the tables in the `FROM` clause change

### Schema Change Statements
- Can be done while database is operational
- Does not require the database schema to be recompiled

#### DROP Command
- Used to drop tables, domains, constraints or other named schema elements
- Drop Behavior Options
  - `CASCADE`
    - Drops tables and any references / dependencies
  - `RESTRICT`
    - Only Drops table if it is not being referenced in any other constraints (foreign key etc..)

#### ALTER Command
- Changing Column Definition
- Add/Drop Constraints
- Add/Drop Column
  - When doing this, specify `RESTRICT` or `CASCADE`

---

<a name="Lecture7"></a>
## Lecture 7 - SQL Programming Techniques

---

<a name="Lecture8"></a>
## Lecture 8 - Web Database Programming Using PHP

---

<a name="Lecture9"></a>
## Lecture 9 - Object and Object-Relational Databases

---

<a name="Lecture11"></a>
## Lecture 11 - Disk Storage, Basic File Structures, Hashing and Modern Storage Architectures

---

<a name="Lecture13"></a>
## Lecture 13 - Distributed Databases, NOSQL Systems, Big Data, Data Mining Concepts

---
