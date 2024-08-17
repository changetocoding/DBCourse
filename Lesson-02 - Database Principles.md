# Lesson 2 - DB Principles and concepts


## Database hierarchy
![image](https://github.com/user-attachments/assets/7e2fa64d-d451-4350-9af1-e96b39579236)


## Concepts
- CRUD
- Transactions, commited
- ACID (Transactions)
  - Atomicity - All or nothing - Succeeds or fails as a single unit
  - Consistency - Transactions can only bring the db from one consistent state to another
  - Isolation - multithreading/concurrency (Different isolation levels and depending on them effects of an incomplete transaction might not be visible to other transactions)
  - Durability - Once commited always presevered (aka save to hdd). In event of a system crash.
  

![acid3-2655829202](https://github.com/user-attachments/assets/27a467b1-2310-4214-8b80-3199700b7cc8)



## Normal Forms (Database normalization)
https://en.wikipedia.org/wiki/Database_normalization

Reduces data redundancy and improve data integrity

Originally defined by E. F. Codd in 1971

### 1NF: No Repeating Elements or Groups of Elements
In the first normal form each field contains a single value. A field may not contain a set of values or a nested record

_PK_ is primary key

| _Title_ | Author | Category | Pages | Author Nationality | _Format_ | Price |  
|-------|-------|-------|-------------|--------------------|--------|------|
| DB Rules |John Doe| Database, IT, SQL | 500 | British | Hardcover | 49.99 |  

Solve it by separating category into separate table

**Book**
|_Title_| Author| Pages|Author Nationality| _Format_ | Price|
|-------|-------|-------|------------------|--------|------|
|DB Rules|John Doe| 500| British | Hardcover | 49.99|


**Category**
| _Title_ | _Category_ |
|----------|------------|
| DB Rules | Database |
| DB Rules | IT |
| DB Rules | SQL |


### 2NF: No Partial Dependencies on a Concatenated Key
A relation (or table) is in 2NF if:

1. It is in 1NF and has a single attribute unique identifier (UID)(in which case every non key attribute is dependent on the entire UID), or
2. It is in 1NF and has a multi-attribute unique identifier, and every regular attribute (not part of the UID) is dependent on all attributes in the multi-attribute UID, not just one attribute (or part) of the UID.

In this case price only depends on format:

|_Title_| Author| Pages|Author Nationality| _Format_ | Price|
|-------|-------|-------|------------------|--------|------|
|DB Rules|John Doe| 500| British | Hardcover | 49.99|
|DB Rules|John Doe| 500| British | Paperback | 19.99|
|Models of DB|Peter Coulson| 200| German |Hardcover | 39.99|

Can add a Price table


**Book**
|_Title_| Author| Pages|Author Nationality|
|-------|-------|------|------------------|
|DB Rules|John Doe| 500|  British |
|Models of DB|Peter Coulson| 200| German |

**Price**
|_Title_| _Format_ | Price |
|----------|-----|-------|
|DB Rules| Hardcover | 49.99|
|DB Rules| Paperback | 19.99|
|Models of DB| Hardcover | 39.99|


### 3NF: Nothing but the key
"[every] non-key [attribute] must provide a fact about the key, the whole key, and nothing but the key so help me Codd"

Author nationality depends on author, not the key (Title)

## ER diagrams
https://www.lucidchart.com/pages/er-diagrams


**Book**
|_Title_| Author| Pages|
|----------|-----|-------|
|DB Rules|John Doe| 500|
|Models of DB|Peter Coulson| 200|

**Author**
| _Author_| Author Nationality|
|----------|------------|
|John Doe|  British |
|Peter Coulson|  German |


**We are done**


## Homework

1. Read up more on acid
2. Practise Normal forms
   - https://cs-uob.github.io/COMS10012/exercises/part1/db2/normalforms.html
   - http://phlonx.com/resources/nf3/
3. Draw an ER diagram for one of NFs you create.
