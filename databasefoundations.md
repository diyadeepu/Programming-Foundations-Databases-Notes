# Database Foundations

### Types of Databases
- Graph database (Neo4j)
- Object database (Realm, Objectivity/DB)
- Document database (CouchDB, MongoDB)
- Relational database

### What is a Relational Database?
A database organizing data into relations (tables of related data).
- Rows in a table are instances of an item / object.
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
