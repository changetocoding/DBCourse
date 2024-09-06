# Joins And Aggregate Functions

### Lesson Content
Last week lesson focused on querying one table. This week we'll look at querying multiple tables and aggregation functions

- Group by & Aggregate functions
- Partion by (https://www.sqlshack.com/sql-partition-by-clause-overview/)
- Having clause
- Joins (Left, Right, inner, outer)
- Query within query

## Aggregate functions

### Group By
Group by allows us to group rows together. The result of a query using a GROUP BY statement contains one row for each group.

```sql
SELECT CustomerID, count(*) as [No of orders]
  FROM [Orders]
  group by CustomerID
```
![image](https://github.com/user-attachments/assets/2c167f08-62c4-42b7-9b02-3ee34708da79)


> [!NOTE]
> In this case can do `count(*)` or `count(CustomerID)`.

### Common Aggregate Functions
    - Count(expression) - Quantity of matching records (per group)
    - Sum(expression) - Summation of given value (per group)
    - Min(expression) - Minimum of given value (per group)
    - Max(expression) - Maximum of given value (per group)
    - Avg(expression) - Average of given value (per group)

E.g. What is the average quantity ordered for each product
```sql
SELECT ProductID, Avg(Quantity) as [Average Qty]
  FROM [Order Details]
  group by ProductID
```

What is the total number of items and total cost for each order
```sql
SELECT OrderID
	,Sum(Quantity) as [Total Qty]
	,Sum(Quantity * UnitPrice) as [Total Price]
	,Count(*) as [Number of items in order]
  FROM [Order Details]
  group by OrderID
```
![image](https://github.com/user-attachments/assets/e14a6da1-9b42-4d03-81b7-d5aa2df99cb2)


> [!WARNING]
> In the select you're only allowed to use aggregate functions or fields in the group by. You'll get a `Column 'Orders.OrderID' is invalid in the select list because it is not contained in either an aggregate function or the GROUP BY clause.
` error instead


### Multiple fields in group by

A group by can also include multiple fields and you can apply where, order by etc.

e.g. How much do people order for product Id 1
```sql
SELECT ProductID, Quantity, count(*) as [Number of orders with qty]
  FROM [Northwinds].[dbo].[Order Details]
  where productId = 1
  group by ProductID, Quantity
```

### Having
How would you write this query
> Which customers have more than 20 orders


Having allows you to filter the results of a group by. Notice you can't use where to filter the results of a group by
```sql
SELECT CustomerID, count(*)
  FROM [Northwinds].[dbo].[Orders]
  group by CustomerID
  having count(*) > 20;

  Go
```
> [!NOTE]
> `;` ends an sql query
> `GO` Executes the query. Useful when have multiple queries together

- `Where` Filters before the group by is run
- `Having` Filters after the group by is run

e.g. 
| Colour   | Shade     |
| ---      | ---       |
| Blue     | Light     |
| Red      | Blood     |
| Blue     | Navy      |
| Green    | Forrest   |

```sql
Select count(*)
from [colours]
where colour in ('Blue', 'Green')
Group By colour
```

Is equivalent to a group by on:
| Colour   | Shade     |
| ---      | ---       |
| Blue     | Light Blue|
| Blue     | Navy Blue |
| Green    | Forrest   |


## Nested queries: Query within a query
We can use a query within the where clause. For example:

Get me the details of orders which are shipped to belgium:
```sql
select * 
from dbo.[Order Details]
where OrderID in (
	select OrderID
	from dbo.Orders
	where shipCountry = 'Belgium'
)
```

## Joins - Working with multiple table
So far only focused on one table but as covered in relational lesson tables normally related to other tables and you have to join them to get information

We use a venn diagram to describe joins Venn

![Visual_SQL_JOINS_orig-1842961435](https://github.com/user-attachments/assets/3dfd1865-a7ca-4366-a54f-24d8065dbfd8)

![sqlJoins_7-2030296519](https://github.com/user-attachments/assets/04b82a53-1d1e-4d99-94dc-95bca4e8baee)

### Cross joins
You'll never use. Cartesian product of rows from tables in the join. In other words, it will produce rows which combine each row from the first table with each row from the second table
```
SELECT *
FROM [Orders], [Customers];
-- OR
SELECT *
FROM [Orders] cross join [Customers];
```

### Inner join
Returns only what is on both tables
```
SELECT *
FROM [Customers] c
INNER JOIN [orders] o on c.CustomerID = o.CustomerID
```
![inner-join-in-sql-2205146387](https://github.com/user-attachments/assets/6accb98a-4e48-46db-be41-a287cebd0fc8)


### Left JOIN
Always contains all rows of the "left" table (A), even if the join-condition does not find any matching row in the "right" table (B)

```sql
select * 
from dbo.Orders o 
left join dbo.[Order Details] od on o.OrderID = od.OrderID
where o.shipCountry = 'Belgium'
```

> [!NOTE]
> Right outer join is the same but the key table is the second table
> Also called a left/Right outer join

### Union
Rarely use but useful to know
```sql
SELECT City, CompanyName, ContactName, 'Customers' AS Relationship 
FROM Customers
UNION SELECT City, CompanyName, ContactName, 'Suppliers'
FROM Suppliers
```


### Homework
Northwinds:
1. Which products have been ordered and shipped to Belgium (i.e what products do we sell in belgium)
2. Create an alphabetical list of products. Include the category name for each product
3. Find all Products above the average product price
4. Join orders details and Products table so we have the product name for every row on the orders details table
5. What is the total units on order for each supplier. Display as supplier name, total units on order
Pubs:
1. Display a list containing each employees first name, last name and job title
2. Using only the `[sales]` table, get the Total quantity of sales for each stor_id
3. What is the average price for each type of book
4. Who wrote the book 'Prolonged Data Deprivation: Four Case Studies'
5. Display a list of book titles with the name of the author. Where a book has multiple authors have a new line for each author (aka book title is repeated)
6. 
