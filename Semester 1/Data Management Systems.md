# Data Management Systems


## Lecture 1

### Database
- Collection of related data

#### Implicit Properties
  - Miniworld or universe of discourse
    - Represents some aspect of the real world
  - Logically coherent collection of data
    - Random assortment of data != database
  - Built for a specific purpose
    - Must have intended users

#### Types of Databases
- Traditional
  - Store Text / Numbers


- Multimedia
  - Store Image, Audio, Video


- Geographic Information Systems (GIS)
  - Maps, Weather, Satellite Images


- OLAP Systems
  - Extract and analyze useful business info from large databases


- Real Time and Active Database
  - Control industrial and manufacturing processes

### DBMS (Database Management System)
- Collection of programs that allow creation and maintaining of a database

#### DBMS Functions
- Define
  - Specify Data types, structure and constraints (meta-data)
- Construct
  - Storing data on some storage controlled by DBMS
- Manipulate
  - Retrieve (ex. `SELECT` Queries)
  - Modify (ex. `INSERT` `DELETE` `UPDATE` Queries)
  - Access through web apps
- Sharing
  - Multiple users to use simultaneously
- System Protection
  - against hardware or software malfunction
- Security Protection
  - against unauthorized access
- Maintain DBS
  - Allow system to evolve as requirements change

#### Queries
- Retrieve data from the database

#### Transactions
- Read or Write Data into the database

#### Sample SQL Code

Creating a Table

```
CREATE TABLE Example
(
  ID int PRIMARY KEY NOT NULL,
  integer int,
  floating_point float,
  string varchar(255),
  FOREIGN KEY(someColumn) REFERENCES
  differentTable(anotherColumn)
);
```
- Should Define a Primary Key
- Integers = int
- Floating Points = float
- Strings = varchar(size)
- If a key in the table being created needs to reference another table's column it is a foreign key

SELECT Queries

```

```
#### Phases for Designing a Database
- Requirements Specification and Analysis
  - Documented
- Conceptual Design
  - Represented and manipulated using computerized tools
- Logical Design
  - Expressed in a DBMS
- Physical Design
  - Specifications are provided for storing and accessing database

### Database Approach Characteristics

#### Self-describing
  - Database System has defined structure and constraints
  - ^ called meta-data is stored in the DBMS catalog
  - meta-data describes file structure/type/storage
  - meta-data can be accessed by the DBMS software and users

#### Insulation between Programs and Data
- Program-Data-Independence: Structure is stored seperately from access programs
<br><br>
- Types of Operations:
  1. Interface includes operation name and data types
  2. Implementation can be be changed without affecting Interface
  <br><br>
- Program-Operation-Independence: Some DBS have operation definition as part of DB definition and that is also independent
<br><br>
- Program-Data-Independence = Data Abstraction
  - DBMS provides conceptual rep. of data, doesnt actually show how data is stored or storage details. Just uses concepts like objects to present to the user.

#### Multiple Data Views
- A view is a subset of the DB, contains virtual data; not explicitly stored

#### Sharing of Data and Multiuse Transaction Processing
- Multiple users at the same time
  - Must have concurrency control software so when several users try to update same data, it updates correctly.
  - ^^ Online Transaction Processing Application (OLTP)
  - Allows hundreds of concurrent transactions to execute per second
-


## Lecture 5
- Formatting Numbers in SQL
  - Decimal(i,j)
  - i = total number of decimal digits
  - j = number of digits of decimal point
- Formatting Strings in SQL
  - varchar defines a max
  - char defines a fixed length (less will be padded right with blank characters)
  - CLOB is for large text values (10mb)
- Formatting Bits in SQL


Having is executed after the group
where is executed before

same shit tho just need having if u doing group ya know
w.e is in group must be in select if either way is diff then wrong
