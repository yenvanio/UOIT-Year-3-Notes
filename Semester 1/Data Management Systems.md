# Data Management Systems

### Final Project

- Web Application
- Pull from Database Sources
- Make/Use? REST API

### Lecture 1

##### Database
- Collection of related data

###### Implicit Properties
  - Miniworld or universe of discourse
    - Represents some aspect of the real world
  - Logically coherent collection of data
    - Random assortment of data != database
  - Built for a specific purpose
    - Must have intended users

##### Types of Databases
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

##### DBMS (Database Management System)
- Collection of programs that allow creation and maintaining of a database

##### DBMS Functions
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

##### Queries
- Retrieve data from the database

##### Transactions
- Read or Write Data into the database

##### Sample SQL Code

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
##### Phases for Designing a Database
- Requirements Specification and Analysis
  - Documented
- Conceptual Design
  - Represented and manipulated using computerized tools
- Logical Design
  - Expressed in a DBMS
- Physical Design
  - Specifications are provided for storing and accessing database

##### Database Approach Characteristics
- Self-describing
  - Database System has defined structure and constraints
  - ^ called meta-data is stored in the DBMS catalog
  - meta-data describes file structure/type/storage
  - meta-data can be accessed by the DBMS software and users
- Insulation b/w Programs and Data
  -
