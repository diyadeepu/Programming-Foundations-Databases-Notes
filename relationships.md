# Relationships

### One-to-Many Relationships
One-to-Many relationships connect a piece of data, or a row in a table, to one or more other pieces of data.

Say in the Customers table, you're tracking the name of each customer's favorite dish. This might not be the most efficient method if the name of the dish changes as you would need to go back and update the name for each customer that chose the particular dish.

Instead, the primary key can be used here. It's guaranteed to be unique and the key never changes. It additionally takes up less space compared to a name in text, keeping the database smaller. 

Here, one dish might be the favorite dish for multiple customers, hence the one-to-many relationship.

### Many-to-Many Relationships
Many-to-Many relationships connect multiple pieces of data, or rows in a table, to multiple other pieces of data.

Many orders that customers make can have many dishes. Most DBMS tools don't easily allow you to model a many-to-many relationship, thus a linking table is used. The linking table has a one-to-many relationship with both tables that are being used.

Linking tables are usually named by joining the name of both tables (the table on the left and the table on the right).

Example:

######Orders
| OrderID | CustomerID | OrderDate |
| --- | --- | --- |
| 17 | 1 | 2019-02-08 13:45:21 |
| 11 | 38 | 2019-01-25 16:31:12 |
| 8 | 17 | 2019-01-04 17:55:43 |
| 6 | 1 | 2018-12-14 12:45:16 |
| 3 | 16 | 2018-12-04 18:12:34 |

######Dishes
| DishID | Name | Description |
| --- | --- | --- |
| 8 | Chef's Salad | The Chef's Salad has ... |
| 10 | Classic Burger | Our Classic Burger ... |
| 14 | Family Fiesta Platter | This platter is ... |
| 15 | Créme Brûlée | Elegantly crafted ... |
| 16 | Cheesecake | Our New York style |

######OrdersDishes
| OrderID | DishID |
| --- | --- |
| 17 | 8 |
| 11 | 10 |
| 8 | 14 |
| 6 | 15 |
| 3 | 16 |

Many-to-many relationships are essentially one-to-many relationships with the addition of a linking table.

### One-to-One Relationships
This relationship isn't as frequently used, but can be used for security purposes. For example, the customers table can be split into 2 different tables: one with their names and id, and the other with the id and personal information.

### Relationship rules and referential integrity
**Referential integrity:** Databases are aware of relationships, ensuring that users can't modify data that could violate the relationship. This is done to ensure consistency and accuracy within the database. 

For example, if a user tried to update a record and put in something that doesn't exist, like an ID number that's not present, the database should reject the entry or change.

### Summary 
- An example of referential integrity is preventing the user from entering a record that refers to nonexistent data.
- Defining relationships helps you to reduce the repetition of data across tables, model real-world scenarios and requirements, and understand how your data should be stored.
- A cascading delete is when you delete a record and the database goes on and deletes other records associated with that record.
- You can use tables in a database without defining any relationships
- In a one-to-many relation, the value representing the 'many' side is the foreign key. It points to the primary key for the 'one' side of the relationship.
- When modeling a many-to-many relationship, you should name the linking table with a combination of the names of the tables it's linking.
- When you need to create a many-to-many relation, you need to generate a linking table that has a one-to-many relationship with two or more tables.
- Bank customers linked to their bank accounts is a scenario representing a one-to-many relationship as a customer can have multiple accounts, but one account can only belong to one customer.
- A one-to-one relationship allows only one record to be connected to only one other record.
