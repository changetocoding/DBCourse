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



## Select
Format for select statement
```
Select ...
from ...
where ...
```

We can use * to select all the columns
```
select *
from Orders
```

Otherwise we must specify the columns. 
```
select [OrderID]
      ,[ShipName]
      ,[ShipAddress] as [Address To Ship To]
from Orders
```
![image](https://github.com/user-attachments/assets/f5f252f4-08cc-49b2-bb1d-df4a61e6a2ab)

- The comma `,` is important between the fields.
- The `as` keyword can be used to rename a column
- `[]` allows us to 'escape' the text (for example to add spaces)


#
