# Strings

You can use {x} notation with strings to read or write individual characters. For example:

```
$mystr = "Jello, world?";

$mystr{0} = "H";

$mystr{12} = "!";

print $mystr;
```

Starting off with a string that doesn't make much sense, we change the first character \(position 0\) to H, then the twelfth character to an exclamation mark, forming "Hello, world!". As you can see, the first character in a string is numbered 0. That is, a string of length 13, as above, will have its last character at position 12.

# Escape Sequences

Escape sequences, the combination of the escape character \ and a letter, are used to signify that the character after the escape character has a special meaning. If you wanted to have the string "And then he said, "That is amazing!", which was true," you would need escape characters because you have double quotes inside double quotes. The valid escape sequences in PHP are shown here:

\"     Print the next character as a double quote rather than treating it as a string terminator

\'     Print the next character as a single quote rather than treating it as a string terminator

\n    Print a new line character

\t     Print a tab character

\r     Print a carriage return \(used primarily on Windows\)

$    Print the next character as a dollar rather than treating it as part of a variable name

\    Print the next character as a backslash rather than treating it as an escape character

Here is a code example of these escape sequences in action:

```
<?php

        $MyString = "This is an \"escaped\" string";

        $MySingleString = 'This \'will\' work';

        $MyNonVariable = "I have \$zilch in my pocket";

        $MyNewline = "This ends with a line return\n";

        $MyFile = "c:\\windows\\system32\\myfile.txt";

?>
```



