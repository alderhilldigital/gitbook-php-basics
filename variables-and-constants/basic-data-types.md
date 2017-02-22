# Basic Data Types

Variables in PHP can be of type integer \(a whole number\), floating-point \(usually called "float"; a fractional number\), string \(a set of characters\), array \(a group of data\), object \(a complex mix of data and functionality\), or a resource \(any external information, such as an image\).



Strings hold characters \(literally: a string of characters\) such as "a," "abc," "Jack and Jill went up the hill to fetch a pail of water," etc. Strings can be as short or as long as you wantthere's no limit to size. PHP considers strings to be case-sensitive \(i.e., Foo and FOO are different\), which means that some string functions have case-insensitive equivalents.

Integers hold whole numbers, either positive or negative, such as 1, -20, 55028932, etc. There is a maximum limit to the size of integersany numbers lower than -2147483647 and any numbers higher than 2147483647 are automatically converted to floats, which can hold a much larger range of values.

Floats hold fractional numbers as well as very large integer numbers, such as 4.2, 1.00000001, and 2147483647000.

Booleans hold either true or false. Behind the scenes, booleans are, in fact, just integersPHP considers the number 0 to be false, and everything else to be true.

Arrays are a special variable type in that they hold multiple values like a container, and can even hold arrays of arrays \(known as multidimensional arrays\).



