# Introduction to PHP

PHP scripts are generally saved with the file extension .php to signify their type. Whenever your web server is asked to send a file ending with .php, it first passes it to the PHP interpreter, which executes any PHP code in the script before returning a generated file to the end user. 

The basic unit of PHP code is called a statement, and ends with a semicolon to signify it is a complete statement. For clarity, one line of code usually contains just one statement, but you can have as many statements on one line as you want. These two examples do the same thing:

```
<?php

        // option 1

        print "Hello, ";

        print "world!";



        // option 2

        print "Hello, "; print "world!";

?>
```



