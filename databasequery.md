# Querying a database

### Creating a database
Once your blueprint (normalization) is complete, you need to actually build the database using DBMS and communicating with it through SQL.

SQL is the language used to give instructions to your database, but it's split into two different jobs:
- DDL (Data Definition Language)
  - Creates the empty database, tables, and columns
  - Use it when you're setting up your database for the first time or changing its layout (schema)
- DML (Data Manipulation Language)
  - Manages the actual information
  - Use it when you are adding new events, editing prices, or searching for specific orders inside the tables you already built.

 Use DDL first to tell DBMS to create the empty database and tables. Once the structure exists, switch to DML to start filling it with actual data.

 ### Creating tables
 To construct a table using SQL, use the CREATE command (from DDL). This is where you translate your design to code, ensuring the database clearly undestands what columns you need and the rules it needs to follow.

 When you build columns within your CREATE statement, apply strict rules (_constraints_) to ensure bad or incomplete data doesn't get in. This includes:
 - Primary Key & Auto-Increment: e.g. Set CustomerID as the unique identifier. Auto-increment will have the database number every new customer (1, 2, 3, ...).
 - Data Types: Tell the database what kind of data to expect (ID would be numbers, while names would be text) 
 - NOT NULL: Setting the column to this blcok DBMS from saving a row if a value is missing.
 - Foreign Keys: Forms the bridge between tables. Rather than typing out dish names, you can use foreign keys that directly link the exact dish id in your separate Menu table.

SQL Sample Code:

CREATE TABLE Customers {
CustomerID INT(6) NOT NULL AUTO_INCREMENT,
FirstName VARCHAR(200) NOT NULL,
LastName VARCHAR(200) NOT NULL,
Email VARCHAR(200),
Address VARCHAR(200),
City VARCHAR(200),
State CHAR(2),
Phone VARCHAR(20) NOT NULL,
Birthday DATE,
FavoriteDish INT(6) REFERENCES Dishes(DishID)
PRIMARY KEY(CustomerID)
}

### Writing SQL Queries
 **Query:** a structured request, or question, asking the database to get, modify, or analyze data.
 - In SQL, you do this by using the SELECT command. The SELECT command tells the database what columns you want to see. FROM tells it which table to look inside.

With the SELECT command, you can either ask the database to return the entire table or specific parts from the table.

For example, if you want to grab the entire Customers table, use **SELECT * FROM Customers;**
- The asterisk acts as a wildcard, meaning "all columns"
- While this is great to quickly view the database, it can slow the system if the database is massive.

If you want to grab just the first name, last name, and email from the Customers table, use SELECT FirstName, LastName, Email FROM Customers;
- This return a clean, focused list without wasting too much power loading all data

### Narrowing query results
If SELECT picks out the columns you want to see, WHERE picks the specific **rows**. Without it, the database gives you everything. With it, you only get the records matching your exact rules.

Add the WHERE clause right after your FROM clause to act as a filter.
- WHERE State="CA" will return customers only in California
- WHERE State="CA" OR State="OR" will retun customers from either state.
- WHERE State LIKE "C%" will return customers from states starting with a C (California, Colorado, Connecticut, etc)

OR is used to expand your search to include multiple acceptable answers. LIKE is used when you only know part of a word. % acts like a wildcard standing in for any missing letters.

Finding dates can be tricky, especially if it stores a Date AND Time. To find just a date, you can use an exact match (WHERE Birthday="2000-01-01"). If it stores a Date AND Time, an exact match will fail unless you guess the exact second in which the reservation was made.

To fix this, you can search using a range. For example, you could say to give all reservations > "2026-02-06" AND < "2026-02-07"

The position of the % matters!
- LIKE "C%" means to find words starting with C, followed by anything
- LIKE "%c" means to find words that start with anything, but end with c
- LIKE "%c%" means to find words that have a c anywhere inside them

### Sorting results
When searching a database, you want answers returned in a neat and organized format (e.g. alphabetical, cheapest to most expensive).

We use the **ORDER BY** command at the very end of our SQL query to tell the database how to sort the final list. Since the database knows the type of data in each column, it's able to identify the most logical way to sort it:
- **Text (Alphabetical):** ORDER BY Name (Sorts from Apple to Zucchini)
- **Numbers (Math):** ORDER BY Price (Sorts from lowest to highest price)
- **Dates (Chronological):** ORDER BY Date (Sorts from oldest to newest dates)
- **Ascending (ASC):** Default → Database assumes you want normal A to Z, therefore you don't even have to type ASC
- **Descending (DESC):** Backwards list → You need to explicitly tell the database to flip it
  - e.g. ORDER BY Price DESC

You can combine filters (e.g. WHERE) with sorters (ORDER BY), but make sure to do it in the right sequence: filter the data first, then sort whatever is left over.

### Aggregrate Functions
Aggregate function use more than one piece of data to generate a value. Rather than reading through a massive list of daa, it's easier to get a single answer, like a total count or an average price. Aggregate functions can be used to do all the heavy calculations.

The 5 Main Math Commands:
- COUNT(): counts how many rows match your search
  - e.g. SELECT COUNT(FirstName) FROM Customers WHERE State="CA"; (_This returns a single number rather than listing all customers._
  - Always count a column that isn't allowed to be blank (e.g. ID / Name), or else the database could skip empty rows, messing up your count.
- SUM(): adds up all the numbers in a column
  - e.g. SELECT SUM(Price) FROM Dishes; (_This calculate the total cost of your order._)
- AVG(): calculates the average number
  - e.g. SELECT AVG(Price) FROM Dishes; (_This tells you the average cost of an item on your menu._)
- MIN() & MAX(): finds the absolute lowest or highest value in a column
  - e.g. SELECT MIN(Price), MAX(Price) FROM Dishes; (_Instantly finds the cheapest and most expensive menu items_)
 
All math commands can be combined into a single query to quickly generate reports or summaries without crashing your computer.

### Joining Tables
Nomalization splits your data into separate tables, so you eventually nned a way to put it back together for it to make sense to a human reading it.

Without connecting tables, if you ask the database for a list of customers and their favorite dishes, it will return raw IDs: _Taylor likes Dish #15_, making the data returned useless.

You can use the command JOIN to connect two different tables. JOIN tells the database to look at 2 separate tables at once and match up their corresponding row.

1. Pick your readable columns with SELECT. Ask you the actual words you want to see not the numbers.
  - e.g. SELECT Customers.FirstName, Dishes.Name
2. Declare your tables with JOIN. Tell the system which two tables are being combined.
  - e.g. FROM Customers JOIN Dishes
3. Provide the map with ON. You need to tell the database exactly which columns act as the matching link between the two tables.
  - e.g. ON Customers.FavoriteDish = Dishes.DishID (_Whenever the 'Favorite Dish' number in the customer table matches the 'Dish ID' number in the menu table, stitch those 2 rows together._)

Once you're able to do this, you can connect more tables at once, like pulling a customer's name, reservation time, and the price of their order into a single, easy to read report.

Example:

SELECT FirstName, LastName, FavoriteDish, Dishes.'Name'| FROM Customers
JOIN Dishes ON Customers.FavoriteDish = Dishes.DishID;

Output:

| FirstName | LastName | Favorite Dish | Name |
| --- | --- | --- | --- |
| Taylor | Jenkins | 8 | Chef's Salad |
| Anna | Smith | 13 | Tofu Skewers |
| Sam | Thomas | 24 | French Onion Soup |
| Nicole | George | 19 | Spinach Ravioli |


### Modifying Data

To modify actual information inside table (create, update, delete), three commands you can use are:
1. INSERT (Create): adds a brand new row. You tell the database which columns you filled and provide it values.
   - e.g. INSERT INTO Customers (FirstName, LastName) VALUES ("John", "Doe");
2. UPDATE: changes existing data, such as fixing typos or updating a phone no.
   - e.g. UPDATE Customers SET Email="new@email.com" WHERE CustomerID=1;
3. DELETE: permanently erases an entire row from the table
   - e.g. DELETE FROM Customers WHERE CustomerID=26;

Modifying data, however, can be extremely dangerous as there isn't any way to undo changes. To avoid this, ensure the following:
1. **Always use the primary key.** For example, if you wanted to delete a customer named "Anna", don't ever use WHERE FirstName="Anna" (_EVERY SINGLE CUSTOMER WITH THE NAME 'ANNA' WILL BE DELETED FROM THE SYSTEM_). Instead, use their exact, unique ID number (e.g. WHERE CustomerID=28)
2. **Don't forget the WHERE clause.** If you typed UPDATE Customers SET Email="test@test.com" and forget to add the WHERE filter at the end, the database will instantly overwrite _every single customer's email_ in the entire table to that test email. Ensure to always run a SELECT search first so that you target the right row.
