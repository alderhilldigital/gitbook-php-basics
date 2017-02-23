# Superglobals

Variables that come into PHP arrive inside one of several special arrays known collectively as the superglobals , so named because they are available throughout your script, even inside objects and other arrays. Superglobals include form data sent from your visitor, cookie data, session information, local server information, and more, making them good to keep around. 

There are nine superglobal arrays available for use, categorized by type of variable.

$\_GET

Contains all variables sent via a HTTP GET request. For example, a URL of myfile.php?name=Paul would load myfile.php and give you $\_GET\["name"\] with the value "Paul". 



$\_POST

Contains all variables sent via a HTTP POST request. 



$\_FILES

Contains all variables sent via a HTTP POST file upload. 



$\_COOKIE

Contains all variables sent via HTTP cookies.



$\_REQUEST

Contains all variables sent via HTTP GET, HTTP POST, and HTTP cookies. This is basically the equivalent of combining $\_GET, $\_POST, and $\_COOKIE, and is less dangerous than using $GLOBALS. However, as it does contain all variables from untrusted sources \(that is, your visitors\), it is best avoided. 



$\_SESSION

Contains all variables stored in a user's session \(server-side data store\).



$\_SERVER

Contains all variables set by the web server you are using, or other sources that directly relate to the execution of your script.



$\_ENV

Contains all environment variables set by your system or shell for the script.



$GLOBALS

An array containing all global variables in your script, including other superglobals. $GLOBALS has been available since PHP 3, and its operation has not changed.





