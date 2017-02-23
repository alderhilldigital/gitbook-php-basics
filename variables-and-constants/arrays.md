# Arrays

To model our surroundings accurately in a programming environment, we need to recognize that some types of data naturally group together. Colors, for example, naturally clump together into one group. Rather than having hundreds of separate variablesone for each colorit makes more sense to have one variable that holds a list, or array, of colors.

First Steps

PHP has built-in support for arrays of data, and you can create them using the array\( \) function or using a special operator, \[ \].

There are two things you need to understand before continuing:

An array is a normal PHP variable, but it works like a containeryou can put other variables inside it.

Each variable inside an array is called an element. Each element has a key and a value, which can be any other variable.

Here is a basic example:

```
$myarray = array("Apples", "Oranges", "Pears");

$size = count($myarray);

print_r($myarray);
```

On the first line, we see the most basic way to create an array, the array\( \) function. This takes a series of variables or values as its parameters \(you can pass no parameters to get an empty array, or as many as you want\), and returns an array containing those variables. In that example, $myarray contains three elements . Line two contains a new function, count\( \), that returns the number of elements existing in the array passed to it.

Line three contains another new function, print\_r\( \). This takes just one parameter, but it outputs detailed information about a variable, such as its type, length, and contents. In the case of arrays, print\_r\( \) iteratively outputs all elements inside the arrayit's a good way to see how arrays work.

Here is the output of print\_r\( \) from the above code:

```
Array

(

[0] => Apples

[1] => Oranges

[2] => Pears

)
```

There are our three valuesApples is at index 0 in the array \(signified by \[0\]=&gt;\), Oranges is at index 1 in the array, and Pears is at index 2 in the array. If you are running your scripts through a web browser as opposed to from the command line, you may find it helpful to put a HTML &lt;pre&gt; tag before your print\_r\( \) calls, as this will format them for easier reading.

Using the proper array terminology defined earlier, the 0, 1, and 2 indices are the keys of each element, the Apples, Oranges, and Pears are the values of each element. The key and the value together are the elements themselves.

Note that you can provide a second parameter to print\_r\( \), which, if set to true, will make print\_r\( \) pass its output back as its return value, and not print anything out. To achieve the same output using this method, we would need to alter the script to this:

```
$myarray = array("Apples", "Oranges", "Pears");

$size = count($myarray);

$output = print_r($myarray, true);

print $output;
```

You can store whatever you like as values in an array, and you can also mix values. For example: array\("Foo", 1, 9.995, "bar", $somevar\). You can also put arrays inside arrays, but we will be getting to that later.

There is a similar function to print\_r\( \), which is var\_dump\( \). It does largely the same thing, but a\) prints out sizes of variables, b\) does not print out nonpublic data in objects, and c\) does not have the option to pass a second parameter to return its output. For example, altering the first script to use var\_dump\( \) rather than print\_r\( \) would give the following output:

```
array(3) {

        [0] => string(6) "Apples"

        [1] => string(7) "Oranges"

        [2] => string(5) "Pears"

}
```

In there, you can see var\_dump\( \) has told us that the array has three values, and also prints out the lengths of each of the strings. For teaching purposes, var\_dump\( \) is better, as it shows the variable sizes; however, you will probably want to use print\_r\( \) in your own work.

Finally, there is the function var\_export\( \), which is similar to both var\_dump\( \) and print\_r\( \). The difference with var\_export\( \) is that it prints out variable information in a style that can be used as PHP code. For example, if we had used var\_export\( \) instead of print\_r\( \) in the test script, it would have output the following:

```
array(

        0 => 'Apples',

        1 => 'Oranges',

        2 => 'Pears',

)
```

You can copy and paste that information directly into your own scripts, like this:

```
$foo = array(

0 => 'Apples',

1 => 'Oranges',

2 => 'Pears',

);
```

# Associative Arrays

As well as choosing individual values, you can also choose your keys. In the fruits code above, we just specify values, and so we get an integer-indexed array; but we could have specified keys along with them, like this:

```
$myarray = array("a"=>"Apples", "b"=>"Oranges", "c"=>"Pears");

var_dump($myarray);
```

This time, var\_dump\( \) will output the following:

```
array(3) {

        ["a"] => string(6) "Apples"

        ["b"] => string(7) "Oranges"

        ["c"] => string(5) "Pears"

}
```

As expected, our 0, 1, and 2 element keys have been replaced with a, b, and c, but we could equally have used Foo, Bar, and Baz, or even variables or other arrays to act as the keys. Specifying your own keys produces what is called an associative array \(also known as a hash\)you associate a specific key with a specific value.

The one exception here is floating-point numbers, which make poor choices for array indexes. The problem lies in the fact that PHP converts them to integers before they are used, which essentially rounds them down. So, the following code will create an array with just one element:

```
$myarr = array(1.5=>"foo", 1.6=>"bar");
```

That will round both 1.5 and 1.6 down to 1, first storing "foo" index 1, then overwriting it with bar. If you really want to use floating-point numbers as your keys, pass them in as strings, like this:

```
$myarr = array("1.5"=>"foo", "1.6"=>"bar");

var_dump($array);
```

That should output the following:

```
array(2) {

        ["1.5"] => string(3) "foo"

        ["1.6"] => string(3) "bar"

}
```

This time the floating-point numbers have not been rounded down or converted at all, because PHP is using them as strings. The same solution applies to reading values out from an associative array with floating-point keysyou must always specify the key as a string.

# The Array Operator

You can also create and manage arrays using square brackets \[ \], which means "add to array" \(earning it the name "the array operator "\). Using this, you can both create arrays and add to the end of existing arrays, so this method is generally more popularyou will generally only find the array\( \) function being used when several values are being put inside the array, as it will fit on one line. Here are some examples of the array operator in action:

```
$array[] = "Foo";

$array[] = "Bar";

$array[] = "Baz";

var_dump($array);
```

That should work in the same way as using the array\( \) function, except it is more flexible because we can add to the array whenever we want to. When it comes to working with non-default indices, we can just place our key inside the square brackets, like this:

```
$array["a"] = "Foo";

$array["b"] = "Bar";

$array["c"] = "Baz";

var_dump($array);
```

# Returning Arrays from Functions

You can return one and only one value from your user functions, but you are able to make that single value an array, thereby allowing you to return many values as one:

```
function dofoo() {

        $array["a"] = "Foo";

        $array["b"] = "Bar";

        $array["c"] = "Baz";

        return $array;

}



$foo = dofoo();
```

Without returning an array, the most common way to pass data back to the calling script is by accepting parameters by reference and changing them inside the function. Passing arrays by reference like this is generally preferred, as it is less of a hack and also frees up your return value for a boolean to check whether the function was successful. For example:

```
function load_member_data($ID, &$member) {

        // this would connect to a database and load the data,

        // but for space reasons this is done by hand!

        $member["Name"] = "Bob";

        return true;

}



$ID = 22901221079;



$result = load_member_data($ID, $member);

// pass $member in for data storage, but get a return value too



if ($result) {

        print "Member {$member["Name"]} loaded successfully.\n";

} else {

        print "Failed to load member #$ID.\n";

}
```

One additional way to write the same thing is just to rely on the fact that an empty array, if typed as a boolean, is considered to be false, whereas an array with values is considered to be TRue. While that works, it is poor technique.

# Array-Specific Functions

There are quite a few array functions, and you need not learn them allyour best bet is to give them all a try so that you at least know how they work. Then when you need them, you can look up their workings here or online.

**array\_diff\( \)**

```
array_diff ( array arr1, array arr2 [, array ...] )
```

The array\_diff\( \) function returns a new array containing all the values of array $arr1 that do not exist in array $arr2.

```
$toppings1 = array("Pepperoni", "Cheese", "Anchovies", "Tomatoes");

$toppings2 = array("Ham", "Cheese", "Peppers");

$diff_toppings = array_diff($toppings1, $toppings2);



var_dump($diff_toppings\);

// prints: array(3) { [0]=> string(9) "Pepperoni" [2]=>

// string(9) "Anchovies" [3]=> string(8) "Tomatoes" }
```

You can diff several arrays simultaneously by providing more parameters to the function. In this situation, the function will return an array of values in the first array that do not appear in the second and subsequent arrays. For example:

```
$arr1_unique = array_merge\($arr1, $arr2, $arr3, $arr4);
```

**array\_filter\( \)**

```
array_filter ( array arr [, function callback] )
```

The array\_filter\( \) allows you to filter elements through a function you specify. If the function returns true, the item makes it into the array that is returned; otherwise, it does not. For example:

```
function endswithy($value) {

        return (substr($value, -1) =  = 'y');

}



$people = array("Johnny", "Timmy", "Bobby", "Sam", "Tammy", "Joe");

$withy = array_filter($people, "endswithy");

var_dump($withy);

// contains "Johnny", "Timmy", "Bobby", and "Tammy"
```

In this script, we have an array of people, most of whom have a name ending with "y". However, several do not, and we want to have a list of people whose names ends in "y", so array\_filter\( \) is used. The function endswithy\( \) will return true if the last letter of each array value is a "y"; otherwise, it will return false. By passing that as the second parameter to array\_filter\( \), it will be called once for every array element, passing in the value of the element as the parameter to endswithy\( \), where it is checked for a "y" at the end.

**array\_flip\( \)**

```
array_flip ( array arr )
```

The array\_flip\( \) function takes an array as its parameter, and exchanges all the keys in that array with their matching values, returning the new, flipped array. You can see how it works in this script:

```
$capitalcities['England'] = 'London';

$capitalcities['Scotland'] = 'Edinburgh';

$capitalcities['Wales'] = 'Cardiff';

$flippedcities = array_flip($capitalcities);

var_dump($flippedcities\);
```

The output is this:

```
array(3) {

        ["London"] => string(7) "England"

        ["Edinburgh"] => string(8) "Scotland"

        ["Cardiff"] => string(5) "Wales"

}
```

As you can see, London, Edinburgh, and Cardiff are the keys in the array now, with England, Scotland, and Wales as the values.

**array\_intersect\( \)**

```
array_intersect ( array arr1, array arr2 [, array ...] )
```

The array\_intersect\( \) function returns a new array containing all the values of array $arr1 that exist in array $arr2.

```
$toppings1 = array("Pepperoni", "Cheese", "Anchovies", "Tomatoes");

$toppings2 = array("Ham", "Cheese", "Peppers");

$int_toppings = array_intersect($toppings1, $toppings2);



var_dump($int_toppings);

// prints: array(1) { [1]=> string(6) "Cheese" }
```

The array\_intersect\( \) function will try to retain array keys when possible. For example, if you are intersecting two arrays that have no duplicate keys, all the keys will be retained. However, if there are key clashes, array\_intersect\( \) will use the first array to contain it. For example:

```
$arr1 = array("Paul"=>25, "Ildiko"=>38, "Nick"=>27);

$arr2 = array("Ildiko"=>27, "Paul"=>38);



print "\nIntersect:\n";

var_dump(array_intersect($arr1, $arr2));

// Values 27 and 38 clashes, so their keys from $arr1 are used.

// So, output is Ildiko (38), and Nick (27)
```

You can intersect several arrays simultaneously by providing more parameters to the function. For example:

```
$arr1_shared = array_intersect\($arr1, $arr2, $arr3, $arr4);
```

**array\_keys\( \)**

```
array_keys ( array arr [, mixed search [, bool strict]] )
```

The array\_keys\( \) function takes an array as its only parameter, and returns an array of all the keys in that array. For example, if you have an array with user IDs as keys and usernames as values, you could use array\_keys\( \) to generate an array where the values were the user IDs. For example:

```
$users[923] = 'TelRev';

$users[100] = 'Skellington';

$users[1202] = 'CapnBlack';

$userids = array_keys($users);

// $userids contains the values 923, 100, and 1202
```

There are two other parameters that can be passed to array\_keys\( \): the value to match and a flag indicating whether to perform strict matching. These two allow you to filter your array keysif you specify TelRev, then the only keys that array\_keys\( \) will return are the ones that have the value TelRev. By default, this is done by checking each key's value with the = = operator \(is equal to\); however, if you specify 1 as the third parameter, the check will be done with = = = \(is identical to\).

```
$users[923] = 'TelRev';

$users[100] = 'Skellington';

$users[1202] = 'CapnBlack';

$userids = array_keys\($users, "TelRev");

// userids contains only 923
```

**array\_merge\( \)**

```
array_merge ( array arr1 [, array arr2 [, array ...]] )
```

The array\_merge\( \) function combines two or more arrays by renumbering numerical indexes and overwriting string indexes, if there is a clash.

```
$toppings1 = array("Pepperoni", "Cheese", "Anchovies", "Tomatoes");

$toppings2 = array("Ham", "Cheese", "Peppers");

$both_toppings = array_merge($toppings1, $toppings2);



var_dump($both_toppings);

// prints: array(7) { [0]=> string(9) "Pepperoni" [1]=>

// string(6) "Cheese" \[2\]=&gt; string\(9\) "Anchovies" \[3\]=&gt;

// string\(8\) "Tomatoes" \[4\]=&gt; string\(3\) "Ham" \[5\]=&gt;

// string\(6\) "Cheese" \[6\]=&gt; string\(7\) "Peppers" }
```

Section 5.14.  Arrays

The + operator in PHP is overloaded so that you can use it to merge arrays, e.g., $array3 = $array1 + $array2. But if it finds any keys in the second array that clash with the keys in the first array, they will be skipped.

The array\_merge\( \) will try to retain array keys when possible. For example, if you are merging two arrays that have no duplicate keys, all the keys will be retained. However, if there are key clashes, array\_merge\( \) will use the clashing key from the last array that contains it. For example:

```
$arr1 = array\("Paul"=&gt;25, "Ildiko"=&gt;38, "Nick"=&gt;27\);

$arr2 = array\("Ildiko"=&gt;27, "Paul"=&gt;38\);



print "Merge:\n";

var\_dump\(array\_merge\($arr1, $arr2\)\);

// Values 27 and 38 clash, so their keys from $arr2 are used.

// So, output is Paul \(38\), Ildiko \(27\), and Nick \(27\).
```

You can merge several arrays simultaneously by providing more parameters to the function. For example:

```
$sports\_teams = array\_merge\($soccer, $baseball, $basketball, $hockey\);
```

array\_pop\( \)

```
mixed array\_pop \( array &arr \)
```

The array\_pop\( \) function takes an array as its only parameter, and returns the value from the end of the array while also removing it from the array. For example:

```
$names = array\("Timmy", "Bobby", "Sam", "Tammy", "Joe"\);

$firstname = array\_pop\($names\);

// first is Timmy; last is Joe again
```

array\_push\( \)

```
int array\_push \( array &arr, mixed var \[, mixed ...\] \)
```

The array\_push\( \) function takes an array and a new value as its only parameter, and pushes that value onto the end of the array, after all the other elements. This is the opposite of the array\_pop\( \) function:

```
$firstname = "Johnny";

$names = array\("Timmy", "Bobby", "Sam", "Tammy", "Joe"\);

array\_push\($names, $firstname\);

// first is Timmy; last is now Johnny
```

array\_rand\( \)

```
mixed array\_rand \( array arr \[, int amount\] \)
```

The array\_rand\( \) function picks out one or more random values from an array. It takes an array to read from, then returns either one random key or an array of random keys from inside there. The advantage to array\_rand\( \) is that it leaves the original array intact, so you can just use that randomly chosen key to grab the related value from the array.

There is an optional second parameter to array\_rand\( \) that allows you to specify the number of elements you would like returned. These are each chosen randomly from the array, and are not necessarily returned in any particular order. The function also has these attributes:

It returns the keys in your array. If these aren't specified, the default integer indexes are used. To get the value out of the array, look up the value at the key.

If you ask for one random element, or do not specify parameter two, you will get a single randomly chosen variable back.

If you ask for more than one random element, you will receive an array of variables back.

If you ask for more random elements than there are in the array, you will get an error.

If you request more than one random element, it will not return duplicate elements.

If you want to read most or all of the elements from your array in a random order, use a mass randomizer like shuffle\( \), as it is faster.

With that in mind, here's an example of array\_rand\( \) in action:

```
$natural\_born\_killers = array\("lions", "tigers", "bears", "kittens"\);

$two\_killers = array\_rand\($natural\_born\_killers, 2\);
```

array\_shift\( \)

```
mixed array\_shift \( array &arr \)
```

The array\_shift\( \) function takes an array as its only parameter, and returns the value from the front of the array while also removing it from the array. For example:

```
$names = array\("Johnny", "Timmy", "Bobby", "Sam", "Tammy", "Joe"\);

$firstname = array\_shift\($names\); // "Johnny"

var\_dump\($names\);

// Timmy, Bobby, Sam, Tammy, Danny, and Joe
```

array\_unique\( \)

```
array array\_unique \( array arr \)
```

The array\_unique\( \) filters an array so that a value can only appear once. It takes an array as its only parameter, and returns the same array with duplicate values removed. For example:

```
$toppings2 = array\("Peppers", "Ham", "Cheese", "Peppers"\);

$toppings2 = array\_unique\($toppings2\);

// now contains "Peppers", "Ham", and "Cheese"
```

array\_unshift\( \)

```
int array\_unshift \( array &arr, mixed var \[, mixed ...\] \)
```

The array\_unshift\( \) function takes an array and a new value as its only parameter, and pushes that value onto the start of the array, before all the other elements. This is the opposite of the array\_shift\( \) function.

```
$firstname = "Johnny";

$names = array\("Timmy", "Bobby", "Sam", "Tammy", "Joe"\);

array\_unshift\($names, $firstname\);

// first is Johnny, last is Joe
```

array\_values\( \)

```
array array\_values \( array arr \)
```

The array\_values\( \) takes an array as its only parameter, and returns an array of all the values in that array. This might seem pointless, but its usefulness lies in how numerical arrays are indexed. If you use the array operator \[ \] to assign variables to an array, PHP will use 0, 1, 2, etc. as the keys. If you then sort the array using a function such as asort\( \), which keeps the keys intact, the array's keys will be out of order because asort\( \) sorts by value, not by key.

Using the array\_values\( \) function makes PHP create a new array where the indexes are recreated and the values are copied from the old array, essentially making it renumber the array elements. For example:

```
$words = array\("Hello", "World", "Foo", "Bar", "Baz"\);



var\_dump\($words\);

// prints the array out in its original ordering, so

// array\(5\) { \[0\]=&gt; string\(5\) "Hello" \[1\]=&gt; string\(5\)

// "World" \[2\]=&gt; string\(3\) "Foo" \[3\]=&gt; string\(3\) "Bar"

// \[4\]=&gt; string\(3\) "Baz" }



asort\($words\);



var\_dump\($words\);

// ordered by the values, but the keys will be jumbled up, so

// array\(5\) { \[3\]=&gt; string\(3\) "Bar" \[4\]=&gt; string\(3\) "Baz"

// \[2\]=&gt; string\(3\) "Foo" \[0\]=&gt; string\(5\) "Hello"

// \[1\]=&gt; string\(5\) "World" }



var\_dump\(array\_values\($words\)\);

// array\_values\( \) creates a new array, re-ordering the keys. So:

// array\(5\) { \[0\]=&gt; string\(3\) "Bar" \[1\]=&gt; string\(3\) "Baz"

// \[2\]=&gt; string\(3\) "Foo" \[3\]=&gt; string\(5\) "Hello"

// \[4\]=&gt; string\(5\) "World" }
```

You will find array\_values\( \) useful to reorder an array's indexes either because they are jumbled up or because they have holes in them, but you can also use it to convert an associative array with strings as the indexes to a plain numerical array.

arsort\( \)

```
bool arsort \( array &arr \[, int options\] \)
```

The arsort\( \) function takes an array as its only parameter, and reverse sorts it by its values while preserving the keys. This is the opposite of the asort\( \) . For example:

```
$capitalcities\['England'\] = 'London';

$capitalcities\['Wales'\] = 'Cardiff';

$capitalcities\['Scotland'\] = 'Edinburgh';

arsort\($capitalcities\);

// reverse-sorted by value, so London, Edinburgh, Cardiff
```

Note that arsort\( \) works by reference, directly changing the value you pass in. The return value is either true or false, depending on whether the sorting was successful.

By default, the sort functions sort so that 2 comes before 10. You can change this using the second parametersee the ksort\( \) reference for how to do this.

asort\( \)

```
bool arsort \( array &arr \[, int options\] \)
```

The asort\( \) function takes an array as its only parameter, and sorts it by its values while preserving the keys. For example:

```
$capitalcities\['England'\] = 'London';

$capitalcities\['Wales'\] = 'Cardiff';

$capitalcities\['Scotland'\] = 'Edinburgh';

asort\($capitalcities\);

// sorted by value, so Cardiff, Edinburgh, London
```

Note that asort\( \) works by reference, directly changing the value you pass in. The return value is either true or false, depending on whether the sorting was successful.

By default, the sort functions sort so that 2 comes before 10. You can change this using the second parametersee the ksort\( \) reference for how to do this.

explode\( \)

```
array explode \( string separator, string input \[, int limit\] \)
```

The explode\( \) function converts a string into an array using a separator value. For example, the string "head, shoulders, knees, toes" could be converted to an array with the values heads, shoulders, knees, toes by using the separator ",". Note that the separator is a comma followed by a space, otherwise the array values would be heads, shoulders, knees, and toes. For example:

```
$oz = "Lions and Tigers and Bears";

$oz\_array = explode\(" and ", $oz\);

// array contains "Lions", "Tigers", "Bears"
```

To reverse this function, converting an array into a string by inserting a separator between elements, use the implode\( \) function.

extract\( \)

```
int extract \( array arr \[, int options \[, string prefix\]\] \)
```

The extract\( \) function converts elements in an array into variables in their own right, an act commonly called "exporting" in other languages. Extract takes a minimum of one parameter, an array, and returns the number of elements extracted. This is best explained using code:

```
$Wales = "Swansea";

$capitalcities = array\("England"=&gt;"London",

  "Scotland"=&gt;"Edinburgh", "Wales"=&gt;"Cardiff"\);

extract\($capitalcities\);

print $Wales;
```

After calling extract, the England, Scotland, and Wales keys become variables in their own right \($England, $Scotland, and $Wales\), with their values set to London, Edinburgh, and Cardiff, respectively. By default, extract\( \) will overwrite any existing variables, meaning that $Wales's original value of Swansea will be overwritten with Cardiff. The new variables are copies of those in the array, and not references.

This behavior can be altered using the second parameter, and averted using the third parameter. Parameter two takes a special constant value that allows you to decide how values will be treated if there is an existing variable, and parameter three allows you to prefix each extract variable with a special string. The possible values of the second parameter are shown in Table 5-6.

Table 5-6. Possible values for the second parameter to extract\( \)

EXTR\_OVERWRITE

On collision, overwrite the existing variable

EXTR\_SKIP

On collision, do not overwrite the existing variable

EXTR\_PREFIX\_SAME

On collision, prefix the variable name with the prefix specified by parameter three

EXTR\_PREFIX\_ALL

Prefix all variables with the prefix specified by parameter three, whether or not there is a collision

EXTR\_PREFIX\_INVALID

Use the prefix specified by parameter three only when variable names would otherwise be illegal \(e.g. ,"$9"\)

EXTR\_IF\_EXISTS

Set variables only if they already exist

EXTR\_PREFIX\_IF\_EXISTS

Create prefixed variables only if non-prefixed version already exists

EXTR\_REFS

Extract variables as references rather than copies

The last option, EXtr\_REFS, can be used on its own or in combination with others using the bitwise OR operator, \|.

Here are some examples based upon the $capitalcities array from the previous example:

```
$Wales = 'Swansea';

extract\($capitalcities, EXTR\_SKIP\);

// leaves $Wales intact, as it exists already



print $Wales; // "Swansea"

print $Scotland; // "Edinburgh"



extract\($capitalcities, EXTR\_PREFIX\_SAME, "country"\);

// creates variables $country\_Wales, $country\_Scotland, etc



print $Wales; // "Swansea"

print $country\_England; // "London"

// Note that PHP places an underscore

// after the prefix for easier reading

extract\($capitalcities, EXTR\_PREFIX\_ALL, "country"\);

// creates variables with prefixes, overwriting $country\_England, etc



extract\($capitalcities, EXTR\_PREFIX\_ALL \| EXTR\_REFS, "country"\);

// sets $country\_ variables to be references to the array elements



$country\_Scotland = "Stirling";

print\($capitalcities\["Scotland"\]\);

// prints "Stirling", because we changed it by reference
```

implode\( \)

```
string implode \( string separator, array pieces \)
```

The implode\( \) function converts an array into a string by inserting a separator between each element. This is the reverse of the explode\( \) function. For example:

```
$oz = "Lions and Tigers and Bears";

$oz\_array = explode\(" and ", $oz\);

// array contains "Lions", "Tigers", "Bears"



$exclams = implode\("! ", $oz\_array\);

// string contains "Lions! Tigers! Bears!"
```

in\_array\( \)

```
bool in\_array \( mixed needle, array haystack \[, bool strict\] \)
```

The in\_array\( \) function will return TRue if an array contains a specific value; otherwise, it will return false:

```
$needle = "Sam";

$haystack = array\("Johnny", "Timmy", "Bobby", "Sam", "Tammy", "Joe"\);



if \(in\_array\($needle, $haystack\)\) {

        print "$needle is in the array!\n";

} else {

        print "$needle is not in the array\n";

}
```

There is an optional boolean third parameter for in\_array\( \) \(set to false by default\) that defines whether you want to use strict checking or not. If parameter three is set to true, PHP will return true only if the value is in the array and of the same typethat is, if they are identical in the same way as the = = = operator \(three equals signs\).

krsort\( \)

```
bool krsort \( array &arr \[, int options\] \)
```

The krsort\( \) function takes an array as its only parameter, and reverse sorts it by its keys while preserving the values. This is the opposite of the ksort\( \) . For example:

```
$capitalcities\['England'\] = 'London';

$capitalcities\['Wales'\] = 'Cardiff';

$capitalcities\['Scotland'\] = 'Edinburgh';

krsort\($capitalcities\);

// reverse-sorted by key, so Wales, Scotland, then England
```

Note that krsort\( \) works by reference, directly changing the value you pass in. The return value is either TRue or false, depending on whether the sorting was successful.

By default, the sort functions sort so that 2 comes before 10. You can change this using the second parametersee the ksort\( \) reference for how to do this.

ksort\( \)

```
bool ksort \( array &arr \[, int options\] \)
```

The ksort\( \) function takes an array as its only parameter, and sorts it by its keys while preserving the values. For example:

```
$capitalcities\['England'\] = 'London';

$capitalcities\['Wales'\] = 'Cardiff';

$capitalcities\['Scotland'\] = 'Edinburgh';

ksort\($capitalcities\);

// sorted by key, so England, Scotland, then Wales
```

Note that ksort\( \) works by reference, directly changing the value you pass in. The return value is either TRue or false, depending on whether the sorting was successful.

By default, the sort functions sort so that 2 comes before 10. While this might be obvious, consider how a string sort would compare 2 and 10it would work character by character, which means it would compare 2 against 1 and, therefore, put 10 before 2. Sometimes this is the desired behavior, so you can pass a second parameter to the sort functions to specify how you want the values sorted, like this:

```
$array\["1"\] = "someval1";

$array\["2"\] = "someval2";

$array\["3"\] = "someval3";

$array\["10"\] = "someval4";

$array\["100"\] = "someval5";

$array\["20"\] = "someval6";

$array\["200"\] = "someval7";

$array\["30"\] = "someval8";

$array\["300"\] = "someval9";

var\_dump\($array\);

ksort\($array, SORT\_STRING\);

var\_dump\($array\);
```

If you want to force a strictly numeric sort, you can pass SORT\_NUMERIC as the second parameter.

range\( \)

```
array range \( mixed low, mixed high \[, number step\] \)
```

The range\( \) function creates an array of numbers between a low value \(parameter one\) and a high value \(parameter two\). So, to get an array of the sequential numbers between 1 and 40 \(inclusive\), you could use this:

```
$numbers = range\(1,40\);
```

The range\( \) function has a third parameter that allows you specify a step amount in the range. This can either be an integer or a floating-point number. For example:

```
$questions = range\(1, 10, 2\);

// gives 1, 3, 5, 7, 9



$questions = range\(1, 10, 3\)

// gives 1, 4, 7, 10



$questions = range\(10, 100, 10\);

// gives 10, 20, 30, 40, 50, 60, 70, 80, 90, 100



$float = range\(1, 10, 1.2\);

// gives 1, 2.2, 3.4, 4.6, 5.8, 7, 8.2, 9.4
```

Although the step parameter should always be positive, if your low parameter \(parameter one\) is higher than your high parameter \(parameter two\), you get an array counting down, like this:

```
$questions = range\(100, 0, 10\);

// gives 100, 90, 80, 70, 60, 50, 40, 30, 20, 10, 0
```

Finally, you can also use range\( \) to create arrays of characters, like this:

```
$questions = range\("a", "z", 1\);

// gives a, b, c, d, ..., x, y, z



$questions = range\("z", "a", 2\);

// gives z, x, v, t, ..., f, d, b
```

shuffle\( \)

```
bool shuffle \( array &arr \)
```

The shuffle\( \) function takes an array as its parameter, and randomizes the position of the elements in there. It takes its parameter by referencethe return value is either true or false, depending on whether it successfully randomized the array. For example:

```
$natural\_born\_killers = array\("lions", "tigers", "bears", "kittens"\);

shuffle\($natural\_born\_killers\);
```

One major drawback to using shuffle\( \) is that it mangles your array keys. This is unavoidable, sadly.

5.14.6. Multidimensional Arrays

Currently our arrays just hold standard, non-array variables, which makes them one-dimensional. In constrast, a two-dimensional array is where each element holds another array as its value, and each element in the child array holds a non-array variable. This allows us to store arrays within arrays \(and arrays within arrays within arrays, etc.\), and therefore lets us store much more information. Consider this script:

```
$capitalcities\['England'\] = array\("Capital"=&gt;"London", "Population"=&gt;

40000000, "NationalSport"=&gt;"Cricket"\);

$capitalcities\['Wales'\] = array\("Capital"=&gt;"Cardiff", "Population"=&gt;5000000,

"NationalSport"=&gt;"Rugby"\);

$capitalcities\['Scotland'\] = array\("Capital"=&gt;"Edinburgh", "Population"=&gt;

8000000, "NationalSport"=&gt;"Football"\);

var\_dump\($capitalcities\);
```

That creates the $capitalcities array elements as before, but uses an array for each value. Each child array has three elements: Capital, Population, and NationalSport. At the end, there is a var\_dump\( \) call on the parent array, which gives this output:

```
array\(3\) {

        \["England"\]=&gt;

        array\(3\) {

                \["Capital"\]=&gt;

                string\(6\) "London"

                \["Population"\]=&gt;

                int\(40000000\)

                \["NationalSport"\]=&gt;

                string\(7\) "Cricket"

        }

        \["Wales"\]=&gt;

        array\(3\) {

                \["Capital"\]=&gt;

                string\(7\) "Cardiff"

                \["Population"\]=&gt;

                int\(5000000\)

                \["NationalSport"\]=&gt;

                string\(5\) "Rugby"

        }

        \["Scotland"\]=&gt;

        array\(3\) {

                \["Capital"\]=&gt;

                string\(9\) "Edinburgh"

                \["Population"\]=&gt;

                int\(8000000\)

                \["NationalSport"\]=&gt;

                string\(8\) "Football"

        }

}
```

Not only does var\_dump\( \) recurse into child arrays to output their contents too, but it indents all the output according to the array level.

Section 5.14.  Arrays

The count\( \) function has a helpful second parameter that, when set to 1, makes count\( \) perform a recursive count. The difference is that if you pass in a multidimensional array, count\( \) will count all the elements in the first array, then go into the first array element and count all the elements in there, and go into any elements in there, etc. For example, the $capitalcities array above has three elements; if you do not use the second parameter to count\( \), you will get 3 back. However, if you pass in 1 for the second parameter, you will get 12: three for the first-level elements \(England, Wales, Scotland\), and three each for the variables inside those elements \(Capital, Population, NationalSport\).

5.14.7. The Array Cursor

Each array has a "cursor," which you can think of as an arrow pointing to the next array element in line to be operated on. It is the array cursor that allows code like while \(list\($var, $val\) = each\($array\)\) to workeach\( \) moves forward the array cursor of its parameter each time it is called, until it eventually finds itself at the end of the array, and so returns false, ending the loop.

The each\( \) function does not move the array cursor back to the first element when you first call it; it just picks up from where the cursor was. It is in situations like this where you need to set the position of the array cursor forcibly, and the functions reset\( \), end\( \), next\( \), and prev\( \) do just that. They all take just one parameterthe array to work withand return a value from that array.

You use the reset\( \) function to rewind its parameter's cursor to the first element, then return the value of that element, whereas end\( \) will set the array cursor to the last element and return that value. The next\( \) and prev\( \) functions both move the cursor pointer forward or backward one element respectively, returning the value of the element now pointed to. If any of the four functions cannot return a value \(if there are no elements in the array, or if the array cursor has gone past the last element\), they will return false. As such, you can use them all in loops if you want.

For example, this iterates over an array in reverse:

```
$array = array\("Foo", "Bar", "Baz", "Wom", "Bat"\);

print end\($array\);



while\($val = prev\($array\)\) {

        print $val;

}
```

Note that we print the output of end\( \), because it sets the array cursor to point at "Bat", and prev\( \) will shift the array cursor back one to "Wom", meaning that "Bat" would otherwise not be printed out.

5.14.8. Holes in Arrays

Using prev\( \) and next\( \) is more difficult when using arrays that have holes . For example:

```
$array\["a"\] = "Foo";

$array\["b"\] = "";

$array\["c"\] = "Baz";

$array\["d"\] = "Wom";

print end\($array\);



while\($val = prev\($array\)\) {

        print $val;

}
```

You may think that will iterate over an array in reverse, printing out values as it goes; however, the value at key b is empty, which will cause both prev\( \) and next\( \) to think that the end of the array has been reached. So, when they hit b, they will return false, prematurely ending the while loop.

In this situation, it would have been better to reverse the array, then use each\( \) to iterate over it. This will cope fine with empty variables and unknown keys.

5.14.9. Using Arrays in Strings

If you want to print array data inside a string, you need to use braces, { and }, around the variable to tell PHP that you are passing it an array to read from. This next code shows how:

```
$myarray\['foo'\] = "bar";

print "This is from an array: {$myarray\['foo'\]}\n";
```

5.14.10. Saving Arrays

The serialize\( \) function converts an array, given as its only parameter, into a normal string that you can save in a file, a session, and so on. The opposite of serialize\( \) is unserialize\( \) , which takes a serialized string and converts it back to an array.

The two functions urlencode\( \) and urldecode\( \) also work in tandem, and convert their string parameter into a version that is safe to be passed across the web. All characters that aren't letters and numbers get converted into web-safe codes that can be converted back into the original text using urldecode\( \).

Passing arrays across pages is best done using urlencode\( \) and urldecode\( \); however, you should consider using them both on any data you pass across the web, just to ensure there are no incompatible characters in there.

Take a look at this next script:

```
$array\["a"\] = "Foo";

$array\["b"\] = "Bar";

$array\["c"\] = "Baz";



$str = serialize\($array\);

$strenc = urlencode\($str\);

print $str . "\n";

print $strenc . "\n";
```

That will output two lines \(the second of which I've forced to wrap so that it appears properly\):

```
a:4:{s:1:"a";s:3:"Foo";s:1:"b";s:3:"Bar";s:1:"c";s:3:"Baz";s:1:"d";}



a%3A4%3A%7Bs%3A1%3A%22a%22%3Bs%3A3%3A%22Foo%22%3Bs%3A1%3A%22b%22

%3Bs%3A0%3A%22%22%3Bs%3A1%3A%22c%22%3Bs%3A3%3A%22Baz%22%3B%7D
```

The first is the direct, serialized output of our array, and you can see how it works by looking through the text inside there. The second line contains the urlencoded serialized array, and is harder to read \(and web safe\).

Once your array is in text form, you can do with it as you please. To return to the original array, it needs to be urldecode\( \)d, then unserialize\( \)d, like this:

```
$arr = unserialize\(urldecode\($strenc\)\);

var\_dump\($arr\);
```



