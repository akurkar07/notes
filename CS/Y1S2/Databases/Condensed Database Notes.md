# Condensed Database Notes

Sources: [Lecture Slides](<Lecture Slides>)

These notes cover the first four COMP1004 database lectures. The main exam skill is being able to move between concepts, diagrams, relational schemas, and SQL code.

## 1. Database Basics

A database is an organised collection of data. A database management system, or DBMS, is the software used to store, manage, query, and protect that data.

In a relational database, data is stored in tables.

Core vocabulary:

- relation: a table;
- tuple: a row or record;
- attribute: a column or field;
- primary key: attribute or set of attributes that uniquely identifies a row;
- foreign key: attribute that refers to a primary key in another table;
- schema: the structure of the database, including tables, columns, keys, and constraints.

Example relation:

| StudentID | Name | Course |
| --- | --- | --- |
| 1001 | Asha | Computer Science |
| 1002 | Ben | Mathematics |

Here, `StudentID` is a good primary key because it uniquely identifies each student.

## 2. ERD to Relational Mapping

An entity relationship diagram models the important things in a system and how they relate to each other.

Common mapping rules:

- each regular entity becomes a relation;
- each simple attribute becomes a column;
- the entity identifier becomes the primary key;
- relationships are usually represented using foreign keys;
- many-to-many relationships normally become a separate relation.

Example ERD idea:

```text
Student --enrols in-- Module
```

Relational version:

```sql
Student(StudentID, Name)
Module(ModuleCode, Title)
Enrolment(StudentID, ModuleCode)
```

`Enrolment` is needed because many students can take many modules.

## 3. Functional Dependencies

A functional dependency means that one attribute determines another.

```text
StudentID -> StudentName
```

This means that if you know the `StudentID`, you can determine the `StudentName`.

Functional dependencies matter because they help you spot redundancy and decide how to normalise a table.

## 4. Normalisation

Normalisation is the process of improving table design to reduce duplicated data and avoid update problems.

Problems caused by poor design:

- insertion anomaly: cannot add one fact without another unrelated fact;
- update anomaly: the same fact appears in many places and must be updated repeatedly;
- deletion anomaly: deleting one row accidentally removes a useful fact.

### 1NF

First normal form means each field contains atomic values. Do not store repeating groups or lists inside one cell.

Bad:

| StudentID | Modules |
| --- | --- |
| 1001 | COMP1001, COMP1004 |

Better:

| StudentID | ModuleCode |
| --- | --- |
| 1001 | COMP1001 |
| 1001 | COMP1004 |

### 2NF

Second normal form means the table is in 1NF and every non-key attribute depends on the whole primary key, not just part of it.

This mainly matters when the primary key is composite.

Bad:

```text
Enrolment(StudentID, ModuleCode, StudentName, ModuleTitle)
```

If the key is `(StudentID, ModuleCode)`, then `StudentName` depends only on `StudentID`, and `ModuleTitle` depends only on `ModuleCode`.

Better:

```text
Student(StudentID, StudentName)
Module(ModuleCode, ModuleTitle)
Enrolment(StudentID, ModuleCode)
```

### 3NF

Third normal form means the table is in 2NF and non-key attributes do not depend on other non-key attributes.

Bad:

```text
Student(StudentID, StudentName, TutorID, TutorName)
```

If `TutorID -> TutorName`, then `TutorName` depends on `TutorID`, not directly on `StudentID`.

Better:

```text
Student(StudentID, StudentName, TutorID)
Tutor(TutorID, TutorName)
```

## 5. SQL DDL

DDL means data definition language. It defines or changes database structures.

Common DDL commands:

- `CREATE TABLE`
- `ALTER TABLE`
- `DROP TABLE`

Example:

```sql
CREATE TABLE Student (
    StudentID INT PRIMARY KEY,
    StudentName VARCHAR(100) NOT NULL,
    Email VARCHAR(255) UNIQUE
);
```

Constraints restrict what data is allowed.

Useful constraints:

- `PRIMARY KEY`: uniquely identifies rows;
- `FOREIGN KEY`: links to another table;
- `NOT NULL`: value must be provided;
- `UNIQUE`: no duplicate values in that column;
- `CHECK`: value must satisfy a condition;
- `DEFAULT`: supplies a value if one is not provided.

Foreign key example:

```sql
CREATE TABLE Enrolment (
    StudentID INT,
    ModuleCode VARCHAR(20),
    PRIMARY KEY (StudentID, ModuleCode),
    FOREIGN KEY (StudentID) REFERENCES Student(StudentID),
    FOREIGN KEY (ModuleCode) REFERENCES Module(ModuleCode)
);
```

## 6. SQL DML

DML means data manipulation language. It is used to insert, update, delete, and retrieve data.

Common DML commands:

- `INSERT`
- `UPDATE`
- `DELETE`
- `SELECT`

Insert:

```sql
INSERT INTO Student (StudentID, StudentName, Email)
VALUES (1001, 'Asha Khan', 'asha@example.com');
```

Update:

```sql
UPDATE Student
SET Email = 'asha.khan@example.com'
WHERE StudentID = 1001;
```

Delete:

```sql
DELETE FROM Student
WHERE StudentID = 1001;
```

Always use a careful `WHERE` clause with `UPDATE` and `DELETE`, otherwise you may affect every row.

## 7. SELECT Queries

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

`WHERE` filters rows before results are returned.

Common operators:

- `=`, `<>`, `<`, `>`, `<=`, `>=`
- `AND`, `OR`, `NOT`
- `LIKE`
- `IN`
- `BETWEEN`
- `IS NULL`

## 8. Aggregates, GROUP BY, and HAVING

Aggregate functions calculate values across rows.

Common aggregate functions:

- `COUNT`
- `SUM`
- `AVG`
- `MIN`
- `MAX`

Example:

```sql
SELECT ModuleCode, COUNT(*) AS NumberOfStudents
FROM Enrolment
GROUP BY ModuleCode;
```

`WHERE` filters rows before grouping. `HAVING` filters groups after grouping.

```sql
SELECT ModuleCode, COUNT(*) AS NumberOfStudents
FROM Enrolment
GROUP BY ModuleCode
HAVING COUNT(*) > 20;
```

## 9. Joins

Joins combine rows from multiple tables using related columns.

```sql
SELECT Student.StudentName, Module.ModuleTitle
FROM Student
JOIN Enrolment ON Student.StudentID = Enrolment.StudentID
JOIN Module ON Enrolment.ModuleCode = Module.ModuleCode;
```

In an exam answer, explain the relationship as well as writing the query: `Student` links to `Module` through the junction table `Enrolment`.

## 10. Subqueries

A subquery is a query inside another query.

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
2. Turn entities into tables.
3. Choose primary keys.
4. Represent one-to-many relationships with foreign keys.
5. Represent many-to-many relationships with a junction table.

For normalisation:

1. Check for repeating groups or non-atomic values.
2. Identify candidate keys and functional dependencies.
3. Remove partial dependencies for 2NF.
4. Remove transitive dependencies for 3NF.

For SQL:

1. Decide which table or tables are needed.
2. Write the `FROM` and joins.
3. Add the `WHERE` condition.
4. Add grouping only if the question asks for totals, counts, averages, or per-category results.
5. Use `HAVING` only when filtering groups.

