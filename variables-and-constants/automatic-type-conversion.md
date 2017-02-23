# Automatic Type Conversion

PHP is loosely typed \(which means that a given variable can change its type as needed\). It will automatically convert one type of variable to another whenever possible. Most data types are freely convertible to most other data types; this code illustrates that point:



    $mystring = "12";

    $myinteger = 20;

    print $mystring + $myinteger;



That script will output 32, despite the fact that one of the variables is a string and the other is an integer. PHP will convert the non-integer operand, $mystring, into an integer, and will find that it is, in fact, an integer inside a string. If PHP converts a string such as "wombat" to an integer, it becomes 0.



Problems with automatic conversion occur when either no meaningful conversion is possible, or when conversion yields unexpected results. For example, calling print on an array makes PHP print out Array; it doesn't automatically convert the array to a string of all its elements. An exception to this is treating an object like a string, and this is covered more deeply in Chapter 8.



Unexpected results occur when PHP converts values and produces unhelpful results. For example, converting from a boolean to a string will produce a 1 if the boolean is set to true, or an empty string if false. Consider this script:



    $bool = true;

    print "Bool is set to $bool\n";

    $bool = false;

    print "Bool is set to $bool\n";



That will output the following:



    Bool is set to 1

    Bool is set to



As you can see, it didn't print a 0 for false. To solve this problem, and others like it, tell PHP how you want the value converted by typecastingforcing the result to be a specific type.



The above script should be rewritten to typecast the boolean to an integer, as this will force boolean true to be 1 and boolean false to be 0. To do this, we place the name of the type we're converting to in parentheses before our variable name, like this:



    $bool = true;

    print "Bool is set to $bool\n";

    $bool = false;

    print "Bool is set to ";

    print \(int\)$bool;



This time the script outputs 1 and 0 as we wanted.



PHP will automatically convert data types as necessaryyou need not worry about it happening. However, you can typecast any type of variable into any other type, like this:



    $mystring = "wombat";

    $myinteger = \(integer\)$mystring



At first, $mystring contains a string. However, we typecast it to be an integer, so PHP will convert it to an integer and place the result into $myinteger. You can typecast as boolean using \(bool\), string using \(string\), and floating-point using \(float\).



Typecasting is most often used to specifically enforce a type to provide extra security or to ensure a set type of data is being used. For example, if your script absolutely requires an integer number, it's a smart move to typecast your variable with \(integer\) so that PHP will convert any other type to integer or do nothing if the type is already integer. Converting a float to an integer will round the number down to the nearest whole number, and is actually faster than using the equivalent rounding function.





