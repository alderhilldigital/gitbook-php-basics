# Integers

Most people specify their numbers using base 10, meaning that the digits 0 to 9 are used. However, you may also specify them in hexadecimal \(base 16\) or octal \(base 8\). The octal number system only uses the digits 0 to 7. For example, the decimal number 3291 represented in octal is 6333. Represented in hexadecimal, which uses 0 to 9, then A, B, C, D, E, and F, the same number is CDB.



Decimal, octal, and hexadecimal all share the digits 0 to 7, which means that a number like 6333 would look the same in any of the bases. Unless you are specific about which base you want, PHP assumes decimal. For example:



    $octalnum = 6333;



PHP interprets that as 6333 in decimal, which would evaluate to 14,275 in octal. To specify that a number is written in octal and not decimal, you must precede it with a 0 \(zero\). So, to say that you mean $octalnum to be set to octal 6333 \(decimal 3291\), you would use this code:



    $octalnum = 06333;

    print $octalnum;



That script outputs 3291, as PHP always works with decimal internally, and converts octal 06333 to decimal 3291 when $octalnum is set. Because a leading zero causes numbers to be interpreted in octal, you should not try to align numbers on different lines by using leading zeroes unless you specifically want them in octal!



To specify a number in hexadecimal, precede it with 0x. To assign the number 68, you would use this:



    $hexnum = 0x44;

    print $hexnum;



Again, the value is printed out in standard decimal. Octal notation is very rarely used in PHPif you are on Unix, you may have to use it to specify file access permissions, but that's generally the only use. Hexadecimal notation \("hex"\) is more common, mostly because many hashing algorithms return text using hexadecimal characters, and also because HTML's color codes are written in hex.





