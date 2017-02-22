# Switch

Your if...elseif blocks can become unwieldy when you have a series of conditions that all test against the same variable, as here:

```
<?php

        $Name = "Bob";

        if \($Name =  = "Jim"\) {

                print "Your name is Jim\n";

        } elseif \($Name =  = "Linda"\) {

                print "Your name is Linda\n";

        } elseif \($Name =  = "Bob"\) {

                print "Your name is Bob\n";

        } elseif \($Name =  = "Sally"\) {

                print "Your name is Sally\n";

        } else {

                print "I don't know your name!\n";

        }

?>
```

PHP has a solution to this: switch/case. In a switch/case block, you specify what you are checking against, then give a list of possible values you want to handle. Using switch/case statements, we can rewrite the previous script like this:

```
<?php

        $Name = 'Bob';

        switch\($Name\) {

        case "Jim":

                print "Your name is Jim\n";

                break;

        case "Linda":

                print "Your name is Linda\n";

                break;

        case "Bob":

                print "Your name is Bob\n";

                break;

        case "Sally":

                print "Your name is Sally\n";

                break;

        default:

                print "I don't know your name!\n";

        }

?>
```

Switch/case statements are frequently used to check all sorts of data, and they take up much less room than equivalent if statements.

There are two important things to note in the PHP switch/case statement code. First, there is no word "case" before "default"that is just how the language works. Second, each of our case actions above end with "break;". This is because once PHP finds a match in its case list, it will execute the action of that match as well as the actions of all matches beneath it \(further down on your screen\). This way of working is taken directly from C, and is generally counterintuitive to how we thinkit is rare that you will want to exclude a break from the end of your cases.

The default case is executed if PHP doesn't find a match in one of the other cases, or if the case before it was executed and didn't end with a break statement.

The keyword "break" means "Get out of the switch/case statement," and has the effect of stopping PHP from executing the actions of all subsequent cases after its match. Without the break, our test script would print out this:

```
Your name is Bob

Your name is Sally

I don't know your name
```



