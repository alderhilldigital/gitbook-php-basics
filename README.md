# Introduction to PHP

PHP began in 1994 as a series of scripts called PHP/FI \(Personal Home Page/Forms Interpreter\), and it was written by a fellow named Rasmus Lerdorf to help him manage documents on his web site. Over the years, PHP grew into something more serious. In 1997, a second version of the system came out with additional functionality.

In late 1998, PHP 3.0 was released, leading to a major rewrite of the code and the involvement of two new developersZeev Suraski and Andi Gutmans. The goal was to support progressively broader and more complex applications on the web. In early 2000, version 4.0 was released. Based on a new language engine called the Zend Engine, this version had much better performance and increased code modularity. By late 2004, the much-evolved version 5.0 was released. It included many new features, such as new language constructs, broader web server support, sessions, and additional third-party extensions. Among the new language features was a significantly improved and expanded object-oriented programming model, which this book uses extensively. Somewhere along the way, PHP ceased to refer to "Personal Home Page" and came to mean "PHP Hypertext Preprocessor," a so-called recursive acronym. \(The acronym actually forms part of the term it defines!\)

PHP is a remarkably productive languageyou can sit down and crank out \(yes, that's the technical term\) large amounts of code in a short period of time, and this productivity is what drew me to it some years back. With PHP, I was able to put together surprisingly robust and dynamic travelogues of my journeys to various countries with relatively little code.





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



