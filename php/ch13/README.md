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



### Sorting result

```mysql

  #result will sort according to the firstName
  SELECT username, firstName, lastName FROM members ORDER BY firstName;


  # result will be sort according to the favoriteGenre and firstName
  # when sorting favoriteGenre is first priority and firstName is second priority
  SELECT favoriteGenre, firstName, lastName FROM members ORDER BY favoriteGenre, firstName;



  #result will be sort according to the descending order of favoriteGenre and ascending order of firstName
  SELECT favoriteGenre, firstName, lastName FROM members ORDER BY favoriteGenre DESC, firstName ASC;


```



### Use pattern Matching

There are two wild card symbols to use in searching data '%' and '_'

'%' is use when we want to find words or one or more characters
'_' is use when you want to find the exactly one character  value in tables  

```mysql

  # This will return all data which contain 'travel'
  SELECT username, firstName, lastName, otherInterests FROM members
  WHERE otherInterests LIKE ‘%travel%’;

  # This Will return the only exact values.
  SELECT firstName, lastName FROM members WHERE firstName LIKE ‘Mar_y’


  # This is same with % but it is use NOT LIKE instead of LIKE
  # so it will return the data which do not contain travel
  SELECT username, firstName, lastName, otherInterests FROM members
  WHERE otherInterests NOT LIKE ‘%travel%’;


```


### Summarizing Data

1. count() — Returns the number of rows selected by the query
2. sum() — Returns the total of all the values of a given field selected by the query
3. min() — Returns the minimum value of all the values of a given field selected by the query
4. max() — Returns the maximum value of all the values of a given field selected by the query
5. avg() — Returns the average of all the values of a given field selected by the query
