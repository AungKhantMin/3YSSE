# Introduction Database and SQL

To Answer This Chapter You only need to know the basic statements of Mysql

1. SELECT - Use To retrieve data from Database
2. INSERT - Use to insert data into Database
3. UPDATE - Use to update existing data in the database
4. DELETE - Use to delete the data from table
5. REPLACE - replace data in a table. if the same record found it will replace the data
6. CREATE - Use to create table or Database
7. ALTER - Use to change the structures of tables
8. DROP - use to wipe out the table of Database
9. EXPLAIN - Use to get the information of tables;
10. DESC - Same as 9


## Creating Database

```mysql
CREATE DATABASE mydatabase; // you can replace your desire name in mydatabase

```

## Looking Databases

```mysql
  SHOW DATABASES;
```


## Creating Table


```mysql
  CREATE TABLE myatble (
    table_id int(10) NOT NULL AUTO_INCREMENT,
    name varchar(20) NOT NULL,
    PRIMARY KEY(table_id)
    );
```

## Looking Table information


```mysql

  EXPLAIN mytable;

```


## Adding Data Into tables


```mysql

  INSERT INTO mytable(name) VALUES('testing'),('ggwp');

```


## Retrieving data from tables

```mysql

  SELECT * FROM mytable;

```


## Connecting Mysql with php via PDO


```php

  // This is same for all connection just need to change database, username and
  // password

  $dsn="mysql:$host=localhost;$database=mydatabase";
  $username = 'root';
  $password = '****';
  $conn = new PDO($dsn,$username,$password);
  $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
  // This Line enable exception handling


  // reading Data

  $rows = $conn->query($sql); // all return rows will save as array in $rows

  foreach ($rows as $row) {
    echo $row['columnName']; // Access The data through column name in table
  }

```
