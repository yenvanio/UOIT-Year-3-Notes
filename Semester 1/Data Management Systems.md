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

### Joins

#### JOIN or INNER JOIN
- `JOIN` (same as `INNER JOIN`) combines tables on a join condition
  - eg.

```sql
SELECT Fname, Lname, Address FROM Employee
JOIN Department ON Dno=Dnumber
WHERE Dname='Research'
```

  - The result from a `JOIN` query will have all the attributes(columns) from the first table and the second table

#### NATURAL JOIN


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
