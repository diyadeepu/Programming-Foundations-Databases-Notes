# Tables

### Modeling and planning a database
**Entity Relationship Diagram (ER Diagram)** is a diagram utilizing tables, fields, and relationships to plan a database.

To build the diagram, a **basic needs analysis** will be completed, where the basic  requirements are gathered.
- What does our database need to store?
- What information will be there?

With the restaurant example, our database needs might be customers, dishes, events, orders, reservations, birthdays, and favorite dishes.

### Naming Tables
Tables are often named with the plural version of its record type. With the customer table, that might be named **Customers**.

It's best practice to name tables starting with a capital letter. (e.g. Customers, Events, Dishes, etc.)

Fields, on the other hand, should named with its singular verison as there's only a single piece of data in that field. (e.g. FirstName, LastName, Birthday, etc.)

Additionally, avoid special characters and spaces for both table and fields names, and utilize CamelCase.

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
_A database needs to know the length of the string to efficient store information._

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

In the Customers table, we can create the CustomerID to be the primary key, storing numeric values that will auto increment. This guarantees a unqiue value for every customer.

For security reasons, people choose a UUID (universally-unique identifier) over an integer key. A **UUID** is a 128-bit number, making it more difficult for an attacker to guess.

Ensure to keep the name of these keys consistent and descriptive. A good way to name the key is to use the singular table name, followed by "ID" (TablenameID).
