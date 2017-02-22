# Introduction to PHP

PHP scripts are generally saved with the file extension .php to signify their type. Whenever your web server is asked to send a file ending with .php, it first passes it to the PHP interpreter, which executes any PHP code in the script before returning a generated file to the end user. The basic unit of PHP code is called a statement, and ends with a semicolon to signify it is a complete statement. For clarity, one line of code usually contains just one statement, but you can have as many statements on one line as you want. These two examples do the same thing:



    &lt;?php

            // option 1

            print "Hello, ";

            print "world!";



            // option 2

            print "Hello, "; print "world!";

    ?&gt;



PHP purists like to point out that print is technically not a function and, technically, they are correct. This is why print doesn't require brackets around the data you pass to it. Other language constructs that masquerade as functions \(and are herein referred to as such for the sake of sanity\) include array, echo, include, require, return, and exit.

You can use parentheses with these constructs, and doing so is harmless:

    &lt;?php

            print\("Hello!"\);

    ?&gt;

Although on the surface, print and echo appear the same, they are not. The print construct behaves more like a function than echo because it returns a value \(1\). However, echo is more useful because you can pass it several parameters, like this:

    &lt;?php

            echo "This ", "is ", "a ", "test.";

    ?&gt;

To do the same using print, you would need to use the concatenation operation \(.\) to join the strings together, rather than a comma. If you have several things to print out, as in that example, then echo is preferred for the sake of clarity.





