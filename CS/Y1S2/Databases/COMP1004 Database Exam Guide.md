# COMP1004 Database Exam Guide

Sources:
- `Lecture Slides/01 - Introduction to Databases.pdf`
- `Lecture Slides/02 - ERD Mapping and Normalisation.pdf`
- `Lecture Slides/03 - SQL DDL.pdf`
- `Lecture Slides/04 - SQL DML.pdf`

Coverage note:
- These notes are limited to the material covered by the four database lecture slide files in this folder.
- Extra general database material has been removed unless it is part of those slide-backed topics.

## Core Exam Topics From The Slides

The slide-backed database topics are:
- database foundations;
- relational database vocabulary;
- entity relationship modelling;
- ERD to relational mapping;
- functional dependencies;
- normalisation;
- SQL DDL;
- SQL DML.

The main practical skill is moving between:
- a scenario;
- an ER model;
- relational tables;
- normal forms;
- SQL code.

## Database Foundations

### Database

A database is an organised collection of data.

### DBMS

A database management system, or DBMS, is software used to store, manage, query, and protect data.

### Relational Database

In a relational database, data is stored in relations.

A relation is usually represented as a table.

Example relation:

| StudentID | Name | Course |
| --- | --- | --- |
| 1001 | Asha | Computer Science |
| 1002 | Ben | Mathematics |

## Relational Vocabulary

Relation:
- a table.

Tuple:
- a row or record in a relation.

Attribute:
- a column or field in a relation.

Degree:
- the number of attributes in a relation.

Cardinality:
- the number of tuples in a relation.

Relational database schema:
- a collection of normalised relations with distinct relation names.

Primary key:
- an attribute or set of attributes that uniquely identifies a tuple.

Foreign key:
- an attribute that refers to a primary key in another relation.

Schema:
- the structure of the database, including tables, columns, keys, and constraints.

## Keys

### Primary Key

A primary key uniquely identifies each tuple in a relation.

Example:

```text
Student(StudentID, Name, Course)
```

`StudentID` is a good primary key if each student has a unique ID.

### Composite Primary Key

A primary key can be made from more than one attribute.

Example:

```text
Enrolment(StudentID, ModuleCode)
```

The combination of `StudentID` and `ModuleCode` identifies a particular enrolment.

### Foreign Key

A foreign key links one relation to another.

Example:

```text
Student(StudentID, Name)
Enrolment(StudentID, ModuleCode)
```

`Enrolment.StudentID` refers to `Student.StudentID`.

Foreign keys are how relationships are represented in relational tables.

## Entity Relationship Modelling

An entity relationship diagram, or ERD, models the important things in a system and how they relate to each other.

### Entity

An entity is a thing the database needs to store data about.

Examples:
- `Student`;
- `Module`;
- `Customer`;
- `Order`;
- `Product`.

Entities usually become relations.

### Attribute

An attribute is a piece of information stored about an entity.

Example:

```text
Student(StudentID, StudentName, Email)
```

`StudentID`, `StudentName`, and `Email` are attributes.

Attributes usually become columns.

### Relationship

A relationship is an association between entities.

Examples:
- a student enrols on a module;
- a customer places an order;
- an order contains products.

Relationships are represented using foreign keys or separate relationship relations.

## ERD Cardinality

Cardinality describes how many instances of one entity can be related to instances of another.

The main relationship types are:
- one-to-one;
- one-to-many;
- many-to-many.

## Mapping ERDs To Relations

Use this method:

1. Each regular entity becomes a relation.
2. Each simple attribute becomes a column.
3. The entity identifier becomes the primary key.
4. Relationships are represented using foreign keys.
5. Many-to-many relationships normally become a separate relation.

## One-To-Many Mapping

Example:

```text
Customer -- places -- Order
```

Relational mapping:

```text
Customer(CustomerID, CustomerName)
Order(OrderID, OrderDate, CustomerID)
```

The foreign key goes on the many side.

Here, `CustomerID` in `Order` refers to `Customer.CustomerID`.

## Many-To-Many Mapping

Example:

```text
Student -- enrols in -- Module
```

Relational mapping:

```text
Student(StudentID, Name)
Module(ModuleCode, Title)
Enrolment(StudentID, ModuleCode)
```

`Enrolment` is needed because many students can take many modules, and many modules can have many students.

In `Enrolment`:
- `StudentID` is a foreign key to `Student`;
- `ModuleCode` is a foreign key to `Module`;
- `(StudentID, ModuleCode)` can be used as a composite primary key.

## Functional Dependencies

A functional dependency means that one attribute determines another.

Notation:

```text
A -> B
```

This means that if you know `A`, you can determine `B`.

Example:

```text
StudentID -> StudentName
```

If you know the `StudentID`, you can determine the `StudentName`.

Functional dependencies are used to:
- identify keys;
- find redundancy;
- decide how to normalise a table.

## Normalisation

Normalisation is the process of improving table design to reduce duplicated data and avoid update problems.

The slide-backed normal forms are:
- first normal form;
- second normal form;
- third normal form.

## Anomalies

Poor table design can cause anomalies.

Insertion anomaly:
- you cannot add one fact without another unrelated fact.

Update anomaly:
- the same fact appears in many places and must be updated repeatedly.

Deletion anomaly:
- deleting one row accidentally removes a useful fact.

## First Normal Form

First normal form, or 1NF, means:
- values are atomic;
- there are no repeating groups;
- each field contains a single value.

Bad:

| StudentID | Modules |
| --- | --- |
| 1001 | COMP1001, COMP1004 |

Problem:
- `Modules` contains more than one value.

Better:

| StudentID | ModuleCode |
| --- | --- |
| 1001 | COMP1001 |
| 1001 | COMP1004 |

Exam phrase:
- 1NF removes repeating groups and makes values atomic.

## Second Normal Form

Second normal form, or 2NF, means:
- the relation is in 1NF;
- every non-key attribute depends on the whole primary key.

This mainly matters when the primary key is composite.

Bad:

```text
Enrolment(StudentID, ModuleCode, StudentName, ModuleTitle)
```

Assume the primary key is:

```text
(StudentID, ModuleCode)
```

Problems:
- `StudentName` depends only on `StudentID`;
- `ModuleTitle` depends only on `ModuleCode`;
- neither depends on the whole composite key.

Better:

```text
Student(StudentID, StudentName)
Module(ModuleCode, ModuleTitle)
Enrolment(StudentID, ModuleCode)
```

Exam phrase:
- 2NF removes partial dependencies on part of a composite key.

## Third Normal Form

Third normal form, or 3NF, means:
- the relation is in 2NF;
- non-key attributes do not depend on other non-key attributes.

Bad:

```text
Student(StudentID, StudentName, TutorID, TutorName)
```

If:

```text
TutorID -> TutorName
```

then `TutorName` depends on `TutorID`, not directly on `StudentID`.

Better:

```text
Student(StudentID, StudentName, TutorID)
Tutor(TutorID, TutorName)
```

Exam phrase:
- 3NF removes transitive dependencies.

## Normalisation Method

Use this method:

1. Check for repeating groups or non-atomic values.
2. Identify keys and functional dependencies.
3. Remove repeating groups for 1NF.
4. Remove partial dependencies for 2NF.
5. Remove transitive dependencies for 3NF.
6. Show the final relations with primary keys and foreign keys.

## SQL Overview

SQL is used to define and manipulate relational databases.

The slide-backed SQL categories are:
- DDL;
- DML.

## SQL DDL

DDL means data definition language.

DDL is used to define database structures.

Common DDL commands:
- `CREATE TABLE`;
- `ALTER TABLE`;
- `DROP TABLE`.

## CREATE TABLE

Example:

```sql
CREATE TABLE Student (
    StudentID INT PRIMARY KEY,
    StudentName VARCHAR(100) NOT NULL,
    Email VARCHAR(255) UNIQUE
);
```

## SQL Constraints

Constraints restrict what data is allowed.

Common constraints:
- `PRIMARY KEY`;
- `FOREIGN KEY`;
- `NOT NULL`;
- `UNIQUE`;
- `CHECK`;
- `DEFAULT`.

### PRIMARY KEY

`PRIMARY KEY` uniquely identifies rows.

Example:

```sql
StudentID INT PRIMARY KEY
```

Composite primary key example:

```sql
PRIMARY KEY (StudentID, ModuleCode)
```

### FOREIGN KEY

`FOREIGN KEY` links to another table.

Example:

```sql
CREATE TABLE Enrolment (
    StudentID INT,
    ModuleCode VARCHAR(20),
    PRIMARY KEY (StudentID, ModuleCode),
    FOREIGN KEY (StudentID) REFERENCES Student(StudentID),
    FOREIGN KEY (ModuleCode) REFERENCES Module(ModuleCode)
);
```

### NOT NULL

`NOT NULL` means a value must be provided.

Example:

```sql
StudentName VARCHAR(100) NOT NULL
```

### UNIQUE

`UNIQUE` prevents duplicate values in a column.

Example:

```sql
Email VARCHAR(255) UNIQUE
```

### CHECK

`CHECK` means a value must satisfy a condition.

Example:

```sql
Mark INT CHECK (Mark >= 0 AND Mark <= 100)
```

### DEFAULT

`DEFAULT` supplies a value if one is not provided.

Example:

```sql
Status VARCHAR(20) DEFAULT 'Pending'
```

## SQL DML

DML means data manipulation language.

DML is used to work with the data inside tables.

Common DML commands:
- `INSERT`;
- `UPDATE`;
- `DELETE`;
- `SELECT`.

## INSERT

`INSERT` adds data to a table.

```sql
INSERT INTO Student (StudentID, StudentName, Email)
VALUES (1001, 'Asha Khan', 'asha@example.com');
```

## UPDATE

`UPDATE` changes existing data.

```sql
UPDATE Student
SET Email = 'asha.khan@example.com'
WHERE StudentID = 1001;
```

Use a careful `WHERE` clause, otherwise every row may be updated.

## DELETE

`DELETE` removes data.

```sql
DELETE FROM Student
WHERE StudentID = 1001;
```

Use a careful `WHERE` clause, otherwise every row may be deleted.

## SELECT

`SELECT` retrieves data.

General shape:

```sql
SELECT column1, column2
FROM TableName
WHERE condition
ORDER BY column1;
```

Example:

```sql
SELECT StudentName, Email
FROM Student
WHERE Course = 'Computer Science'
ORDER BY StudentName;
```

## WHERE

`WHERE` filters rows.

Common operators:
- `=`;
- `<>`;
- `<`;
- `>`;
- `<=`;
- `>=`;
- `AND`;
- `OR`;
- `NOT`;
- `LIKE`;
- `IN`;
- `BETWEEN`;
- `IS NULL`.

Example:

```sql
SELECT StudentName
FROM Student
WHERE Course = 'Computer Science';
```

## ORDER BY

`ORDER BY` sorts results.

```sql
SELECT StudentName
FROM Student
ORDER BY StudentName;
```

## Aggregate Functions

Aggregate functions calculate values across rows.

Common aggregate functions:
- `COUNT`;
- `SUM`;
- `AVG`;
- `MIN`;
- `MAX`.

Example:

```sql
SELECT ModuleCode, COUNT(*) AS NumberOfStudents
FROM Enrolment
GROUP BY ModuleCode;
```

## GROUP BY

`GROUP BY` groups rows so aggregate functions can be applied to each group.

Example:

```sql
SELECT ModuleCode, COUNT(*) AS NumberOfStudents
FROM Enrolment
GROUP BY ModuleCode;
```

## HAVING

`HAVING` filters grouped results.

```sql
SELECT ModuleCode, COUNT(*) AS NumberOfStudents
FROM Enrolment
GROUP BY ModuleCode
HAVING COUNT(*) > 20;
```

Key difference:
- `WHERE` filters rows before grouping;
- `HAVING` filters groups after grouping.

## Joins

Joins combine rows from multiple tables using related columns.

Example:

```sql
SELECT Student.StudentName, Module.ModuleTitle
FROM Student
JOIN Enrolment ON Student.StudentID = Enrolment.StudentID
JOIN Module ON Enrolment.ModuleCode = Module.ModuleCode;
```

This works because:
- `Student` links to `Enrolment` using `StudentID`;
- `Module` links to `Enrolment` using `ModuleCode`;
- `Enrolment` represents the student-module relationship.

## Subqueries

A subquery is a query inside another query.

Example:

```sql
SELECT StudentName
FROM Student
WHERE StudentID IN (
    SELECT StudentID
    FROM Enrolment
    WHERE ModuleCode = 'COMP1004'
);
```

This returns students enrolled on `COMP1004`.

## Quick Exam Patterns

For ERD mapping:

1. Identify entities.
2. Turn entities into relations.
3. Choose primary keys.
4. Represent one-to-many relationships with foreign keys.
5. Represent many-to-many relationships with a separate relation.

For normalisation:

1. Check for repeating groups or non-atomic values.
2. Identify keys and functional dependencies.
3. Remove partial dependencies for 2NF.
4. Remove transitive dependencies for 3NF.

For SQL:

1. Decide which table or tables are needed.
2. Write the `FROM` and joins.
3. Add the `WHERE` condition.
4. Add grouping if the question asks for totals, counts, averages, or per-category results.
5. Use `HAVING` only when filtering groups.

## Quick Definitions

- Database: organised collection of data.
- DBMS: software used to store, manage, query, and protect data.
- Relation: table.
- Tuple: row or record.
- Attribute: column or field.
- Degree: number of attributes in a relation.
- Cardinality: number of tuples in a relation.
- Relational database schema: collection of normalised relations with distinct relation names.
- Primary key: attribute or set of attributes that uniquely identifies a tuple.
- Foreign key: attribute that refers to a primary key in another relation.
- ERD: diagram that models entities and relationships.
- Functional dependency: one attribute determines another.
- Normalisation: process of improving table design to reduce duplication and update problems.
- 1NF: atomic values and no repeating groups.
- 2NF: 1NF and every non-key attribute depends on the whole primary key.
- 3NF: 2NF and no non-key attribute depends on another non-key attribute.
- DDL: SQL used to define database structures.
- DML: SQL used to manipulate data.
