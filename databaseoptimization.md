# Database Optimization

### Normalization
Edgar Codd defined three rules known as the **normalization rules** in the early 1970s to help organize data in a database. 
- **First normal form (1NF)**
- **Second normal form (2NF)**
- **Third normal form (3NF)**

These rules are formal criteria, building on top of each other, step by step. The database is in a normal form when a normalization rule has been applied to a database.

### First Normal Form (1NF)
The First Normal Form requires that the values in each cell are atomic and that tables have no repeating groups. Each field in every table has only **one value** and no columns exist where repeated kinds of data are present for each row.
- Duplicate rows don't exist in a table.
- The order of rows and columns isn't important to the data.

Violations of the First Normal Form are pretty easy to identify. These include:
- Multiple values in a cell
- Creating columns ending with numbers (e.g. FavoriteDish1, FavoriteDish2)
- Relying on the sequence of rows and columns 

Suppose a customer decided to place 2 orders of cheesecake. In a linking table, this would mean that there would be repeating duplicate rows.
- To fix this, we can assign a unique value for each row in the table that acts as a primary key.

### Second Normal Form (2NF)
The Second Normal Form requires that no value in a table should solely depend on part of a key to uniquely identify a row.
- For every value in a column that isn't a key, each value must rely on only the whole key.
- This issue occurs when a table uses a composite key (a key made up of multiple columns, like Event Name + Date)

Suppose you have an event that always occurs at the same location once every month. While the dates will differ, the name of the event and the name of the location will not. You can split this into another list so that you only need to write the location of an event once. One list can be event names tied to the location names, while the other list can be the event names and the dates they'll occur.

This way, your data is more safely stored, and the location is solely dependent on the event name.

### Third Normal Form (3NF)
The Third Normal Form requires that values shouldn't be stored if they can be calculated from another non-key field.

Suppose the price of dishes during lunch time is 50% off of the regular price. Creating a separate column to store lunch prices would be violating the third normal form. This can also be a problem if a user alters the price of one dish, but forgets to apply the same rule to the rest of the dishes. If the price of that one dish is supposed to be random (_the 50% rule doesn't apply to that dish_), then this would be fine.

Instead, have the database software multiply the regular prices by 0.5 to output lunch time prices.

### Denormalization
Denormalization is the process of intentionally duplicating information in a table, violating normalization rules. 

Building relationships between different tables and performing calculations can take up a lot of power and time, especially if the database needs to jump between different tables to collect values and add them together.

This is where you could break Third Normal Form on purpose. Calculate the total once when the customer pays, and save that final math answer directly into the main Orders table so it's instantly ready next time.

The problem here would be that you're trading safety for speed. It makes sense to take this risk only when you have a massive database that absolutely needs the speed.

### Summary
- Second Normal Form tells you to ensure that no non-key field is dependent on only part of a composite key in addition to being compliant with First Normal Form.
- If you can figure out the value of one non-key value field in a row by looking at another non-key field in that same row, you violate the Third Normal Form as it requires each field in a row to represent something unique about a record.
- In order to put a database into Third Normal Form, it must also be in First and Second Normal Form.
- Denormalization refers to consciously choosing to violate the rules of normality in order to improve speed or for some other business reason.
- First Normal Form tells you to remove repeating groups.
- If you need to prioritize the speed of a particular operation, you might choose to denormalize a table, as long as you remain aware of the threat to database integrity.
- The normalization process provides a framework to think about how data is organized, improving integrity, organizing tables, and reducing redundancy.
- If a table has two rows with the same values in all columns, adding a primary key to the table can help ensure that the table meets the first normal form requirements.
