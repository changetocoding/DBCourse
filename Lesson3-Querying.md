# Lesson content
- Select
   - `as` (useful with joins) - 'Rename column to something useful'
   - Comma's important between column names
   - `select *`
- Select with a limit  - 'Give me top ...'
- Select distinct (with multiple columns too) -> 'How many distinct combinations are there?'
- where
  - ... in
  - `>,<, equals, like`
  - `Is (not) null`
  - `<>`
- Order by
- Joins (Left, Right, inner, outer)
- Group by & Aggregate functions
- Partion by (https://www.sqlshack.com/sql-partition-by-clause-overview/)
- Having clause
- Query within query

### Case insensitive

> IMPORTANT: sql is case insensitive


## Select

### Format for select statement
```sql
SELECT ...
FROM ...
WHERE ...
```

We can use * to select all the columns
```sql
select *
from Orders
```

### Specifying colums
Otherwise we must specify the columns. 
```sql
select [OrderID]
      ,[ShipName]
      ,[ShipAddress] as [Address To Ship To]
from Orders
```
![image](https://github.com/user-attachments/assets/f5f252f4-08cc-49b2-bb1d-df4a61e6a2ab)

- The comma `,` is important between the fields.
- The `as` keyword can be used to rename a column
- `[]` allows us to 'escape' the text (for example to add spaces)

### Limiting results
We can limit the results to the first n results. It is normally recommend to keep your queries fast unless you need the whole table

The way to do this varies by database so check for your database. SqlServer:
```sql
SELECT TOP (1000) [CustomerID] ,[CompanyName],[ContactName]
  FROM [dbo].[Customers]
```
See this for what other dbs do: https://www.w3schools.com/sqL/sql_top.asp


### Selecting distinct values
We can also select distinct values: 'How many distinct combinations are there?'
```sql
Select distinct [ContactTitle]
from customers
```
It can be done with multiple fields
```
Select distinct [ContactTitle], country
from customers
```
![image](https://github.com/user-attachments/assets/f96adae4-462e-4825-8a46-9df1f1364808)


### Combining columns
We can also do stuff like addition etc
```sql
SELECT  [OrderID]
      ,[ProductID]
      ,[UnitPrice]
      ,[Quantity]
      ,[Discount]
	  ,UnitPrice * Quantity as [TotalPrice]  
  FROM [Order Details]
```

Or combining text columns
```
SELECT '(' + [ContactTitle] + ') ' + [ContactName]
  FROM [Customers]
```
![image](https://github.com/user-attachments/assets/673f81a8-a6ca-4100-b200-9bfddcb3dcee)

## FROM
dbo is the default schema. Don't need to specify it. With other schemas you need to specify the schema
```sql
SELECT TOP (1000) [CategoryID]
      ,[CategoryName]
      ,[Description]
      ,[Picture]
  FROM [dbo].[Categories]
```

## Where
Where allows you to filter the results
```sql
SELECT *
FROM Customers
WHERE Country = 'Belgium'
```

### And/Ors
```sql
SELECT *
FROM Customers
WHERE Country = 'Belgium' 
OR Country = 'France'

SELECT *
FROM Customers
WHERE Country = 'Belgium' 
AND  City = 'Bruxelles'
```
![image](https://github.com/user-attachments/assets/639fde81-0720-4336-8939-40cb2b8be0c1)

Normally tables have an id field (e.g. `customerID`) which is useful for selecting a precise row you are looking form
```sql
SELECT *
FROM Customers
WHERE customerID = 'MAISD'
```
### Where Conditionals


We can rewrite the above or query using `in`. This allows you to specify multiple values that the field can contain:
```sql
SELECT *
FROM Customers
WHERE Country in ('Belgium','France')
```

More than/Less than
```sql
SELECT TOP (100) *
  FROM [Orders]
  where [Freight] > 30
  and [Freight] < 100
```

Not equals
```sql
SELECT *
FROM Customers
WHERE Country <> 'Belgium'
```
```sql
SELECT *
FROM Customers
WHERE Country not in ('Belgium','France', 'USA')
```

Nulls are a bit more tricky. You have to use the `IS` keyword
```sql
SELECT *
FROM Customers
WHERE Region is null

SELECT *
FROM Customers
WHERE Region is not NULL
```

Like allows you to compare if a string is similar to something
```sql
SELECT *
FROM Customers
WHERE ContactName like 'a%'
```

`_` represents a single character  
`%` wildcard represents any number of characters

Starts with:
```sql
SELECT *
FROM Customers
WHERE ContactName like 'a%'
```
Ends with with:
```sql
SELECT *
FROM Customers
WHERE ContactName like '%o'
```
They can also be combined
```sql
SELECT *
FROM Customers
WHERE ContactName like 'a%o'
```
Contains: in this case contact name contains 'an'
```sql
SELECT *
FROM Customers
WHERE ContactName like '%an%'
```

### Order by

```sql
SELECT orderId, Freight
FROM orders
order by freight
```
![image](https://github.com/user-attachments/assets/6f78dd38-7af9-4ccd-bd42-4e894a6e9a23)



```sql
SELECT orderId, Freight
FROM orders
order by freight desc
```
![image](https://github.com/user-attachments/assets/ed0eaab1-dc9c-4dae-b55a-6238ef4507f7)

### Homework

    Get all columns from the tables Customers, Orders and Suppliers
    Get all Customers alphabetically, by Country and name
    Get all Orders by date
    Get the count of all Orders made during 1997
    Get the names of all the contact persons where the person is a manager, alphabetically
    Get all orders placed on the 19th of May, 1997
