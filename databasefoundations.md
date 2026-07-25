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
