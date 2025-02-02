# Errors and Exception

Error are inevitable during the development process. They provide useful feedback to help developers identify and fix issues in their code. Errors in Python are generally classified into two types: **Syntax Errors** and **Exceptions**. 

## Syntax Errors (Parsing Errors)

**Syntax Error** occurs when Python's parser encounters a line of code that violates the grammar rules of the Python language. These errors prevent the code from being executed because the interpreter cannot understand the malformed structure.

When a syntax error occurs, Python provides the following information:
1. **File Name**: Indicates where the error occurred.
2. **Line Number**: Shows the specific line where the error was detected.
3. **Error Message**: Describes the issue (e.g., `SyntaxError: invalid syntax`).
4. **Visual Cue**: The parser echoes the problematic line, highlighting the potential issue with an arrow (`^^^^^`) pointing to the code segment likely responsible for the error. This error might arise from a missing token preceding the highlighted one.


**Example: Missing Colon in a `while` Loop**

```python
# Incorrect Code
while True print('Hello world')
```

**Error Output:**
```plaintext
File "<stdin>", line 1
while True print('Hello world')
             ^^^^^
SyntaxError: invalid syntax
```

**Explanation**:
- The error occurs because the colon (`:`) is missing at the end of the `while` statement.
- The parser highlights the `print` function, indicating where the code structure becomes invalid.

**Correct Code:**
```python
while True:
    print('Hello world')
```

## Exceptions

Even when Python code is syntactically correct, it can still fail at runtime due to unforeseen issues. These runtime errors are called **exceptions**. Exceptions represent conditions that a program may encounter during execution, such as division by zero, invalid variable usage, or type mismatches. Unlike syntax errors, exceptions are errors in logic or operations that occur during runtime.

- **Definition**: Exceptions are runtime errors detected during the execution of a program. They disrupt the normal flow of a program.
- **Fatality**: While exceptions can cause a program to crash, Python provides mechanisms to handle them gracefully using exception handling.
- **Default Behavior**: When an exception is not handled, Python prints an error message and terminates the program.


---

### Some Common Exceptions

#### 1. ZeroDivisionError

Occurs when attempting to divide by zero.

```python
# Code
10 * (1 / 0)

# Outputs
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
10 * (1/0)
    ~^~
ZeroDivisionError: division by zero
```

- **Cause**: Dividing or performing operations with zero as a divisor.
- **Fix**: Add a check to ensure the divisor is not zero.

**Fixed Code**:
```python
divisor = 0
if divisor != 0:
    print(10 * (1 / divisor))
else:
    print("Division by zero is not allowed.")
```

---

#### 2. NameError

Occurs when attempting to use a variable or name that has not been defined.

```python
# Code
4 + spam * 3

# Output
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
4 + spam * 3
    ^^^^
NameError: name 'spam' is not defined
```

- **Cause**: The variable `spam` is referenced without being assigned a value.
- **Fix**: Ensure all variables are defined before use.

**Fixed Code**:
```python
spam = 2
print(4 + spam * 3)
```

---

#### 3. TypeError

Occurs when an operation is performed on incompatible types.

```python
# Code
'2' + 2
```

**Output**:
```plaintext
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
'2' + 2
~~~~^~~
TypeError: can only concatenate str (not "int") to str
```

- **Cause**: Attempting to add a string (`'2'`) and an integer (`2`), which are incompatible types.
- **Fix**: Convert the data types explicitly to make them compatible.

**Fixed Code**:
```python
print(int('2') + 2)  # Converts '2' to integer before addition
print('2' + str(2))  # Converts 2 to string before concatenation
```

---

### Key Components of an Exception Message

Consider the following example to understand the exception message components.
```plaintext
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
10 * (1/0)
    ~^~
ZeroDivisionError: division by zero
```

1. **Traceback**:
   - Indicates the sequence of calls leading to the error.
   - Shows the file name (`<stdin>`), line number (`line 1`), and the offending line of code.

2. **Highlighted Error**:
   - Points to the specific part of the code where the error occurred (e.g., `~^~` under `1/0`).

3. **Error Type**:
   - Describes the category of the error (`ZeroDivisionError`).
   - The string printed as the exception type is the name of the built-in exception that occurred. This is true for all built-in exceptions, but need not be true for user-defined exceptions (although it is a useful convention). 
   - Standard exception names are built-in identifiers (not reserved keywords).

4. **Error Message**:
   - Provides additional details about the cause (`division by zero`).

---

### Built-In Exception Types

Python has a wide variety of built-in exceptions, such as:
- **ArithmeticError**: For errors in arithmetic operations (e.g., `ZeroDivisionError`, `OverflowError`).
- **IndexError**: Accessing an index outside the valid range of a sequence.
- **KeyError**: Accessing a key that does not exist in a dictionary.
- **ValueError**: When an operation receives an argument of the right type but an inappropriate value.
- **IOError**: For input/output operations that fail.

---

## User Interrupted Exception
Look at the following example, which asks the user for input until a valid integer has been entered, but allows the user to interrupt the program (using **Control-C** or whatever the operating system supports); note that a user-generated interruption is signalled by raising the **KeyboardInterrupt exception**.

```python
while True:
    try:
        x = int(input("Please enter a number: "))
        break
    except ValueError:
        print("Oops! That was no valid number. Try again...")

Please enter a number: asd2
Oops! That was no valid number. Try again...
^C 
KeyboardInterrupt
```

## Handling Exceptions

Exception handling is done using the `try`, `except`, and optionally, the `else` and `finally` blocks.

### Basic Structure of Exception Handling

#### 1. `try` Block:  
You place the code that might raise an exception inside the `try` block. This is the code you want to execute.
#### 2. `except` Block: 
If an exception occurs in the `try` block, the code inside the `except` block is executed. You can specify the type of exception you want to catch (e.g., `ValueError`, `ZeroDivisionError`). At most only `except` handle is executed. 
#### 3. `else` Block: 
The code in the `else` block is executed only if **no exception occurs** in the `try` block.
#### 4. `finally` Block: 
This block is executed no matter what, whether an exception occurred or not. It's often used for cleanup tasks, such as closing files or releasing resources.

---

### Example: Asking User for Input Until a Valid Integer is Entered

The program repeatedly asks for input until the user enters a valid integer. The `try-except` block handles the `ValueError` exception, which occurs if the user enters something other than an integer.

```python
while True:
    try:
        x = int(input("Please enter a number: "))
        break  # Exit the loop if input is valid
    except ValueError:
        print("Oops! That was no valid number. Try again...")
```

---

### Multiple `except` Clauses

You can handle different types of exceptions separately using multiple `except` clauses.

```python
try:
    x = int(input("Please enter a number: "))
    y = 10 / x
except ValueError:
    print("Oops! That was no valid number. Try again...")
except ZeroDivisionError:
    print("Oops! Division by zero is not allowed.")
```

---

### Catching Multiple Exceptions in One Clause

You can catch multiple exceptions in a single `except` clause by specifying them in a tuple.

```python
try:
    x = int(input("Please enter a number: "))
    y = 10 / x
except (ValueError, ZeroDivisionError) as e:
    print(f"An error occurred: {e}")
```

**Explanation**:
- Both `ValueError` and `ZeroDivisionError` are caught in the same `except` block.
- The exception object `e` is used to print the error message.

---

### Catching Specific and General Exceptions

You can catch a specific exception or a general `Exception` that handles multiple exceptions. It is generally good practice to catch specific exceptions to handle different error types more appropriately.

```python
try:
    x = int(input("Please enter a number: "))
    y = 10 / x
except ZeroDivisionError:
    print("Division by zero is not allowed!")
except ValueError:
    print("Invalid input! Please enter an integer.")
except Exception as e:
    print(f"An unexpected error occurred: {e}")
```

**Explanation**:
- `ZeroDivisionError` and `ValueError` are handled with specific messages.
- A general `Exception` handler is used to catch any other unexpected exceptions.

---

### Exception Hierarchy and Inheritance

Exceptions in Python are organized in a hierarchy, with `BaseException` at the top. `Exception` is a subclass of `BaseException`. Exceptions that needs to be handled with `try-catch` inherit from `Exception`, but some exceptions like `SystemExit` (raised by `sys.exit()`) and `KeyboardInterrupt` are directly derived from `BaseException` and are typically used for program termination. 



```python
class B(Exception):
    pass

class C(B):
    pass

class D(C):
    pass

for cls in [B, C, D]:
    try:
        raise cls()
    except D:
        print("D")
    except C:
        print("C")
    except B:
        print("B")
```

**Output**:
```plaintext
D
C
B
```

**Explanation**:
- The exception `D` is caught first because it is the most specific handler. If the order of `except` clauses was reversed, it would print `B` three times because `B` is the base class of both `C` and `D`.
- The hierarchy ensures that the most specific exception type is caught first.

---

### Accessing Exception Arguments

Exceptions can have associated arguments, which provide additional details about the error. You can access these arguments via the **`args` attribute** of the exception instance.

```python
try:
    raise Exception('spam', 'eggs')
except Exception as inst:
    print(type(inst))    # <class 'Exception'>
    print(inst.args)     # ('spam', 'eggs')
    print(inst)          # ('spam', 'eggs')
    x, y = inst.args     # Unpacking arguments
    print('x =', x)      # x = spam
    print('y =', y)      # y = eggs
```

**Explanation**:
- The exception is raised with two arguments, `'spam'` and `'eggs'`.
- The `args` attribute holds these arguments as a tuple.
- You can also use **`__str__()`** to print the exception message directly.

---

### Using the `else` Block

The `else` block runs only if no exception occurs in the `try` block. This is useful when you have code that should only execute after successful execution of the `try` block.

The use of the else clause is better than adding additional code to the try clause because it **avoids accidentally catching an exception that wasn't raised by the code being protected** by the `try … except` statement.

```python
for arg in sys.argv[1:]:
    try:
        f = open(arg, 'r')
    except OSError:
        print('Cannot open', arg)
    else:
        print(arg, 'has', len(f.readlines()), 'lines')
        f.close()
```

**Explanation**:
- If the file is opened successfully without any `OSError`, the `else` block is executed to read the file and print its line count.
- The `else` block ensures that file reading is only attempted if no error occurred during file opening.

---

## Raising Exception


You can manually trigger exceptions using the `raise` statement. This allows you to force a specific exception to occur, either by raising a predefined exception or creating a new instance of an exception class.

---

### Raising a Custom Exception

You can raise an exception directly by specifying the exception type and an optional message. For example:

```python
raise NameError('HiThere')

# Outputs
NameError: HiThere
```

In this case, a `NameError` exception is raised with the message `'HiThere'`.

---

### Raising an Exception Class

Instead of passing an exception instance, you can pass an `Exception` class (a subclass of `BaseException`). When an exception class is passed to `raise`, it is automatically instantiated (created) with no arguments:

```python
raise ValueError

# tha above is shorthand for below: 
raise ValueError()

# Output: 
ValueError
```

---

### Re-Raising an Exception

If you are handling an exception within an `except` block but want to allow it to propagate further, you can re-raise the exception using `raise` without specifying an exception. This is useful when you want to log the exception or perform some actions before passing it on.

```python
try:
    raise NameError('HiThere')
except NameError:
    print('An exception flew by!')
    raise


# Output
An exception flew by!
Traceback (most recent call last):
File "<stdin>", line 2, in <module>
raise NameError('HiThere')
NameError: HiThere
```

In this example:
- The `NameError` exception is caught and handled by the `except` block, which prints a message.
- The `raise` statement then re-raises the same exception, allowing it to propagate further.

---

## Exception Chaining

Exception chaining allows you to propagate exceptions in Python and link multiple exceptions together to provide clearer context. This is done using the `raise` statement with the `from` clause, which helps indicate that an exception was caused by another.

---

### Basic Example of Exception Chaining

When an exception is raised inside an `except` block while handling another exception, the **original exception is automatically attached to the new exception**. This is called exception chaining. For example:

```python
try:
    open("database.sqlite")
except OSError:
    raise RuntimeError("unable to handle error")
```

**Output:**
```plaintext
Traceback (most recent call last):
File "<stdin>", line 2, in <module>
open("database.sqlite")
~~~~^^^^^^^^^^^^^^^^^^^
FileNotFoundError: [Errno 2] No such file or directory: 'database.sqlite'
During handling of the above exception, another exception occurred:
Traceback (most recent call last):
File "<stdin>", line 4, in <module>
raise RuntimeError("unable to handle error")
RuntimeError: unable to handle error
```

In this case:
- A `FileNotFoundError` occurs when trying to open a non-existent file.
- This error is caught by the `except` block and triggers a `RuntimeError`.
- The original exception (`FileNotFoundError`) is attached to the new `RuntimeError`.

---

### Using the `from` Clause to Explicitly Chain Exceptions

You can **explicitly indicate** that an exception is caused by another using the `from` clause for readability:

```python
def func():
    raise ConnectionError

try:
    func()
except ConnectionError as exc:
    raise RuntimeError('Failed to open database') from exc

# Output
Traceback (most recent call last):
File "<stdin>", line 2, in <module>
func()
~~~~^^
File "<stdin>", line 2, in func
ConnectionError
The above exception was the direct cause of the following exception:
Traceback (most recent call last):
File "<stdin>", line 4, in <module>
raise RuntimeError('Failed to open database') from exc
RuntimeError: Failed to open database
```

In this example:
- The `ConnectionError` raised in `func()` triggers a `RuntimeError` in the `except` block.
- The `from exc` clause links the original `ConnectionError` to the new `RuntimeError`, making it clear that the `RuntimeError` was caused by the `ConnectionError`.

---

### Disabling Automatic Exception Chaining

You can also disable automatic exception chaining by using `from None`. This prevents the original exception from being shown in the traceback:

```python
try:
    open('database.sqlite')
except OSError:
    raise RuntimeError from None

# Output
Traceback (most recent call last):
File "<stdin>", line 4, in <module>
raise RuntimeError from None
RuntimeError
```

In this case:
- The original `OSError` is not displayed, and only the `RuntimeError` is shown, without the chaining information.

--- 

## User Defined Exception

In Python, you can define your own exceptions by creating custom exception classes. These classes should typically inherit from the built-in `Exception` class (or its subclasses). User-defined exceptions can be used to signal specific error conditions in a program, allowing for more precise and informative error handling.

---

### Defining a User-defined Exception

To create a custom exception, you define a class that inherits from `Exception`. This class can have additional attributes or methods to provide more information about the exception. This custom exception class is just like any other class, but it is kept simple, only offering a number of attributs that allow information about the error to be extracted by handlers for the exception. 

```python
class MyCustomError(Exception):
    def __init__(self, message, code):
        self.message = message
        self.code = code
        super().__init__(self.message)

try:
    raise MyCustomError("Something went wrong", 500)
except MyCustomError as e:
    print(f"Error: {e.message}, Code: {e.code}")

# Output
Error: Something went wrong, Code: 500
```

In this example:
- `MyCustomError` is a user-defined exception class that inherits from `Exception`.
- The class has an `__init__` method that accepts a `message` and a `code`, which provide additional information about the error.
- The `try` block raises the `MyCustomError` exception with a specific message and code.
- The `except` block catches the exception and prints the error details.

---

### Naming Conventions

While you can choose any name for your custom exception class, it is a common practice to **name exception classes with an "Error" suffix**, similar to Python's built-in exceptions. This helps to make it clear that the class represents an error condition.

For example, you could define:
- `InvalidInputError`
- `DatabaseConnectionError`
- `FileReadError`

---

### Use of User-defined Exceptions

User-defined exceptions are often used in larger programs or libraries where certain error conditions need to be signaled in a way that is specific to the program's domain or functionality. For example, a module interacting with a database might define its own exceptions to signal database-related issues.

---

## Defining Clean-up Actions

The `finally` clause in Python's `try` statement is **used to define clean-up actions** that must be executed under all circumstances. Regardless of whether an exception occurs or not, the `finally` clause ensures that certain actions (like resource cleanup) are always carried out.

---

### How the `finally` Clause Works

1. **Guaranteed Execution:** The code within the `finally` block will always be executed, even if the `try` block raises an exception or if a `return`, `break`, `continue`, or `raise` statement is encountered in the `try` or `except` block.
2. **Exception Handling:** If an exception occurs in the `try` block and is caught in the `except` block, the `finally` block will execute before control moves outside the `try` statement. If no exception is handled, the `finally` block still runs.
3. **Return, Break, Continue:** 
   - If a `return`, `break`, `raise` or `continue` statement is executed in the `try` or `except` block, the `finally` block will execute right before.
   - If a `return` statement is in the `finally` block, it will override any return statement from the `try` block.
   - If the `finally` clause executes a `break`, `continue` or `return` statement, exceptions are **not** re-raised.

???
If an exception occurs during the execution of the `try` clause, it may be handled by an `except` clause. If the exception is not handled, it is re-raised after the `finally` clause has been executed.

- An exception can also occur during the execution of an `except` or `else` clause. In such cases, the exception is re-raised after the `finally` clause has been executed.  
- If the `finally` clause executes a `break`, `continue`, or `return` statement, exceptions are not re-raised.  
- If the `try` statement encounters a `break`, `continue`, or `return` statement, the `finally` clause will execute just before the `break`, `continue`, or `return` statement is executed.  
- If the `finally` clause contains a `return` statement, its return value will take precedence over any return value from the `try` clause.

---

#### Example 1: Basic Use of `finally`
```python
try:
    raise KeyboardInterrupt
finally:
    print('Goodbye, world!')


# Output
Goodbye, world!
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
KeyboardInterrupt
```
- The `finally` block executes before the program terminates, even if an exception (like `KeyboardInterrupt`) is raised.

---

#### Example 2: Handling Exceptions and Cleanup
```python
def divide(x, y):
    try:
        result = x / y
    except ZeroDivisionError:
        print("division by zero!")
    else:
        print("result is", result)
    finally:
        print("executing finally clause")

divide(2, 1)
divide(2, 0)

# Output
result is 2.0
executing finally clause
division by zero!
executing finally clause
```
- The `finally` block runs after the `try` block, regardless of whether an exception was raised or not.

---

#### Example 3: Return Statement in `finally`
```python
def bool_return():
    try:
        return True
    finally:
        return False

print(bool_return())

# Output
False
```
- In this case, the `return False` from the `finally` block **overrides** the `return True` from the `try` block.

---

#### Example 4: Unhandled Exception after `finally`
```python
def divide(x, y):
    try:
        result = x / y
    except ZeroDivisionError:
        print("division by zero!")
    else:
        print("result is", result)
    finally:
        print("executing finally clause")

divide("2", "1")

# Output
executing finally clause
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 3, in divide
TypeError: unsupported operand type(s) for /: 'str' and 'str'
```
- The exception `TypeError` is raised because you cannot divide strings, but the `finally` block still executes before the exception is re-raised.

---

#### Example 5: reraising Exception after `finally`
Wwhen you reraise an error inside an `except` block in Python, the corresponding `finally` block will still execute before the error propagates further. The `finally` block is always executed, regardless of whether an exception was handled or re-raised, making it useful for cleanup actions.


```python
try:
    print("In try block")
    raise ValueError("An error occurred")
except ValueError as e:
    print(f"Caught an error: {e}")
    raise  # Reraises the exception
finally:
    print("In finally block")

# Output
In try block
Caught an error: An error occurred
In finally block
Traceback (most recent call last):
  ...
ValueError: An error occurred
```
---

### Real-World Use Cases of `finally`

In real applications, the `finally` block is often used to ensure that external resources, such as files, network connections, or database connections, **are released properly**, even if an error occurs during their use.

**Example: Resource Cleanup**
```python
try:
    file = open("example.txt", "r")
    data = file.read()
finally:
    file.close()  # Ensures the file is closed even if an error occurs
```

---

### When does `finally` not get executed?

The `finally` clause in Python is almost always executed, but there are rare cases where it might not be executed. These include:

#### 1. Process Termination
If the Python process is forcibly terminated while the `try` or `except` block is still running, the `finally` clause will not execute. Examples include:
- Using `os._exit()` or a similar function to terminate the process.
- A `SIGKILL` signal or equivalent forcefully terminates the Python process.

```python
import os
try:
   print("In try block")
   os._exit(1)  # Forcefully exit
finally:
   print("In finally block")  # This won't execute
```

#### 2. Power Outage or System Crash
If the program is interrupted by a power failure, operating system crash, or other catastrophic events, the `finally` block will not execute.

#### 3. Infinite Loop or Non-terminating Code
If there is an infinite loop or a blocking operation in the `try` or `except` block, the `finally` block may never execute because the program does not progress.

```python
try:
   while True:  # Infinite loop
       pass
finally:
   print("In finally block")  # This won't execute
```

#### 4. Deadlocks
If the code in the `try` block causes a deadlock, the `finally` block will not execute because the program gets stuck.

#### 5. Interpreter Crash
If the Python interpreter itself crashes due to an internal error or a bug, the `finally` clause will not execute.

#### 6. Hardware Interruption
If the program is running in an environment where the hardware malfunctions (e.g., a failing disk or memory issue), the `finally` block might not execute.

---

## Predefined cleanup action

In Python, some objects have predefined clean-up actions, ensuring that resources they manage (like files) are properly released when they are no longer needed, regardless of whether the operation was successful or not. The `with` statement is used to handle such objects efficiently, ensuring they are cleaned up automatically.

---

### Problem with Manual Resource Management

In certain scenarios, when you manually manage resources like files, there is a risk of leaving them open longer than necessary, especially if an exception occurs or the code finishes execution unexpectedly. For example:

**Example: File Handling Without Cleanup**
```python
for line in open("myfile.txt"):
    print(line, end="")
```
**Problem:** The file is left open after the code finishes executing. In simple scripts, this might not cause noticeable issues, but in larger applications, it can result in memory leaks or resource contention.

---

### Using `with` Statement for Automatic Cleanup

The `with` statement ensures that the objects involved are cleaned up immediately after use, making it a more reliable way to manage resources like files.

**Example: File Handling with `with` Statement**
```python
with open("myfile.txt") as f:
    for line in f:
        print(line, end="")
```
**Explanation:** The `with` statement automatically handles the opening and closing of the file. The file is closed as soon as the block of code inside the `with` statement finishes execution, even if an error occurs during the process.

---

### How `with` Works

1. **Context Manager:** The `with` statement works with context managers. A context manager is an object that defines the **`__enter__()` and `__exit__()` methods**, which are responsible for setting up and cleaning up the resource, respectively.
2. **Automatic Cleanup:** When the code within the `with` block completes (successfully or due to an exception), the `__exit__()` method **is automatically called**, which ensures that any cleanup tasks (like closing a file) are executed.

---

### Real-World Use Cases of `with`

**File Handling:** Ensures that files are closed after reading or writing, even if an exception occurs.
```python
with open("data.txt", "r") as file:
   data = file.read()
   # process the data
# No need to manually close the file, it's handled by the 'with' block
```

**Database Connections:** Automatically close database connections after a query is executed.
  
```python
with db_connection.cursor() as cursor:
   cursor.execute("SELECT * FROM users")
   result = cursor.fetchall()
# Connection is automatically closed when the block is done
```

---

## Raising and Handling Multiple Unrelated Exceptions

In some cases, you may need to handle multiple exceptions that occur simultaneously, such as when dealing with parallel tasks in concurrency frameworks or when wanting to continue execution while collecting multiple errors. Python provides a way to raise and handle multiple unrelated exceptions through the `ExceptionGroup` class, introduced in newer versions of Python.

---

### Raising Multiple Unrelated Exceptions with `ExceptionGroup`

The `ExceptionGroup` is a special type of exception that allows multiple unrelated exceptions to be raised together. It takes a list of **exception instances** (only instances and not raw exceptions) and wraps them in a single exception, making it possible to raise them all at once.

**Example: Raising an Exception Group**
```python
def f():
    excs = [OSError('error 1'), SystemError('error 2')]
    raise ExceptionGroup('there were problems', excs)

f()

# Output
+ Exception Group Traceback (most recent call last):
|
File "<stdin>", line 1, in <module>
|
f()
|
~^^
|
File "<stdin>", line 3, in f
|
raise ExceptionGroup('there were problems', excs)
| ExceptionGroup: there were problems (2 sub-exceptions)
+-+---------------- 1 ----------------
| OSError: error 1
+---------------- 2 ----------------
| SystemError: error 2
+------------------------------------
  ```
- **Explanation:** The `ExceptionGroup` contains two sub-exceptions: an `OSError` and a `SystemError`. Both exceptions are raised together under the same exception group.

---

### Handling Multiple Unrelated Exceptions

When catching exceptions from an `ExceptionGroup`, you can use the `except*` clause, which allows you to selectively handle only the exceptions of a specific type from the group. The `except*` clause **processes sub-exceptions of a given type, leaving others to propagate** to other handlers or be reraised.

**Example: Handling Specific Exceptions in an Exception Group**
```python
def f():
    raise ExceptionGroup(
        "group1",
        [
            OSError(1),
            SystemError(2),
            ExceptionGroup(
                "group2",
                [
                    OSError(3),
                    RecursionError(4)
                ]
            )
        ]
    )

try:
    f()
except* OSError as e:
    print("There were OSErrors")
except* SystemError as e:
    print("There were SystemErrors")

### Output
There were OSErrors
There were SystemErrors
+ Exception Group Traceback (most recent call last):
|
File "<stdin>", line 2, in <module>
|
f()
|
~^^
|
File "<stdin>", line 2, in f
|
raise ExceptionGroup(
|
...<12 lines>...
|
)
| ExceptionGroup: group1 (1 sub-exception)
+-+---------------- 1 ----------------
| ExceptionGroup: group2 (1 sub-exception)
+-+---------------- 1 ----------------
| RecursionError: 4
+------------------------------------
```

**Explanation:** In this example, we have an `ExceptionGroup` with a nested exception group. The `except*` clauses catch `OSError` and `SystemError` separately from the group, and the program prints messages indicating the specific errors.

---

### Use Case: Collecting Multiple Errors

You can also use `ExceptionGroup` to collect multiple errors over time, such as in testing scenarios, where multiple tests may fail and you want to raise them all at once.

**Example: Collecting Errors from Multiple Tests**
```python
excs = []
for test in tests:
    try:
        test.run()
    except Exception as e:
        excs.append(e)

if excs:
    raise ExceptionGroup("Test Failures", excs)
```
- **Explanation:** In this example, exceptions raised by individual tests are collected in the `excs` list. After all tests are run, if there are any exceptions, they are raised together in an `ExceptionGroup`.

---

## Enriching Exceptions with Notes

In Python, exceptions can be enhanced by adding extra information after they have been raised and caught. This can be useful for providing additional context about the error, such as where and why it occurred, especially when handling multiple exceptions or when debugging.

Python exceptions have a method called `add_note(note)` which allows you to append a string to the exception's notes list. These notes are included in the standard traceback output, **appearing after the exception message in the order they were added**.

---

### Adding Notes to an Exception

You can add one or more notes to an exception after it is caught using `add_note()`.

```python
try:
    raise TypeError('bad type')
except Exception as e:
    e.add_note('Add some information')
    e.add_note('Add some more information')
    raise


# Output
Traceback (most recent call last):
File "<stdin>", line 2, in <module>
raise TypeError('bad type')
TypeError: bad type
Add some information
Add some more information
```

**Explanation:** After raising a `TypeError`, we add two notes to the exception. These notes are printed along with the exception details in the traceback.

---

### Adding Notes to Multiple Exceptions in an Exception Group

When handling multiple exceptions (for example, in a loop), you can add context to each exception by using `add_note()`. This is particularly useful when raising an `ExceptionGroup` that contains multiple exceptions with additional information.

```python
def f():
    raise OSError('operation failed')

excs = []
for i in range(3):
    try:
        f()
    except Exception as e:
        e.add_note(f'Happened in Iteration {i+1}')
        excs.append(e)

raise ExceptionGroup('We have some problems', excs)

# Output
+ Exception Group Traceback (most recent call last):
|
File "<stdin>", line 1, in <module>
|
raise ExceptionGroup('We have some problems', excs)
| ExceptionGroup: We have some problems (3 sub-exceptions)
+-+---------------- 1 ----------------
| Traceback (most recent call last):
|
File "<stdin>", line 3, in <module>
f()
|
~^^
|
File "<stdin>", line 2, in f
|
raise OSError('operation failed')
| OSError: operation failed
| Happened in Iteration 1
+---------------- 2 ----------------
| Traceback (most recent call last):
|
File "<stdin>", line 3, in <module>
f()
|
~^^
|
File "<stdin>", line 2, in f
|
raise OSError('operation failed')
| OSError: operation failed
| Happened in Iteration 2
+---------------- 3 ----------------
| Traceback (most recent call last):
|
File "<stdin>", line 3, in <module>
f()
|
~^^
|
File "<stdin>", line 2, in f
|
raise OSError('operation failed')
| OSError: operation failed
| Happened in Iteration 3
+------------------------------------
```

**Explanation:** In this example, three `OSError` exceptions are raised inside a loop. Each exception is enriched with a note that indicates the iteration number when the error occurred. These notes are included in the traceback, making it easier to understand the context of each error within the group.

---

