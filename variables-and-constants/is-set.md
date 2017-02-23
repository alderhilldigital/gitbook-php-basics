# Is Set?



Although most functions are covered in Chapter 7, you need to know the isset\( \) function \(literally, "is a variable set?"\) to make the most of this chapter. To use the function, send it a variable as the only parameter, and it will return true or false depending on whether the variable has a value assigned to it. For example:



    $foo = 1;

    if \(isset\($foo\)\) {

            echo "Foo is set\n";

    } else {

            echo "Foo is not set\n";

    }



    if \(isset\($bar\)\) {

            echo "Bar is set\n";

    } else {

            echo "Bar is not set\n";

    }



That will output "Foo is set" and "Bar is not set". Usually if you try to access a variable that isn't set, like $bar above, PHP will issue a warning that you are trying to use an unknown variable. This does not happen with isset\( \), which makes it a safe function to use.

