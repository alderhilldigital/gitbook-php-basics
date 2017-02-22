# Variables

Variables are things that store data. In PHP they begin with $ followed by a letter or an underscore, then any combination of letters, numbers, and the underscore character. This means you may not start a variable with a number.

Variables are case-sensitive, which means that $Foo is not the same variable as $foo, $FOO, or $fOO.



Assigning variables is as simple as using the assignment operator \(=\) on a variable, followed by the value you want to assign. Here is a basic script showing assigning and outputting datanote the semicolons used to end each statement:

    &lt;?php

            $name = "Paul";

            print "Your name is $name\n";

            $name2 = $name;

            $age = 20;

            print "Your name is $name2, and your age is $age\n";

            print 'Goodbye, $name!\n';

    ?&gt;

There we set the $name variable to be the string Paul, and PHP lets us print out that variable after Your name is. Therefore, the output of the first print statement is Your name is Paul, because PHP will substitute $name for its value whenever it finds it by itself, or inside a double-quoted string \(that is, one starting and ending with"\).

We then set $name2 to be $name, which effectively copies $name's value into $name2. $name2 is now set to Paul. We also set up the $age variable to be the number 20. Our second print statement outputs both variables at once, as again, PHP will substitute them inside the string.

However, the last print statement will not replace $name with Paul. Instead, it will print:

    Goodbye, $name!\n

The reason for this is that PHP will not perform variable substitution inside single-quoted strings, and won't even replace most escape characters \(the exception being \'\). In double-quoted strings, PHP will replace $name with its value; in a single-quoted string, PHP will consider $name to mean that you actually want it to output the text $name just like that.



When you want to append something to your variable while inside a string, PHP may consider the characters to be part of the variable. For example:



    &lt;?php

            $food = "grapefruit";

            print "These $foods aren't ripe yet.";

    ?&gt;



While the desired output was These grapefruits aren't ripe yet, the actual output is different: because we have added the "s" to the end of the variable name, we have changed it from trying to read $food to trying to read $foods. The variable $foods does not exist, so PHP will leave the space blank and may generate an error. There are two ways to solve this:



    &lt;?php

            $food = "grapefruit";

            print "These ${food}s aren't ripe yet.";

            print "These {$food}s aren't ripe yet.";

    ?&gt;



The braces, { and }, technically signal a variable variable when used inside a string, but in the example above, they are used to tell PHP where the variable ends. You don't need to use braces where characters being appended to a variable would make the variable name illegal, like this:



    &lt;?php

            $food = "grapefruit";

            print "This $food's flavour is bad.";

    ?&gt;



That will work because you are not allowed to use apostrophes as part of your variable names.



