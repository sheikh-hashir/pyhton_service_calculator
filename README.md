It is a pyhton service calculator.

This service runs on 54153 port, you can also change the port number by editing line 4 of my_calulator.py

It will prompt a message that the server is listening on port 54153. 

On the next line it will display the instructions how to use the service.

Open the another terminal and type
"nc -u 54153"
-u command is given as it runs on UDP

You have to write two numbers one on each line, then you will have to enter an operator, which will tell which operation the user likes to perform.

The following operators are valid:

"+, -, *, /, %, ^, =, <, >"

On the 4th line the result will be displayed.

payload3 is a variable which stores the operator, it is then campared to check which operation user likes to perform.

If a user wishes to perform division and enters 0 as denominator, the code will prompt user that "Division by zero is not possible" and will ask the user to enter a non zero number in a while loop.

Same is the case when a user tries to find modulus and enters 2nd number 0 so the user will be prompted to enter again until he enters a non zero number.

In case of an invalid operator the program will prompt a message and then run again.

This whole works in a while true loop and will ask for the inputs until the user press ctrl + c.

As the input from client in string so the code will first convert the string into float, perfrom the operation and then convert the result back into string.

This converted string is sent to client on the client address which was achieved from recvfrom(1024) built in python function by python sendto() function.
This function accepts 2 arguments, first is the string and the second is the client address.

