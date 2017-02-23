# Constants

If you find yourself setting a variable for convenience and never changing it during a script, chances are you should be using a constant. Constants are like variables except that once they are defined, they cannot be undefined or changedthey are constant, as the name suggests. Unlike many other languages, constants are not faster than variables in PHP. The primary advantage to using constants is the fact that they do not have a dollar sign at the front and, therefore, are visibly different from variables. Furthermore, constants are automatically global across your entire script, unlike variables.

To set a constant, use the define\( \) function. It takes two parameters: the first being the name of the constant to set, and the second being the value to set. For example, the following line of code sets the constant SecondsPerDay, then prints it out:

```
define ("SecondsPerDay", 86400);

print SecondsPerDay;
```

Note that it is not $SecondsPerDay or SECONDSPERDAYthe names of constants, like the names of variables, are case-sensitivebut unlike variables, they do not start with a dollar sign. You can change this behavior by passing true as a third parameter to define\( \), which makes the constant case-insensitive:

```
define ("SecondsPerDay", 86400, true);

print SecondsPerDay;

print SECONDSperDAY;
```

There are two helpful functions available for working with constants, and these are defined\( \) and constant\( \). The defined\( \) function is basically the constant equivalent of isset\( \), as it returns true if the constant string you pass to it has been defined. For example:

```
define ("SecondsPerDay", 86400, true);

if (defined("Secondsperday")) {

        // etc

}
```

Note that you should pass the constant name into defined\( \) inside quotes.

Finally, constant\( \) is a function that at first seems redundant, but is important nonetheless: it returns the value of a constant. While you can get the value of a constant just by using ite.g., "print MY\_CONSTANT;"how would you accomplish that if you didn't know the constant's name? If you were using a variable, you could use a variable variable, but this is not possible with constantshence the constant\( \) function.

```
define("SecondsPerDay", 86400, true);

$somevar = "Secondsperday";

print constant($somevar);
```

## Pre-set constants

There are a number of constants automatically set by PHP in order to save you having to recalculate complicated values each time in your script, but PHP also provides other helpful information. For example, PHP always sets the \_ \_FILE\_ \_, \_ \_LINE\_ \_, \_ \_FUNCTION\_ \_, \_ \_CLASS\_ \_, and \_ \_METHOD\_ \_ constants for younote that there are double underscores on either side to make it unlikely you will use these names for your own constants.

\_ \_FILE\_ \_

The name of the script that's running. Note that this reports the file that contains the current line of code, so this will report the name of an include file if applicable.

\_ \_LINE\_ \_

The line number PHP is executing. Like \_ \_FILE\_ \_, this holds the line number of the current line of code, which may be in an include file if applicable.

\_ \_FUNCTION\_ \_

The name of the function PHP is currently inside

\_ \_CLASS\_ \_

The name of the class of the object being used

\_ \_METHOD\_ \_

The name of the class function PHP is currently inside

Using these special constants, it is very easy to output complex error reports or other debugging information.

PHP defines numerous constants for use in its functions and extensionsa great many of these are outlined elsewhere in this book, and they help you remember values. For example, if you want to know the value of the mathematical figure pi, use M\_PI, which is much easier than remembering 3.141592653. To extract \(or "export"\) variables from an array using extract\( \) and always using a prefix, use EXtr\_PREFIX\_ALL. Again, that's much easier to remember than a numerical value such as 3, but does the same thing.

There are some generic coding constants that you might find useful, such as PHP\_EOL to grab the newline character for the current OS, PHP\_OS to grab the name of the OS, PHP\_VERSION to get the version number of the engine, and DEFAULT\_INCLUDE\_PATH to see where PHP will include files from, if it can't find them in the local directory.

There are predefined constants to do all sorts of things inside your code, and there is not room to cover them all here. For a comprehensive and up-to-date list, check the PHP manual at [http://www.php.net/manual/en/reserved.constants.php](http://www.php.net/manual/en/reserved.constants.php).

Mathematical Constants

There are several values in mathematics that are used in math-related scripts but take some time to calculate, so, to save time, PHP defines them as constants available to you in every script. For example, if you want to use the value of pi, you can use the preset constant value M\_PI.

So, to calculate the area a of a circle based upon its radius r, the formula is a = pi \* r2. Using PHP, we can write this as:

```
$area = M_PI * ($radius * $radius);

// or...

$area = M_PI * pow($radius, 2);
```

## Mathematical constants

M\_PI

3.14159265358979323846

pi

M\_PI\_2

1.57079632679489661923

pi/2

M\_PI\_4

0.78539816339744830962

pi/4

M\_1\_PI

0.31830988618379067154

1/pi

M\_2\_PI

0.63661977236758134308

2/pi

M\_SQRTPI

1.77245385090551602729

sqrt\(M\_PI\)

M\_2\_SQRTPI

1.12837916709551257390

2/sqrt\(M\_PI\)

M\_SQRT2

1.41421356237309504880

sqrt\(2\)

M\_SQRT3

1.73205080756887729352

sqrt\(3\)

M\_SQRT1\_2

0.70710678118654752440

1/sqrt\(2\)

