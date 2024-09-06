# Joins And Aggregate Functions

### Lesson Content
Last week lesson focused on querying one table. This week we'll look at querying multiple tables and aggregation functions

- Group by & Aggregate functions
- Partion by (https://www.sqlshack.com/sql-partition-by-clause-overview/)

- Joins (Left, Right, inner, outer)
- Having clause
- Query within query

## Aggregate functions

### Group By
Group by allows us to group rows together. The result of a query using a GROUP BY statement contains one row for each group.

### Common Aggregate Functions
    - Count(expression) - Quantity of matching records (per group)
    - Sum(expression) - Summation of given value (per group)
    - Min(expression) - Minimum of given value (per group)
    - Max(expression) - Maximum of given value (per group)
    - Avg(expression) - Average of given value (per group)

```sql
SELECT CustomerID, count(*) as [No of orders]
  FROM [Orders]
  group by CustomerID
```
![image](https://github.com/user-attachments/assets/2c167f08-62c4-42b7-9b02-3ee34708da79)


> [!NOTE]
> In the select you're only allowed to use aggregate functions or fields in the group by. You'll get a `Column 'Orders.OrderID' is invalid in the select list because it is not contained in either an aggregate function or the GROUP BY clause.
` error instead


> [!NOTE]
> can do `count(*)` or `count(CustomerID)`. They are equivalent (ish)

### 



