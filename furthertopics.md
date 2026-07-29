# Further Database Topics

### Indexes, transactions, and stored procedures
To make your system more secure, safer, and faster, DBMS tools offer three advanced features:

1. Indexes
   - Creates a quick reference list for a specific column, like LastName
   - Think of it like the index at the back of a textbook
   - The database uses index to jump instantly to the exact location, giving you the benefit of speed.
   - They slow down creating data → Every time you insert a new row, the database takes more time updating the index.
2. Transactions
   - It groups a batch of multiple SQL commands together into a single "all-or-nothing" block.
   - Prevents half-finished jobs → e.g. If a customer pays for an order, the database has to (1) deduct inventory and (2) record the payment.
      - If the server crashes after step 1, a transaction will instantly "roll back" (undo) the inventory change so your database doesn't get corrupted with missing items and no money.
   - Either every command in the transaction succeeds, or the entire block is canceled.
3. Stored Procedures
   - A complex SQL script or query that you write once and save permanently on the database server.
   - If you run a massive, complicated JOIN query every morning for a report, you don't need to retype it → Just trigger the saved procedure.
   - Database administrators use these as guards by locking users out of the raw table completely. Users can only interact with the data through safe, pre-approved procedures.
     - This way, people don't accidentally type dangerous commands or access sensitive data they shouldn't see.

### Access control, compliance, and injection
Databases can contain sensitive information, so it's crucial to actively control visibility access and protect the system from malicious attacks. Security is a continuous process, not a one-time setup.

1. Access Control
   - Create specific user accounts with strict permission levels instead of letting everyone access the database
   - Grant an administrator full power to modify the database structure (schema), while providing standard employees a "Read-Only" account
     - This way, they can still look up data, but can't accidentally delete or change anything.
2. Compliance
   - Government laws dictate exactly how to store and protect your Personally Identifiable Information (PII)
   - If you fail to design your database to comply with these major privacy laws, e.g. HIPAA, it can lead you to pay massive, costly legal fines.
3. SQL Injection
   - If your system is poorly designed, any attacked could type in a destructive SQL command into a normal input box (e.g. "; DROP TABLE Customers; into a "Last Name" field). The system could read that input as a real command and actually erase your entire table.
   - Use secure programming practices to clean and process all user inputs.
   - Train the database to treat whatever the user types strictly as harmless text, never as executable code.

### Software Options
Choose a DBMS that matches the style and size of your project as not all databases are built for the same job.
1. Size Scale (Traditional Relational Databases)
   - Micro: _SQLite_. Perfect for tiny, local jobs, like saving user preferences directly inside a single mobile phone app.
   - Desktop: _Microsoft Access or FileMaker Pro_. Built for small projects with just a few users, usually running locally on a single computer rather than a massive server.
   - Middle Ground: _MySQL or MariaDB_. Flexible, cost effective, and great for everything from a quick prototype to an app with thousands of daily users.
   - Enterprise: _Oracle, Microsoft SQL Server, SAP HANA_. Built to handle millions of simultaneous interactions for massive companies.
     - They're incredibly powerful, but come with high licensing and infrastructure costs.
2. Beyond the Table (NoSQL & Big Data)
   - NoSQL: "Not Only SQL"
   - Traditions tables are too rigid for messy, unpredictable data. You can't easily fit continuous streams of social media comments, complex webs of Facebook friends, or massive piles of unstructured "Big Data" into a neat Excel-style grid.
   - NoSQL databases don't have the strict table rules. They can store unstructured data exactly as it naturally flows
   - If the data gets really massive, engineers switch to specialized processing frameworks, like Hadoop or Spark).
