# Debugging Techniques for Common Python Errors

## What is Debugging

Debugging is the process of finding and fixing errors or bugs in the source code of any software. When software does not work as expected, computer programmers study the code to determine why any errors occurred.

## 1. Debugging Condition Errors in an ```if-elif-else``` Statement

```python
temperature = 75

if temperature > 80:
    print("It's hot")
elif temperature > 50:
    print("It's temperate")
else:
    print("It's cold")
```

### Issue:
The code has a missing condition for temperatures between 0 and 50. Consequently, temperatures in that range are unclassified.

### Debugging Solution:
To debug this, run the code and test with different temperatures. You’ll notice the program outputs nothing for temperatures between 0 and 50. Changing the final elif to an else ensures any temperature below 50 defaults to “cold.”


### Correct Code :
```python
temperature = 75

if temperature > 80:
    print("It's hot")
elif temperature > 50:
    print("It's temperate")
else:
    print("It's cold")
```

### Debugging Tip:
When using multiple conditions, test values at every threshold and examine edge cases to ensure each path is covered.


## 2. Debugging a Space Counter in Strings

```python
text = "Hello, world, my name is"
count = 0

for char in text:
    if char == "":
        count += 1

print(count)
```

### Issue:
```char == ""``` looks for an empty string, which is not the same as a space. Thus, ```count``` remains zero.

### Debugging Solution:
Run the code and inspect ```char``` inside the loop. You’ll see each ```char``` is a non-empty string, so ```char == ""``` never evaluates as ```True```. Changing ```char == ""``` to ```char == " "``` counts actual spaces.


### Correct Code :
```python
text = "Hello, world, my name is"
count = 0

for char in text:
    if char == " ":
        count += 1

print(count)

```

### Debugging Tip:
If a condition isn’t triggering as expected, print variables within the loop to verify their values. This helps confirm if conditions are met correctly.


## 3. Debugging Even/Odd Number Checker from 1 to ```n```

```python
print("Give me a number")
n = input()

for num in range(1, n):
    if num % 2 < 0:
        print(num, "is even.")
    else:
        print(num, "is odd.")
```

### Issue:
This code has two bugs. First, ```input()``` returns a string, but ```range()``` needs an integer. Second, ```num % 2 < 0``` is incorrect for even numbers; it should be ```num % 2 == 0```.

### Debugging Solution:
1. Add ```print(type(n))``` to check the type of ```n```, which reveals it’s a string.
2. For even/odd checking, ```print num % 2``` and see if it’s zero for even numbers.


### Correct Code :
```python
print("Give me a number")
n = int(input())

for num in range(1, n):
    if num % 2 == 0:
        print(num, "is even.")
    else:
        print(num, "is odd.")
```

### Debugging Tip:
Use ```print()``` to check data types and variable values. This helps pinpoint incorrect type usage or unexpected results from operations.


## 4. Debugging Factorial Calculation
```python
num = int(input("Enter an integer: "))

if num < -1:
    print("No negative numbers.")
else:
    result = 1
    for i in range(1, num):
        result *= i

    print("Factorial of " + num + "is" + result)
```

### Issue:
This code has multiple errors:

1. ```num < -1``` condition is incorrect for excluding negative values.
2. ```range(1, num)``` excludes num itself.
3. ```print("Factorial of " + num + "is" + result)``` mixes strings and integers, causing a type error.

### Debugging Solution:
1. Test ```num < -1``` and replace it with ```num < 0``` for clarity.
2. Change ```range(1, num)``` to ```range(1, num + 1)``` to include ```num```.
3. Convert ```num``` and ```result``` to strings in the print statement.

### Correct Code: 
```python
num = int(input("Enter an integer: "))

if num < 0:
    print("No negative numbers.")
else:
    result = 1
    for i in range(1, num + 1):
        result *= i

    print("Factorial of " + str(num) + " is " + str(result))
```

### Debugging Tip:
Use ```type()``` to confirm if variable types match expectations, especially when combining strings and integers in output.


## 5. Debugging Password Attempts with a Limit

```python
attempts = 0
correct_password = "secret"

while True:
    password = input("Enter your password: ")
    attempts += 1

    if password == "incorrect_password":
        print("Correct password!")
    else:
        print("Incorrect password")

    if attempts > 3:
        print("Too many attempts")
        break
```

### Issue:
The code incorrectly checks ```password == "incorrect_password"``` instead of ```correct_password```, and the loop doesn’t break after three attempts.

### Debugging Solution:
1. Change ```password == "incorrect_password"``` to ```password == correct_password```.
2. Test if attempts exceeds 3 right after printing “Incorrect password.”

### Correct Code : 
```python
attempts = 0
correct_password = "secret"

while True:
    password = input("Enter your password: ")
    attempts += 1

    if password == correct_password:
        print("Correct password!")
        break
    else:
        print("Incorrect password")

    if attempts >= 3:
        print("Too many attempts")
        break
```

### Debugging Tip:
When working with loops, test both successful and unsuccessful cases to ensure proper control flow, especially when managing breakpoints or limited attempts.


Debugging is a fundamental skill in programming, and learning how to identify common issues improves your code quality and productivity. By running test cases, examining variable values, and checking data types, you can efficiently debug and refine your Python code.