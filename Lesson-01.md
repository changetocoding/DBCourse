# Introduction lesson


## Current knowledge

Querying:
- Select
- Select with a limit
- Order by
- joins
- Group by & Aggregate functions
- Having clause

Manipulating data:
- Creating tables
- primary keys
- constraints
- Indexes
- Update statement
- delete statement

## Setup
Sql setup

1. Download Sql server mgt. studio: https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver15
2. Download sql server express localdb: https://docs.microsoft.com/en-us/sql/database-engine/configure-windows/sql-server-express-localdb?view=sql-server-ver15
3. Download database and restore it to localdb instance: https://docs.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver15&tabs=ssms
4. Create new project: Make sure .net core console app. Add Entityframework nuget package (make sure entity framework core one)
5. Crack on

In sql server mgt server was [ComputerName]\SQLEXPRESS
My connection string was "Server=localhost\SQLEXPRESS;Database=master;Trusted_Connection=True;"
