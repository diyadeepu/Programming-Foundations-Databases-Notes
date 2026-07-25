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
A **data type** is the type of information stored in each column.
- Date: used to store dates
  - e.g. Birthday (2019-03-09)
  - DATETIME: stores both date and time (2019-03-09 16:51:00)
  - TIMESTAMP: automatically captures the date and time when a row is updated or added
    - Great for recording when an order was placed
      
- Strings: a collection of characters and text
  - CHAR: a fixed number of characters
    - Often reserved for fields where we know the exact number of characters within the field in each row
  - VARCHAR: a variable number of characters up to a max length
    - e.g. FirstName, LastName, Address
  - Other types for longer texts, like a description

_A database needs to know the length of the string to efficient store information._
