# Database Foundations

### Types of Databases
- Graph database (Neo4j)
- Object database (Realm, Objectivity/DB)
- Document database (CouchDB, MongoDB)
- Relational database

### What is a Relational Database?
A database organizing data into relations (tables of related data).
- Rows in a table are instances of an item / object. A set of rows is referred to as "tuples".
- Columns in a table are attributes of that item / object. A set of columns is referred to as a relation.
- Example: Let's say a restaurant stores information about its customers in a table within a database. Each customer would be an entity, and the attributes collected would be name, phone no., email, etc. Another table stored in the database could be dishes. Each dish would be an entity, and the attributes collected here would differ from the customers: name, price, description, etc.

### Column Data Types
Each column will require a certain type of information about each instance that needs to be defined, such as the following:
- Number
- Text
- Date
- True/false value
- Binary data

All values within a column will contain same format of information, yet the values will differ for each entity.

### Keys and Unique Values
A **key** is a unique value to access one specific row. For example, with the customer table, it's entirely possible to have multiple customers with the same name. Thus, using a key can ensure the right customer is identified.

The most important key in a table is the **primary key**. While it's not necessarily required, it can help grab specific rows with more ease.

Many DBMS tools create a column with a number that's constantly incremented as each entity is added, and this is known as a **synthetic key**, or a **surrogate key**.

In situations where the schema can't be edited, two or more data values will need to act as the unique identifier key, aka the **composite key**.

A **foreign key** is where one table's primary key is referenced in another table. This is crucial when relationships between different tables are formed.
Example:
| OrderID | CustomerID | Order |
| --- | --- | --- |
| 7 | **19** | Classic Burger |
| 16 | 4 | Apple Pie |
| 24 | 19 | Cheesecake |

| CustomerID | First Name | Last Name | Phone No. | Birthday |
| --- | --- | --- | --- | --- |
| **19** | Abby | Smith | (987) 654 - 3210 | 1989-01-30 |
| 4 | Betty | Thomas | (012) 345 - 6789 | 1985-12-14 |
| 29 | Caroline | George | (019) 284 - 3576 | 2000-05-21 |

### Relationships
Building relationships with different tables allows us to utilize data in more sophisticated implementations.

The three types of database relationships include:
- One-to-many
  - The most common relationship where a record from one table is associated with multiple records in another table.
  - For example, if we take a dish from the dishes table and look through our customers table, we can identify which customers found that particular dish to be their favorite. The key from the dishes table would be a primary key, while the key in the customers table would be a foreign key.

- Many-to-many
  - This relationship occurs when multiple records from one table are associated with multiple records in another table. We use a linking table here that has columns with foreign keys from each table.

- One-to-one
  - This relationship occurs when one record from a table is associated with a single record in another table and vice versa.
  - This isn't as commonly used, but it can be useful.
 
### ACID and transactions
Adding or removing records are easy modifications that can be made to a table. Yet, in complex interaction like bank transactions, where multiple operations are done, changes made to data need to be done strictly and accurately.

Current systems can process information quickly, but not instantaneously, thus if an error is present, the whole process can be broken. 

Transactions in databases are used to prevent these types of errors. A **transaction** is a set of operations that require them all to be completed. In the case that an operation isn't completed, the database remains completely unchanged.

ACID is a principle that transactions follow, where A stands for atomic, C stands for consistent, I stands for isolated, and D stands for durable.
- Atomic: parts of the transaction can't be separated
- Consistency: transactions need to leave the database in a consistent condition.
- Isolated: while transaction operations are executing, no other changes can be made to the database
- Durability: altered information is actually stored into the database

DBMS software has the ability to follow the ACID principle and applies it when the user indicates that a transaction is being made.

### Basic SQL
**SQL (Structured Query Language)**, or **Sequel** is the language users use to communicate with databases.

Most **relational database management system tools (RDBMS)** support **ANSI SQL**, a version defined by the American National Standards Institute that has the standard, wide set of SQL commands. Many tools have their own version to incorporate features that are specific to the DBMS software they use (e.g. T-SQL / Transact-SQL, MySQL).

### What is the purpose of SQL?
SQL lets you write statements for the DBMS to understand how to interact with data given. SQL, in this case, is a **data manipulation language (DML)**. SQL additionally has features for managing databases, like adding or editing tables and controlling access to tables. Here, SQL acts as a **data definition language (DDL)** and a **data control language**.

### Foundational SQL Statements
A **SQL statement** is made up of clauses with expressions and predicates. Clauses are keywords specifying action, while expressions and predicates set parameters to operate on. To ensure readability, keywords are often in uppercase.

Example:
SELECT FirstName, LastName FROM Customers
WHERE LastName = 'Jenkins';

In this example, **SELECT**, **FROM**, and **WHERE** would be the clauses. The expression would be **LastName = 'Jenkins'**, while the predicate is **'Jenkins'**.

These statements can either be written in database software (e.g. SQL Server Management Studio) or added in program code so that an app can access data. 

For example, this statement ('SELECT FirstName, LastName FROM Customers WHERE Birthday = '1991-02-09';) would show the user the first name and last name for every record within the customers table with that specific birthday. 
- Three clauses are used here: the first asks for FirstName, LastName, and Birthday fields; the second specifies using records from the customer table; the third specifies how to sort the returned records.

A **query** asks the database for information or to do something. 

### What are CRUD operations?
CRUD (Create, Read, Update, Delete) operations are basic operations that interact with data. 

### Summary
- A unique value occurs only once in a given column.
- A relationship connects two pieces of data in different tables within the same database.
- A good example of a candidate key would be an employee ID number as it would be a unique value.
- SELECT Width,Height FROM Shapes; contains 2 SQL clauses, SELECT and FROM.
- In a database, a relation is a set of attributes (columns) describing information about specific instances (rows) of an entity.
- A composite key is a key that consists of different fields taken together to act as a unique identifier.
- Durability is the ACID step that requires the database to be updated when the transaction completes successfully.
- An associate table is useful when records need to be related in a many-to-many relationship.
- Atomic is the ACID step stating that a transaction can't be divided into smaller parts.
- SQL is the language used to communicate with a database.
- A transaction is all of the steps for an action that must be completed.
