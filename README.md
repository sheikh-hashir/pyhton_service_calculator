# Python Service Calculator

This service is a Python calculator that runs on port 54153 by default. You can change the port number by editing line 4 of `my_calculator.py`.

## Getting Started

1. **Start the Service**: 
   When you run the service, it will prompt a message indicating that the server is listening on port 54153. Following this, it will display instructions on how to use the service.

2. **Connecting to the Service**:
   Open another terminal and type:
`nc -u 54153`

The `-u` flag is used because the service runs on UDP.

3. **Using the Service**:
- Enter two numbers, one on each line.
- Enter an operator to specify the operation you want to perform.

## Valid Operators

The following operators are valid:
`+, -, *, /, %, ^, =, <, >`


On the 4th line, the result will be displayed.

## Functionality Details

- **Operator Handling**:
  - `payload3` is a variable that stores the operator.
  - The code checks which operation the user wants to perform by comparing `payload3`.

- **Special Cases**:
  - **Division by Zero**:
    - If a user tries to divide by zero, the code will prompt the user that "Division by zero is not possible" and will ask for a non-zero number in a while loop.
  - **Modulus by Zero**:
    - Similarly, if a user tries to find the modulus with zero as the second number, the user will be prompted to enter a non-zero number until a valid input is given.

- **Invalid Operator**:
  - In case of an invalid operator, the program will prompt a message and then run again.

This entire process works in a `while True` loop, continuously asking for inputs until the user presses `Ctrl + C` to terminate the program.

## Technical Details

- **Data Handling**:
  - The input from the client is a string, so the code first converts the string into a float, performs the operation, and then converts the result back into a string.
  
- **Communication**:
  - The converted string is sent to the client on the client address, which was obtained from the `recvfrom(1024)` function.
  - The `sendto()` function is used to send the result back to the client. This function accepts two arguments: the result string and the client address.
