# Introduction lesson


## Current knowledge

Databases:
- 'CRUD' operations - Create, Read, Update, Delete
- Normal forms
- db server, database, Schemas, tables, 
- ER diagrams

Querying:
- Select
   - `as` (useful with joins)
- Select with a limit
- where
  - ... in
  - `>,<, equals like`
- Order by
- Joins (Left, Right, inner, outer)
- Group by & Aggregate functions
- Partion by (https://www.sqlshack.com/sql-partition-by-clause-overview/)
- Having clause
- Query within query


Manipulating data:
- Creating tables
- Data types
- Creating schemas
- Views
- primary keys
- When not to use primary keys
- Constraints
- Indexes, unique
- Update statement
- delete statement
- Add/Remove columns

Advance topics
- Triggers
- Stored Procedures
- 



## Setup
Sql setup

1. Download Sql server mgt. studio: [Download](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver15)
2. Download sql server express localdb: [Download](https://docs.microsoft.com/en-us/sql/database-engine/configure-windows/sql-server-express-localdb?view=sql-server-ver15)

## Install databases
### Northwinds (Doesn't create Db so we need to create one)
1. Create db. Call it northwinds  
![image](https://github.com/user-attachments/assets/8ff64087-45ed-427f-b23e-92bf389109d4)
2. Open a new query  
![image](https://github.com/user-attachments/assets/c842f4a2-fbb6-4499-9bd4-a431d99446b6)
3. Copy and paste the script from [here](https://github.com/microsoft/sql-server-samples/blob/master/samples/databases/northwind-pubs/instnwnd.sql)
4. Click `Execute`
![image](https://github.com/user-attachments/assets/a06296ab-22fa-4981-bb06-917a47a6dffc)

### Pubs (Script creates db)
1. Select the database server and right click -> new query  
![image](https://github.com/user-attachments/assets/b6c7b239-9525-4a75-85f6-a72d41623aa0)
2. Copy and paste the script from [here](https://github.com/microsoft/sql-server-samples/blob/master/samples/databases/northwind-pubs/instpubs.sql)
3. Click `Execute`  


