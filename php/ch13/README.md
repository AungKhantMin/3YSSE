# Retrieving Data From Mysql with php

### The Binary Attribute and Collation

In General, mysql is not case sensitive, so if we need to compare between text
'b'  will equal to "B" so that will tricky. By  using **BINARY** attribute it will
compare the binary value of text. so the problem solve.


### The Unique constraints

Unique keys are like primary key. But they are little different. A table can
contain a lot of Unique keys but there must be only one primary key. Unique key
can contain  **NULL** Values and Primary Key cannot contain **NULL** Values.


### The Enum Data type

Enum Datatype Is use. when we only want to accept the certain values for columns.
For Example

```mysql

  color ENUM('red', 'blue','green')
```
We can only add red, blue, green value to color


### Retrieving Data with SELECT

1. Limit The numbers of rows return
2. Sort returned rows in any order
3. Use Pattern Matching
4. Summarize returned data
5. Eliminate duplicate rows
6. Group results together
7. Use joins to extract data from multiple tables
8. Use various MySQL functions to further enhance the power of your queries


### Limit The numbers of rows return

```mysql

    # Limiting the rows by using where clause

    SELECT * FROM furit WHERE name='banana';


    # Limiting the rows by LIMIT keyword

    SELECT id, username FROM members LIMIT 4;


    # By Default Limit will count the rows from first, but we can change it by
    # giving two numbers to LIMIT

    SELECT id, username FROM members LIMIT 1,2;

    # This Query will show the row froms 2 to 3
```
