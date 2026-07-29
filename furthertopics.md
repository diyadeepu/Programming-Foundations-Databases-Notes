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

1. Access Control\
   - 
