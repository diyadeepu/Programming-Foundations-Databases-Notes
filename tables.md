# Tables

### Modeling and planning a database
**Entity Relationship Diagram (ER Diagram)** is a diagram utilizing tables, fields, and relationships to plan a database.

To build the diagram, a **basic needs analysis** will be completed, where the basic  requirements are gathered.
- What does our database need to store?
- What information will be there?

With the restaurant example, our database needs might be customers, dishes, events, orders, reservations, birthdays, and favorite dishes.

### Naming Tables
Tables are often named with the plural version of their record type. With the customer table, that might be named **Customers**.

It's best practice to name tables starting with a capital letter. (e.g. Customers, Events, Dishes, etc.)

Fields, on the other hand, should be named with their singular version as there's only a single piece of data in that field. (e.g. FirstName, LastName, Birthday, etc.)

Additionally, avoid special characters and spaces for both table and field names, and utilize CamelCase.

### Columns and data types
**Null** is a value representing the absence of the value in a database. It's not a data type, but rather a condition. If a cell has a value, it is _NOT NULL_. 

##### Data Types for Dates
A **data type** is the type of information stored in each column.
- Date: used to store dates
  - e.g. Birthday (2019-03-09)
  - DATETIME: stores both date and time (2019-03-09 16:51:00)
  - TIMESTAMP: automatically captures the date and time when a row is updated or added
    - Great for recording when an order was placed

##### Data Types for Strings
- Strings: a collection of characters and text
  - CHAR: a fixed number of characters
    - Often reserved for fields where we know the exact number of characters within the field in each row
  - VARCHAR: a variable number of characters up to a max length
    - e.g. FirstName, LastName, Address
    - Phone no. can also be stored here as they have special characters or unique formatting.
  - Other types for longer texts, like a description
_A database needs to know the length of the string to efficiently store information._

Different databases might have more specialized types. MySQL, for example, has a text type for longer text.

##### Data Types for Numbers
- Integers
- Double precision
- Floating point
- Decimals (of varying length)
  - DECIMAL(3,2) can be used, for example, with prices for dishes.
_A database needs to know the precise data type for numbers to avoid encountering issues with rounding._

### Primary and foreign keys
A table, like the Customers table, might have information that isn't reliably unique. Therefore, a unique information identifier needs to be added, such as a surrogate or a synthetic key that's different for each entity.

In the Customers table, we can create the CustomerID to be the primary key, storing numeric values that will auto-increment. This guarantees a unique value for every customer.

For security reasons, people choose a UUID (universally-unique identifier) over an integer key. A **UUID** is a 128-bit number, making it more difficult for an attacker to guess.

Ensure to keep the name of these keys consistent and descriptive. A good way to name the key is to use the singular table name, followed by "ID" for identifier or "PK" for primary key (TablenameID).

A **composite key** is a combination of fields helping to uniquely identify a record. It could be a combo of first name, last name, and phone no., provided that this combination is unique for every single row.

### Summary
- If you reference a key from Table A in Table B, that value in Table B is a foreign key.
- An example of a good primary key would be an employee's id as each employee gets a unique ID number.
- A good name for a table containing customer details and contact information would be Customers.
- In a database keeping track of records for a school, Students, Grades, and Classes are tables that you can expect to find.
  - As tables store multiple records, their names are pluralized.
- When storing the text **Mozambique** in a column with a data type of VARCHAR(8), Mozambiq would be saved in the database and the last two characters wouldn't be stored.
- String types are a data type representing texts of different lengths.
- To store the value 4:32PM, December 27, 2019, use the DATETIME data type.
- A cell, regardless of its data type, is Null when it has no value.
- If you don't use a number type to store numeric data, you need to take additional steps to process the data as a number whenever you use it.
- Before you create a database, you need to know the names and data types of fields you'll use, how entries in different tables will be used together, and what tables you'll need for your data.
- A composite key is useful when there's no primary key to uniquely identify and relate a record to other data.
- When planning a database, you start with an Entity Relationship (ER) diagram to plan out what fields appear on which tables and how they're related.
