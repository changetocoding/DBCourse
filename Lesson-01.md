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



## Setup LocalDB
[Microsoft guide](https://docs.microsoft.com/en-us/sql/database-engine/configure-windows/sql-server-express-localdb?view=sql-server-ver15)
1. Install using link above or through the Visual Studio Installer, as part of the ASP.NET and web development workload, or as an individual component.
2. It should automatically be running. If it isn't you can start it by running in command prompt
```
SqlLocalDB start MSSQLLocalDB
```
3. Connect to it via SQL Server.    
Server name: (localdb)\MSSQLLocalDB  
Authentication: Windows Authentication
4. Create a new database in SQL Server
5. Run database setup script (to be provided by a colleague)

Please note that depending on the version you download and install your server name may differ (in step 3, (localdb)\MSSQLLocalDB may be something else like (localhost)\SQLEXPRESS)

