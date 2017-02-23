# Floats

Integers are good for whole numbers, but for everything else you will need floating-point numbers, often called real numbers or just floats. These are numbers like 1.1, 1.1111112, -12345678.9123, and even 1.0.



Here are some examples of floating-point arithmetic:



    $a = 1.132324;

    $b = $a + 1;

    $b = $a + 1.0;

    $c = 1.1e15;

    $d = \(0.1+0.7\) \* 10;



Mixing a float with an integer, as in line two, results in another float so that PHP doesn't lose any accuracy. Line four specifies a very large exponent; if you print out the resulting number, you will actually get 1.1E+015 back because the number is so large.



The last example appears to assign the value 8 to $d, but owing to inherent inconsistencies in floating-point numbers, the value will actually be 7.9999999999999991. Usually this is not a problem, because rounding that value even to 10 decimal places gives you 8, but it does mean that you should avoid comparing floating-point numbers if possible.

