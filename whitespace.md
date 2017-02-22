# Code Blocks

PHP makes extensive use of code blocks chunks of PHP code that are separate from the rest of the script. You will notice that PHP uses braces, { and }, to open and close code blocks.

# Whitespace

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

# Opening and closing code islands

There are many ways to open a PHP code island \(to enter PHP parsing mode\), and you are welcome to choose which you prefer. The recommended manner is to use &lt;?php to enter PHP mode, and ?&gt; to leave PHP mode, but you can also use the short tags version, &lt;? and ?&gt;.

The short version has one big advantage and two big disadvantages: you can output information from your script by using a special short tags hack, &lt;?=, like this:

```
<?="Hello, world!" ?>
```

Here is the equivalent, written using the standard open and closing tags:

```
<?php

        print "Hello, world!";

?>
```

As you can see, the short tags version is more compact, if a little harder to read. However, the first downside to the short version is that it clashes with XML \(and therefore XHTML\), which also uses &lt;? to open code blocks. This means that if you try to use XML and short-tagged PHP together, you will encounter problemsthis is the primary reason people recommend using the normal open and close tags. Short tags are always dangerous because they can be disabled in the PHP configuration file, php.ini, which means your scripts may not be portable.

Two other, lesser-used variants exist: &lt;% %&gt;, which opens and closes code blocks in the same way as Microsoft's ASP, and also &lt;script language="php"&gt;&lt;/script&gt;. These two often work better with visual editor programs such as Dreamweaver and FrontPage, but they are not recommended for general use because they need to be enabled to work.

You can switch into and out of PHP mode by using &lt;?php and ?&gt; whenever and as often as you want to.

