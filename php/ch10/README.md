## All Things We Need To Know About Chapter 10
###### Query String, Cookie, Sessions

### Query String

The Working Process Of Query String is Like Get Method.

syntax

```php
    $name= "Jhon"
    $age = "blah"
    echo "<a href='test.php?age='.$age.'&amp;name='.$name/>";

```

Query String Sent Data Using GET method

### Cookie

There Is Only Tow Things You need To know about Cookie to pass the exam.
How To set Cookie and How To Delete Cookie, And One More How To use array with cookie

syntax

```php

    // Creating Cookie
    setcookie('Cookie Name', 'cookie Value', time()+60*60*24*365);
    // here mark the time value fixed :3 it will be goods for you :)

    // Deleting Cookie

    setcookie('Cookie Name', "", time()-3600);
    // Change The Time and set value to null

    // Playin With Cookie array
    setcookie('test[$n]', 'value', time()+3600);

    //Accessing Cookie Through Global Variable
    //$_COOKIE is The Global variable to access cookies store in browser

    // Accessing Normal Cookie

    $_COOKIE['name'];

    // Accessing Array Cookie

    $_COOKIE['name'][$n];

    // This Is all You need to know about

```
