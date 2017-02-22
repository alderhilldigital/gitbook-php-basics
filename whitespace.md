Spaces, tabs, and blank lines in between statements have no effect on how the code is executed. To PHP, this next script is treated like any other, regardless of the fact that some statements are on the same line, and others are separated by several line breaks:

```
<?php

        $name = "Paul"; print "Your name is $name\n";

        $name2 = $name; $age = 20;



        print "Your name is $name2, and your age is $age\n";

        print 'Goodbye, $name!\n';

?>
```

You should use whitespace to separate your code into clear blocks, so that its meaning can be understood by visually inspecting the layout.

