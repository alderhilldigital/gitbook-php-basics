# IF

PHP allows you to choose what action to take based on the result of a condition. This condition can be anything you choose, and you can combine conditions to make actions that are more complicated. Here is a working example:

```
<?php

        $Age = 20;

        if ($Age &lt; 18) {

                print "You're young - enjoy it!\n";

        } else {

                print "You're not under 18\n";

        }



        if ($Age &gt;= 18 && $Age &lt; 50) {

                print "You're in the prime of your life\n";

        } else {

                print "You're not in the prime of your life\n";

        }



        if ($Age &gt;= 50) {

                print "You can retire soon - hurrah!\n";

        } else {

                print "You cannot retire soon :\( ";

        }

?>
```

At the most basic level, PHP evaluates if statements left to right, meaning that it first checks whether $Age is greater or equal to 18, then checks whether $Age is less than 50. The double ampersand, &&, means that both statements must be true if the print "You're in the prime of your life\n" code is to be executedif either one of the statements is not true for some reason, "You're not in the prime of your life" is printed out instead. The order in which conditions are checked varies when operator precedence matters; this is covered in the next chapter.

As well as &&, there is also \|\| \(the pipe symbol printed twice\) which means OR. In this situation, the entire statement is evaluated as true if any of the conditions being checked is true.

There are several ways to compare two numbers. We have just looked at &lt; \(less than\), &lt;= \(less than or equal to\), and &gt;= \(greater than or equal to\). We will be looking at the complete list later, but first I want to mention one important check: = =, or two equals signs put together. That means "is equal to." Therefore 1 == 1 is true, and 1 == 2 is false.

The code to be executed if the statement is true is in its own block \(remember, a block starts with { and finishes with }\), and the code to be executed otherwise is in an else block. This stops PHP from trying to execute both the true and false actions.

One key thing to note is that PHP practices "if statement short-circuiting"this is where PHP will try to do as little conditional work as possible, so it basically stops checking conditional statements as long as it is sure it can stop. For example:

```
if ($Age > 10 && $Age < 20)
```

If $Age evaluates to 8, the first check \($Age &gt; 10\) will fail, so PHP will not bother checking it against 20. This means you can, for example, check whether a variable is set and whether it is set to a certain valueif the variable is not set, PHP will short-circuit the if statement and not check its value. This is good because if you check the value of an unset variable, PHP will flag an error.

A helpful addition to if statements is the elseif statement, which allows you to chain conditions together in a more intelligent way:

```
<?php

        if ($Age &lt; 10) {

                print "You're under 10";

        } elseif ($Age &lt; 20) {

                print "You're under 20";

        } elseif ($Age &lt; 30) {

                print "You're under 30";

        } elseif ($Age &lt; 40) {

                print "You're under 40";

        } else {

                print "You're over 40";

        }

?>
```

Section 4.9.  Conditional Statements

Perl users should note that it is spelled elseif and not elsif.

You could achieve the same effect with if statements, but using elseif is easier to read. The downside of this system is that the $Age variable needs to be checked repeatedly.

If you only have one statement of code to execute, you can do without the braces entirely. It's a readability issue.

So, these two code chunks are the same:

```
<?php

if ($banned) {

        print "You are banned!";

}



if ($banned) print "You are banned!";

?>
```



