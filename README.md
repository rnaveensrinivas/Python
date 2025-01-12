# Table of Contents
* [Introduction](#Introduction)
* [Whetting Your Appetite](#Whetting-Your-Appetite)
* [Using the Python Interpreter](#Using-the-Python-Interpreter)
* [An Informal Introduction to Python](#An-Informal-Introduction-to-Python)
* [More Control Flow Tools in Pyton](#more-control-flow-tools-in-python)
* [Data Structures](#data-structures)
* [Modules](#Modules)
* [Packages](#packages)
* [Input and Output](#input-and-output)
* [Errors And Exception](#errors-and-exception)
* [Classes](#classes)
* [Brief Tour of the Standard Library](#brief-tour-of-the-standard-library)
* [Virtual Environments and Packages](#virtual-environments-and-packages)
* [Floating-Point Arithmetic: Issues and Limitations](#floating-point-approximation-and-display)

# Introduction

Python is an easy-to-learn, powerful programming language known for its efficient high level data structures, simple object-oriented approach, elegant syntax, dynamic typing, and interpreted nature, making it ideal for scripting and rapid development across platforms.

---

# Whetting Your Appetite

Python is a versatile  programming language that caters to a wide range of tasks, from scripting to GUI applications and game development. Its simplicity, power, and wide applicability make it an excellent choice for programmers of all levels.

---

## Why Python?

### Flexibility Across Use Cases
- Python **bridges the gap** between scripting and full-fledged programming:
  - **Shell Scripting: Perl, Bash**: Limited to file manipulation and text data processing and not suitable for writing large application like GUI development.
  - **Software Engineering: C/C++/Java**: Time-consuming for even a small initial development.
- Python offers the best of both worlds:
  - Simple enough for quick tasks.
  - Powerful enough for large, complex programs.

### Cross-Platform Compatibility
- Available on major operating systems, including:
  - **Windows**
  - **macOS**
  - **Unix/Linux**

---

## Key Features of Python

### 1. Ease of Use
- A real programming language with:
  - Better structure and support for large-scale programs compared to shell scripts or batch files.
  - Extensive error-checking capabilities, reducing runtime bugs.

### 2. High-Level Data Types
- Built-in types like flexible arrays and dictionaries allow:
  - Handling complex operations with concise syntax.
  - Has applications in a broader range of problems compared to Awk or Perl.

### 3. Interpreted Language
- **No Compilation Required**:
  - Saves time during development.
  - No need for compilation and linking.
- **Interactive Interpreter**:
  - Experiment with features and test functions interactively.
  - Ideal for quick throw-away programs or bottom-up development.
  - Doubles as a desk calculator.

### 4. Readable and Compact Code
- Python programs are typically much shorter than C, C++, or Java equivalents due to:
  - **High-Level Syntax**: Complex operations in fewer lines.
  - **Indentation for Grouping**: Eliminates the need for brackets.
  - **No Declarations**: No need for variable or argument declarations.

---

## Extensibility
- Python can be extended with functions and data types which are written in C, C++, or other languages callable from C, For example,
  - Add new built-in functions or modules for:
    - Performance-critical operations.
    - Access to binary-only libraries (e.g., vendor-specific graphics libraries).
- One can also embed the Python interpreter into C applications:
  - Use Python as an extension or command language within custom applications.

---

## Fun Fact
- Python is named after the BBC show *Monty Python's Flying Circus* and has no connection to reptiles.
- References to Monty Python skits in documentation are encouraged, adding a touch of humor and creativity.

---

# Using the Python Interpreter

The Python interpreter is a powerful tool that can be used interactively or for executing scripts. 

## Installing Python
To install Python interpreter follow the below commands: 
```bash
$ sudo apt update
$ sudo apt install python3 -y
$ python3 --version
```

### Optional: Adding an alias
You can also add an alias for `python3` so that you don't have to type the full command. For example, `py` or `python`.  To add alias, 

```bash
$ echo "alias python=python3" >> ~/.bashrc
```

## Locating Python
To find Python on your system, use the `whereis` command in Linux-based environments:
```bash
$ whereis python3
python3: /usr/bin/python3 /usr/lib/python3 /etc/python3 /usr/share/python3 /usr/share/man/man1/python3.1.gz
```
The above command lists the paths where Python is installed, including binaries, libraries, configuration files, and documentation.

---

## Invoking the Interpreter interactively

### Standard Invocation of Interactive Interpreter

The interpreter is typically installed at `/usr/bin/python3`. Add `/usr/bin` to your shell's search path (already added if you installed via command line) to invoke it use:
```bash
$ python3
Python 3.12.3 (main, Nov  6 2024, 18:32:19) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```
When invoked interactively, Python reads and executes commands interactively, similar to a Unix shell. This acts as a handy calculator. 

#### Quitting the Interactive Interpreter
You can exit the Python interpreter using one of the following methods:
- **Control Commands**:
  - `CTRL-Z` Suspends the program. 
    - To get back to the interpreter, `fg job_id_of_python_program`.
  - `CTRL-D` Pressing the shortcut on an **empty command** quits the program. 
    - For example, `>>> var=10 CTRL-D` just beeps and does nothing. 
- **Commands**:
  - `exit()`
  - `quit()`

### Command Line Options
#### Execute Commands Directly:
Use `-c` to execute Python commands inline and qutoe the entire command to avoid shell issues with special characters.
```bash
# Syntax
$ python -c "commands"

# Example
$ python -c "print('Hello, World')"
Hello, World
```

#### Execute Modules: 
Use `-m` to run Python modules as scripts:
```bash
# Syntax
$ python -m module_name [arguments]

# Example
$ cat script.py 
import sys
print(sys.argv)
$ python -m script passing arguments
['/home/usr/Desktop/script.py', '-m', 'script.py', 'passing', 'arguments']
```
**Note**: Don't use the extension `.py` in the module name. 

#### Interactive Mode After Script: 
Use `-i` to enter interactive mode after running a script. 

```bash
# Syntax
$ python -i file

# Example
$ cat script.py
print("Hello, World!")

$ python -i script.py
Hello, World!
>>> # we have enetered interactive mode after executing the script.py
>>>
```
## Running a Script
To run a Python script follow the below syntax: 
```bash
# Syntax
$ python script_name.py

# Example
$ python script.py
print("Hello, World!")
```

## Interactive Mode
When commands are read from ???tty, the interpreter is said to be in interactive mode. 
```bash
$ python3
Python 3.12.3 (main, Nov  6 2024, 18:32:19) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> for i in range(10):
...     print(i, end=" ")
... print()
... 
0 1 2 3 4 5 6 7 8 9 
>>> 
```
* `>>>` is called **primary command**
* `...` is called **secondary command**, they are used 
  * to create multiline code
  * to quit a secondary prompt type in a blank line (leave the secondary prompt all by itself). 
  
**Tip**: To clear the interactive session screen use `CTRL+L`.

## Interactive Editing and History Features in Python
The interpreter's line-editing features include interactive editing, history substitution and code completion **on systems that support the GNU Readline library**.

### Key Features:

#### Line Editing & History Substitution: 
Some Python interpreters support editing of the current input line and history substitution using the GNU Readline library, similar to Korn and Bash shells.

#### Tab Completion: 
- Automatically enabled at interpreter startup.
- Supports variable, module, and attribute name completion.
- Works for dotted expressions (e.g., `string.a`) by evaluating up to the last `.` and suggesting attributes of the resulting object.

???Note that this may execute application-defined code if an object with a __getattr__() method is part of the expression.

#### History Management: 
- Input history is saved to `.python_history` in the user directory.
  - Run the command `less ~/.pythong_history` to view history of Python commands you have executed in the interpreter. 
- History persists across interactive interpreter sessions. But each time you close the interactive sessions all the Python environment information is cleared. 

### Limitations:
- No suggestions for proper indentation on continuation lines.
- Limited use of the interpreter's symbol table for completion.
- No built-in tools for checking or matching parentheses, quotes, etc.

### Enhanced Alternatives:
#### IPython:
- Advanced tab completion, object exploration, and history management.
- Highly customizable and embeddable.
#### bpython:
- Similar features with an enhanced interactive experience.

---

## Argument Passing

Python provides a flexible way to handle command-line arguments passed to a script. These arguments are stored in the `sys.argv` list, which resides in the `sys` module.

---

### Accessing Arguments
The command-line arguments are automatically converted into a list of strings and assigned to the `sys.argv` variable. To access this list, import the `sys` module:
```python
import sys
print(sys.argv)
```

#### Understanding the Arguments 
Let's try to understand the arguments that can be passed to Python.
```bash
$ python --help
usage: python3 [option] ... [-c cmd | -m mod | file | -] [arg] ...
Options (and corresponding environment variables):
-b     : issue warnings about converting bytes/bytearray to str and comparing
         bytes/bytearray with str or bytes with int. (-bb: issue errors)
...
Arguments:
file   : program read from script file
-      : program read from stdin (default; interactive mode if a tty)
arg ...: arguments passed to program in sys.argv[1:]
```

From the above, we understand that in ordered to pass argument, we need to have any one of these (**indicators of input source**) `[-c cmd | -m mod | file | -]` to prefix it. We notice that `-` is the default when just `python` is given to command line. But since it is not passed via command line, it will be accounted as an argument. 

```bash
$ python
Python 3.12.3 (main, Nov  6 2024, 18:32:19) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> sys.argv
['']
>>> 
```

```bash
# not passing any of [-c cmd | -m mod | file | -] leads to error. 
$ python trying to pass command line arguments
python3: can't open file '/home/sri/Documents/Python/trying': [Errno 2] No such file or directory

sri@envy:~/Documents/Python
$ python - trying to pass command line arguments
Python 3.12.3 (main, Nov  6 2024, 18:32:19) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> sys.argv
['-', 'trying', 'to', 'pass', 'command', 'line', 'arguments']
>>> 
```
---

### Structure of `sys.argv`
`sys.argv` will always have a valid length (>=1). `sys.argv[0]` always contains the name of the script or the indicator of the input source.
#### Passing no script or argumetns
If no script or arguments are provided: `sys.argv[0]` is an empty string (`''`).
```bash
$ python
Python 3.12.3 (main, Nov  6 2024, 18:32:19) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> len(sys.argv)
1
>>> sys.argv
['']
>>> 
```
#### Passing just the arguments 
If the script is run with `-` (indicating standard input): `sys.argv[0]` is set to `'-'`.
```bash
$ python - trying to pass command line arguments
Python 3.12.3 (main, Nov  6 2024, 18:32:19) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> len(sys.argv)
7
>>> for arg in sys.argv:
...     print(arg)
... 
-
trying
to
pass
command
line
arguments
>>> 
```
#### Passing Program as String
If using `-c` to execute a command: `sys.argv[0]` is set to `'-c'`.
```bash
$ python -c "import sys; print(sys.argv)"
['-c']
$ python -c "import sys; print(sys.argv)" hello
['-c', 'hello']
$
```
#### Passing a Module
If using `-m` to run a module: `sys.argv[0]` is set to the full name (**absolute path**) of the located module.

```bash
$ cat random_module.py 
import sys
print(f"Arguments are: {sys.argv}")

$ python3 -m random_module
Arguments are: ['/home/sri/Desktop/random_module.py']

$ python -m random_module passing some arguments
Arguments are: ['/home/sri/Desktop/random_module.py', 'passing', 'some', 'arguments']
$ 

```

#### Note
Arguments following `-c` or `-m` are **not consumed** by the Python interpreter itself. These arguments remain in `sys.argv` for the command or module to process directly. This ensures flexibility when passing options to user-defined scripts or modules.

---

## Source Code Encoding

### Default Encoding
Python source files are treated as **UTF-8** by default. This allows characters from most languages to be used in string literals, identifiers, and comments. However, the **standard library uses only ASCII for identifiers** to maintain portability.

### Editor Requirements
**Your editor must**:
1. Recognize the file as UTF-8.
2. Use a font that supports the characters present in the file.

### Declaring a Custom Encoding
To use an encoding other than UTF-8, add a special comment at the beginning of the file:
```python
# -*- coding: encoding -*-
```
- Example for Windows-1252 encoding:
```python
# -*- coding: cp1252 -*-
```

### Custom Encoding and Shebang
If the file starts with a UNIX shebang line (e.g., `#!/usr/bin/env python3`), the encoding declaration should be the **second line**:
```python
#!/usr/bin/python3
# -*- coding: cp1252 -*-
```

---

## Shebang (`#!`) Explained
The shebang line specifies where the interpreter is located inorderd to execute the script. 

### Syntax: 
```
#!/path/to/interpreter

code...
```
### Example - script.py:
```python
#!/usr/bin/python3

print("Hello World")
```
### Purpose:
Enables the script to run directly from the command line without explicitly invoking the interpreter.
```bash
$ ./script.py
```
instead of:
```bash
$ python3 script.py
```
**Note!** You need to have execute permission to run the file. Else you will get error `bash: ./script.py: Permission denied`, when you try to run `./script.py`
```bash
$ cat script.py
#!/usr/bin/python3
print("Hello, World!")
$ chmod +x script.py
$ ./script.py
Hello, World!
```
    
### Shebang Portablility:
The `env` utility (`/usr/bin/env`) is often used for portability. It searches for the interpreter in the system's `PATH`, making the script adaptable across environments.AN INFORMAL INTRODUCTION TO PYTHON


## Summary of Python Interpreter
```
$ sudo apt update
$ sudo apt install python3 -y
$ python3 --version
$ echo "alias python=python3" >> ~/.bashrc
$ whereis python
$ python --help
$ python
^z
^d
exit()
quit()
$ python -c "commands"
$ python -m module_name [arguments]
$ python -i file
$ python - [arguments]
import sys; sys.argv
# -*- coding: encoding -*-
#!/usr/bin/python3
#!/usr/bin/env
```
---

# An Informal Introduction to Python

Python allows for interactive experimentation and scripting with ease.

## Comments in Python

Comments start with `#` and extend to the end of the line. They can appear at the beginning of aline or after code segment (inline comments), but not within string literals. Examples:

```python
# This is a comment
spam = 1  # Inline comment
text = "# This is not a comment because it's inside quotes."
```

## Numbers

Python's interpreter can function as a calculator. Arithmetic operations are straightforward, and parentheses can be used for grouping.

### Basic Arithmetic

```python
>>> 2 + 2
4
>>> 50 - 5*6
20
>>> (50 - 5*6) / 4
5.0
>>> 8 / 5  # Division always returns a float
1.6
```

### Integer and Float Types

- Numbers like `2`, `4`, `20` are of type `int`.
- Numbers with fractional parts like `5.0`, `1.6` are of type `float`.

### Division Variants

- `/` performs division and returns a float.
- `//` performs floor division and discards the fractional part.
- `%` calculates the remainder.

Examples:

```python
>>> 17 / 3
5.666666666666667
>>> 17 // 3
5
>>> 17 % 3
2
# rebuilding 17
>>> 5 * 3 + 2  # floored quotient * divisor + remainder
17
```

### Exponentiation

Use the `**` operator to calculate powers:

```python
>>> 5 ** 2  # 5 squared
25
>>> 2 ** 7  # 2 to the power of 7
128
```

### Operator Precedence

The `**` operator has higher precedence than `-`:
??? get the operator precedence
```python
>>> -3**2
-9
>>> (-3)**2
9
```

### Variable Assignment

The `=` operator assigns values to variables. Variables can then be used in calculations.

```python
>>> width = 20
>>> height = 5 * 9
>>> width * height
900
```

Attempting to use an undefined variable results in an error, **NameError**:

```python
>>> n
Traceback (most recent call last):
NameError: name 'n' is not defined
```

### Mixed-Type Operations

Python converts integers to floating-point numbers when mixed with floats:

```python
>>> 4 * 3.75 - 1
14.0
```

### Special Variable: `_`

The last printed result is stored in the `_` variable, making it useful for continuing calculations:

```python
>>> tax = 12.5 / 100
>>> price = 100.50
>>> price * tax
12.5625
>>> price + _
113.0625
>>> round(_, 2)
113.06
```

**Important**: Avoid explicitly assigning a value to `_`, assignment creates an independent local variable with the same name **masking** the built-in variable.

### Other Number Types

#### `Decimal`:  
The `Decimal` class from the `decimal` module provides precise decimal arithmetic, which is useful for financial and scientific applications. 

```python
>>> from decimal import Decimal
>>> Decimal('0.1') + Decimal('0.2')  # Avoids floating-point precision errors
Decimal('0.3')

>>> Decimal('1.23456789').quantize(Decimal('0.01'))  # Rounds to two decimal places
Decimal('1.23')
```

#### `Fraction`:  
Use the `Fraction` class from the `fractions` module for exact arithmetic with rational numbers.

```python
>>> from fractions import Fraction
>>> Fraction(1, 3) + Fraction(2, 3)
Fraction(1, 1)
```

#### Complex Numbers:  
Python supports complex numbers natively, with `j` or `J` indicating the imaginary part.

```python
>>> 3 + 5j  # Complex number
(3+5j)

>>> (2 + 3j) * (1 - 4j)
(14-5j)
```

## Strings
Python allows for manipulation of text, represented by the `str` type. This includes words, sentences, special characters, or even numerals enclosed in quotes.
Strings in Python can be enclosed in **single quotes** (`'...'`) or **double quotes** (`"..."`) with the same result. 

**There is no character type in Python, character is just string of length one.**

### Examples
```python
# Single quotes
>>> 'spam eggs'
'spam eggs'

# Double quotes
>>> "Hello, World!"
'Hello, World!'

# Strings with numbers
>>> '1975'
'1975'
```

### Quoting Quotes
Use the backslash (`\`) to escape quotes, or use alternating quotes for convenience.

```python
>>> 'doesn\'t'  # Escaping a single quote
"doesn't"

>>> "doesn't"   # Using double quotes
"doesn't"

>>> "\"Yes,\" they said."
'"Yes," they said.'

>>> '"Yes," they said.'
'"Yes," they said.'
```

### `print()` method
In the Python shell, the string definition and output string can look different. 
The print() function produces a more readable output, by omitting the enclosing quotes and by printing escaped and special characters:
```python
>>> s = 'First line.\nSecond line.' # \n means newline
>>> s # without print(), special characters are included in the string
'First line.\nSecond line.'
>>> print(s) # with print(), special characters are interpreted, so \n produces, new line
First line.
Second line.
```

### Special Characters and Raw Strings

Raw strings, denoted by prefixing the string with `r`, treat backslashes (`\`) as literal characters. This prevents special characters like `\n` from being interpreted.

```python
>>> print(r'C:\some\name')
C:\some\name
```

#### A Subtle Limitation
Raw strings **cannot end with an odd number of backslashes** because the final backslash escapes the closing quote.

```python
# This will cause an error
>>> r"C:\some\path\"
SyntaxError: EOL while scanning string literal

# Workaround: Use normal strings with escaping
>>> "C:\\some\\path\\"
'C:\\some\\path\\'
```

### Multi-line Strings
Use triple quotes (`"""..."""` or `'''...'''`) for strings spanning multiple lines. End of lines are automatically included in the string, but it's possible to prevent this by adding a \ at the end of the line. 

```python
>>> print("""\
... Usage: command [OPTIONS]
... -h       Display help
... -o FILE  Output to FILE
... """)
Usage: command [OPTIONS]
-h       Display help
-o FILE  Output to FILE

>>> print('hello \
... boy')
hello boy
```

### String Operations

#### Concatenation and Repetition
Strings can be concatenated using `+` and repeated using `*`.

```python
>>> 'un' + 'happy'
'unhappy'

>>> 'ha' * 3
'hahaha'
```

#### Automatic Concatenation
Adjacent strings separated by a space are automatically concatenated. * Very useful when we want to break long strings. You can also use `\` backslash. 

```python
>>> 'Py' 'thon'  # Adjacent string literals are concatenated
'Python'

# have to enclose the string within paranthesis 
# else text will just get the first quoted string. Think!
>>> text = ('Put several strings within parentheses '
... 'to have them joined together.')
>>> text
'Put several strings within parentheses to have them joined together.'

# An alternative way of doing the above.
>>> text = 'put \
... together'
>>> text
'put together'
```

> Note: This works only for literals. Use `+` for variables or expressions.

```python
>>> prefix = 'Py'
>>> prefix 'thon' # can't concatenate a variable and a string literal
File "<stdin>", line 1
prefix 'thon'
^^^^^^
SyntaxError: invalid syntax
>>> ('un' * 3) 'ium'
File "<stdin>", line 1
('un' * 3) 'ium'
^^^^^
SyntaxError: invalid syntax
```

```python
>>> prefix = 'Py'
>>> prefix + 'thon'
'Python'
```


#### Indexing and Slicing
Strings are indexed starting at `0`. Negative indices count from the end. In negative indexing, `-0` is same as `0`, hence they start from `-1`. Indexing allows you to get a **character**, slicing allows you to get a **substring**.

```python
>>> word = 'Python'
>>> word[0]    # First character
'P'

>>> word[-1]   # Last character
'n'

>>> word[0:2]  # Characters from index 0 (inclusive) to 2 (exclusive)
'Py'

>>> word[2:]   # From index 2 to the end
'thon'

>>> word[:2]   # From the start to index 2 (exclusive)
'Py'
```

Attempting to use an index that is too large will result in an error:
```python
>>> word[42] # the word only has 6 characters
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
IndexError: string index out of range
```

#### Slicing Behavior
- Start is **inclusive**, and end is **exclusive**.
  - It's done so that `s[:i] + s[i:] = s`
- Tip for remembering slicing:
  - One way to remember how slices work is to think of the indices as pointing between characters, with the left edge of the first character numbered 0. 
  - Then the right edge of the last character of a string of n characters has index n, for example:
    ```plaintext
     +---+---+---+---+---+---+
     | P | y | t | h | o | n |
     +---+---+---+---+---+---+
     0   1   2   3   4   5   6
    -6  -5  -4  -3  -2  -1   
    ```
  * The slice from i to j consists of all characters between the edges labeled i and j, repsectively.

- Slices have useful defaults
  - Omitted first index defaults to zero
  - Ommited second index defaults to size of string being sliced.
- For non-negative indices, length of a slice is the difference of indices, if both are within bounds.
- Out-of-range slices are **handled gracefully**:
```python
>>> word[4:42]
'on'

>>> word[42:]
''
```

### Strings are Immutable
Strings in Python cannot be modified. To change a string, create a new one.

```python
>>> word = "Python"
>>> word[0] = 'J'  # Error
Traceback (most recent call last):
TypeError: 'str' object does not support item assignment

>>> 'J' + word[1:]  # Create a new string
'Jython'
```

### String Length
Use `len()` to find the length of a string.

```python
>>> len('supercalifragilisticexpialidocious')
34
```

### Strings as Sequence Types (`textseq`)

Strings are sequences of characters and support many common sequence operations. These include indexing, slicing, concatenation, and more.

#### Indexing and Slicing:
```python
word = "Python"
print(word[0])    # 'P' (first character)
print(word[-1])   # 'n' (last character)
print(word[0:3])  # 'Pyt' (substring from position 0 to 3, exclusive)
```

#### Concatenation and Repetition:
```python
greeting = "Hello, " + "World!"
print(greeting)   # 'Hello, World!'
print("Hi! " * 3) # 'Hi! Hi! Hi!'
```

#### Membership Testing:
```python
print('H' in "Hello")  # True
print('z' not in "Hello")  # True
```

---

### String Methods (`string-methods`)

Python strings come with a rich set of methods for common tasks like case conversion, splitting, joining, and searching.


#### Transformation:
```python
print("hello".upper())       # 'HELLO'
print("WORLD".lower())       # 'world'
print("python".capitalize()) # 'Python'
print("tItLe".title())       # 'Title'
```

#### Searching and Replacing:
```python
text = "hello world"
print(text.find("world"))    # 6 (index where "world" starts)
print(text.replace("world", "Python"))  # 'hello Python'
```

#### Splitting and Joining:
```python
data = "apple,orange,banana"
print(data.split(","))       # ['apple', 'orange', 'banana']
print(", ".join(['apple', 'orange', 'banana']))  # 'apple, orange, banana'
```

---

### Formatted String Literals (`f-strings`)

Introduced in Python 3.6, **f-strings** allow you to **embed expressions directly in string literals** for easy and efficient formatting.

#### Basic Usage:
```python
name = "Alice"
age = 25
print(f"My name is {name} and I am {age} years old.") 
# Output: 'My name is Alice and I am 25 years old.'
```

#### Evaluating Expressions:
```python
print(f"The sum of 5 + 3 is {5 + 3}.") 
# Output: 'The sum of 5 + 3 is 8.'
```

#### Formatting Values for Floating Point Values:
```python
pi = 3.14159
print(f"Pi rounded to 2 decimals: {pi:.2f}") 
# Output: 'Pi rounded to 2 decimals: 3.14'

num = 1000
print(f"{num:2.2}")
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
ValueError: Precision not allowed in integer format specifier
>>> 
```

---

### String Formatting with `str.format()` (`formatstrings`)

The `str.format()` method provides a more powerful way to format strings.


#### Positional and Keyword Arguments:
```python
print("Hello, {}!".format("World")) 
# Output: 'Hello, World!'
print("Name: {name}, Age: {age}".format(name="Alice", age=25)) 
# Output: 'Name: Alice, Age: 25'
```

#### Formatting Numbers:
```python
print("Pi: {:.2f}".format(3.14159))  # Output: 'Pi: 3.14'
print("{:d}".format(42))           , # Output: '42'
```

#### Padding and Alignment:
```python
print("{:<10}".format("left"))   # 'left      '
print("{:>10}".format("right"))  # '     right'
print("{:^10}".format("center")) # '  center  '
```

---

### Old String Formatting (`old-string-formatting`)

Before `str.format()` and f-strings, Python used the `%` operator for string formatting.

#### Basic Substitution:
```python
print("Hello, %s!" % "World") 
# Output: 'Hello, World!'
```

#### Formatting Numbers:
```python
print("Pi: %.2f" % 3.14159)  # Output: 'Pi: 3.14'
print("%d items" % 42)       # Output: '42 items'
```

#### Multiple Substitutions:
```python
print("Name: %s, Age: %d" % ("Alice", 25)) 
# Output: 'Name: Alice, Age: 25'
```

---

### Key Takeaways

- The `str.format()` method and f-strings are preferred for modern string formatting due to their flexibility and clarity.
- The older `%` formatting style is still functional but less versatile compared to newer methods.

## Lists

Lists are **sequential compound data types** that group together values in a specific order. Lists are defined using square brackets `[]`, with items separated by commas. They can contain items of **different types**, though typically, items are of the same type.

```python
squares = [1, 4, 9, 16, 25]
print(squares)  # Output: [1, 4, 9, 16, 25]
```

---

### Indexing and Slicing

Lists, like strings, support **indexing** and **slicing**.

```python
# Indexing
print(squares[0])   # Output: 1
print(squares[-1])  # Output: 25

# Slicing
print(squares[-3:]) # Output: [9, 16, 25]
```

---

### Concatenation and Repetition

Repetition operator in Python is very efficient. 
```python
print(squares + [36, 49, 64, 81, 100]) 
# Output: [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]


print([1]*5)
# Output: [1, 1, 1, 1, 1]
```

---

### Lists are Mutable

Unlike strings, lists are **mutable**, meaning their content can be changed. 
We can add new items to list using `append()` method.

#### Examples:
```python
# Modifying a single element
cubes = [1, 8, 27, 65, 125]
cubes[3] = 64  # Fixing the incorrect value
print(cubes)   # Output: [1, 8, 27, 64, 125]

# Adding new elements
cubes.append(216)  # Adding 6³
cubes.append(7 ** 3)  # Adding 7³
print(cubes)  # Output: [1, 8, 27, 64, 125, 216, 343]
```

---

### List References

Assigning a list to a new variable creates a **reference**, not a copy. Hence, changes made to one variable affect the other.

#### `id()` Method
`id()` gives the memory location referred by the variable. 

```python
rgb = ["Red", "Green", "Blue"]
rgba = rgb
>>> id(rgb) == id(rgba) # they reference the same object
True
rgba.append("Alpha")
print(rgb)  # Output: ["Red", "Green", "Blue", "Alpha"]
```

#### Creating Copy
To create a copy, use slicing or `.copy()` method:
```python
# Using slicing
correct_rgba = rgba[:]
correct_rgba[-1] = "Alpha"
print(correct_rgba)  # Output: ["Red", "Green", "Blue", "Alpha"]
print(rgba)          # Output: ["Red", "Green", "Blue", "Alpha"]

# .copy() method
correct_rgba = rgba.copy()
correct_rgba[-1] = "Alpha"
print(correct_rgba)  # Output: ["Red", "Green", "Blue", "Alpha"]
print(rgba)          # Output: ["Red", "Green", "Blue", "Alpha"]
```

---

### Assignment to Slices

Lists allow replacing, removing, or clearing elements using slice assignments.

```python
letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g']

# Replacing values
letters[2:5] = ['C', 'D', 'E']
print(letters)  # Output: ['a', 'b', 'C', 'D', 'E', 'f', 'g']

# Removing values
letters[2:5] = []
print(letters)  # Output: ['a', 'b', 'f', 'g']

# Clearing the list
letters[:] = []
print(letters)  # Output: []
```

---

### `len()`
Returns the number of items in a list.

```python
letters = ['a', 'b', 'c', 'd']
print(len(letters))  # Output: 4
```
---

### Nesting Lists
Lists can contain other lists, creating a nested structure.

```python
a = ['a', 'b', 'c']
n = [1, 2, 3]
x = [a, n]

print(x)        # Output: [['a', 'b', 'c'], [1, 2, 3]]
print(x[0])     # Output: ['a', 'b', 'c']
print(x[0][1])  # Output: 'b'
```
---

## Types of Error

### NameError

```python
>>> n
Traceback (most recent call last):
NameError: name 'n' is not defined
```

### Syntax Error

```python
>>> prefix = 'Py'
>>> prefix 'thon' # can't concatenate a variable and a string literal
File "<stdin>", line 1
prefix 'thon'
^^^^^^
SyntaxError: invalid syntax
>>> ('un' * 3) 'ium'
File "<stdin>", line 1
('un' * 3) 'ium'
^^^^^
SyntaxError: invalid syntax
```

### Index Error

```python
>>> word[42] # the word only has 6 characters
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
IndexError: string index out of range
```

### Type Error

```python
>>> word[0] = 'J'  # Error
Traceback (most recent call last):
TypeError: 'str' object does not support item assignment
```

## Other Programming features demonstrated using Fibonacci Series

The Fibonacci sequence can be generated using the following code:
```python
# Fibonacci series:
# The sum of two elements defines the next
a, b = 0, 1
while a < 10:
    print(a, sep=", ")
    a, b = b, a + b

# Outputs: 0, 1, 1, 2, 3, 5, 8
```

---

### Key Features and Concepts

#### Multiple Assignment
Python allows simultaneous assignment of multiple variables. During assignment, expressions on the right-hand side are evaluated **left to right** before the values are assigned:
```python
a, b = 0, 1
```

#### `while` Loop
The `while` loop runs as long as the condition evaluates to `True`.  
Conditions can include:
  - **Numbers**: Non-zero integers are `True`; zero is `False`.
  - **Sequences** (strings, lists, etc.): Non-empty sequences are `True`; empty sequences are `False`.

#### Indentation
- Python uses **indentation** to group statements.
- Every line in the block must be indented by the same amount.
- At the interactive prompt:
  - Type spaces or tabs for indentation.
  - Follow compound statements with a blank line to indicate completion.

####  `print()` Function
The `print()` function writes output to the screen. Differences from writing expressions in interactive terminal:
- Handles multiple arguments, floating-point numbers, and strings differently.
- Automatically inserts spaces between arguments.
- Prints strings without quotes.
- Can customize Output with `end` keyword argument
  - Avoid the default newline after output.
  - Specify a different ending string.

#### Comparison Operators
- `<` (less than), `>` (greater than)
- `==` (equal to), `!=` (not equal to)
- `<=` (less than or equal to), `>=` (greater than or equal to)

---

# More Control Flow Tools in Python

## `if` Statements

The `if` statement is used to execute code based on a condition. It can include optional `elif` and `else` parts:

```python
# Syntax
if condition: 
    code...
elif condition:
    code...
elif condition: 
    code...

else: 
    code...

# Example
x = int(input("Please enter an integer: "))
if x < 0:
    x = 0
    print('Negative changed to zero')
elif x == 0:
    print('Zero')
elif x == 1:
    print('Single')
else:
    print('More')
```
- An `if … elif … elif …` sequence is a substitute for the switch or case statements found in other languages.
- `elif` is short for "else if" and prevents **excessive indentation**.
- The `else` part is optional.
- Use the `match` statement for comparing same constant value to several constant.
- Python lets you use any value where it expects a Boolean. 
  - The following are "falsy": `False`, `None`, `[]`, `{}`, `""`, `set()`, `0`, `0.0`.
  - Everything else gets treated as `True`. 
  - This allows the checking of empty lists empty strings, empty dictionaries, etc. using `if` statements. 

### Ternary if-then-else 
```python
parity = "even" if x % 2 == 0 else "odd"
```
---

## `for` Statements

The `for` statement iterates over items of any sequence (like a list or string) in order:

```python
# Syntax 
for variable in iterator: 
    code...

# Example
words = ['cat', 'window', 'defenestrate']
for w in words:
    print(w, len(w))
# o/p
cat 3
window 6
defenestrate 12
```

### Modifying Collections While Iterating

Avoid modifying a collection directly while iterating. Instead, use a copy or create a new collection:

#### Using a Copy:
```python
users = {'Hans': 'active', 'Éléonore': 'inactive', 'John': 'active'}
for user, status in users.copy().items():
    if status == 'inactive':
        del users[user]
```

#### Creating a New Collection:
```python
users = {'Hans': 'active', 'Éléonore': 'inactive', 'John': 'active'}
active_users = {}
for user, status in users.items():
    if status == 'active':
        active_users[user] = status
```

#### Infinite loop

Modifying a collection directly while iterating over it can lead to unexpected behavior, including infinite loops. This happens when the iterator does not account for the structural changes in the collection, causing it to repeatedly process the modified elements.

```python
nums = [1, 2, 3, 4, 5]

for num in nums:
    print(num)
    if num % 2 == 0:
        nums.append(num * 2)  # Modifying the list during iteration
```
##### What Happend?

* The iterator starts with the original list, [1, 2, 3, 4, 5].
* When it encounters 2, it appends 4 (twice its value) to the list.
* The modified list becomes [1, 2, 3, 4, 5, 4].
* The iterator does not track that the new elements have been added, and depending on how Python processes the list, this may cause repeated processing of some elements or even go back to earlier elements.

---

## The `type()` Function

`type()` is a built-in function in Python. It is used for two primary purposes:

### Checking the Type of an Object
When called with one argument, `type(obj)` returns the type of the object `obj`.  
Example:
```python
print(type(42))          # Output: <class 'int'>
print(type(3.14))        # Output: <class 'float'>
print(type("Hello"))     # Output: <class 'str'>
print(type([1, 2, 3]))   # Output: <class 'list'>
```

### Creating New Types (Classes)
When called with three arguments, `type(name, bases, dict)` dynamically creates and returns a new class.  
- `name`: Name of the class (string).
- `bases`: Tuple of base classes (inheritance).
- `dict`: Dictionary containing attributes and methods of the class.  

Example:
```python
MyClass = type('MyClass', (object,), {'x': 42, 'greet': lambda self: "Hello"})
obj = MyClass()
print(obj.x)            # Output: 42
print(obj.greet())      # Output: Hello
```

So, `type()` is versatile, serving both to inspect objects and to define new classes dynamically.

## Iterable 
Iterable is an object **capable of returning its members one at a time**. Examples of iterables include all sequence types (such as list, str, and tuple) and some non-sequence types like dict, file objects, and objects of any classes you define with an __iter__() method or with a __getitem__() method that implements sequence semantics.

## The `range()` Function

Use the built-in `range(start, stop, step)` function to generate sequences of numbers (**arthimetic progressions**):

```python
for i in range(5): # end is not included 
    print(i)

# Outputs
0
1
2
3
4
```

### Customizing `range()`

```python
print(list(range(5, 10)))         # [5, 6, 7, 8, 9]
print(list(range(0, 10, 3)))     # [0, 3, 6, 9]
print(list(range(-10, -100, -30)))  # [-10, -40, -70]
```

### Iterating Over Indices of a Sequence

Combine `range()` and `len()` to iterate over sequence indices:

```python
a = ['Mary', 'had', 'a', 'little', 'lamb']
for i in range(len(a)):
    print(i, a[i])

# Outputs
0 Mary
1 had
2 a
3 little
4 lamb
```

Alternatively, use `enumerate()` for simplicity.

```python
a = ['Mary', 'had', 'a', 'little', 'lamb']
for i, word in enumerate(a):
    print(i, word)
```

### Characteristics of `range()`

`range()` returns an iterable, not a list, **saving memory**. it returns successive elements when invoked. Example of using `range()` with `sum()`:

```python
print(sum(range(4)))  # 0 + 1 + 2 + 3 = 6
```

The type of `range()` object is `range`: 
```python
type(range(10))
<class 'range'>
```

---

## `break`Statement

The `break` statement exits the innermost loop:

```python
for n in range(2, 10):
    for x in range(2, n):
        if n % x == 0:
            print(f"{n} equals {x} * {n//x}")
            break

# Output
4 equals 2 * 2
6 equals 2 * 3
8 equals 2 * 4
9 equals 3 * 3
```

## `continue`

The `continue` statement skips to the next iteration of the loop:

```python
for num in range(2, 10):
    if num % 2 == 0:
        print(f"Found an even number {num}")
        continue
    print(f"Found an odd number {num}")

# Output
Found an even number 2
Found an odd number 3
Found an even number 4
Found an odd number 5
Found an even number 6
Found an odd number 7
Found an even number 8
Found an odd number 9
```

---

## `else` Clauses on Loops

An `else` clause can follow a `for` or `while` loop. The `else` block executes only if the loop completes without encountering a `break` statement.

### For Loops with `else`

In the following example, the `else` clause executes if no factors are found (i.e., the loop does not encounter a `break`). Continue doesn't affect the else clause. 

```python
for n in range(2, 10):
    for x in range(2, n):
        if n % x == 0:
            print(f"{n} equals {x} * {n//x}")
            break
    else:
        # Loop fell through without finding a factor
        print(f"{n} is a prime number")

# Output
2 is a prime number
3 is a prime number
4 equals 2 * 2
5 is a prime number
6 equals 2 * 3
7 is a prime number
8 equals 2 * 4
9 equals 3 * 3
```

### While Loops with `else`

In a `while` loop, the `else` block executes when the loop condition becomes false:

```python
count = 0
while count < 5:
    print(count)
    count += 1
else:
    print("Loop completed without a break.")

# Output
0
1
2
3
4
Loop completed without a break.
```

### Behavior of `else` Clause

The `else` block does not execute if the loop is terminated by a `break`. This behavior is similar to the `else` clause in a `try` statement, which executes only if no exception occurs.

```python
# Syntax
try:
    # Code that might raise an exception
    risky_code()
except SomeException as e:
    # Code to handle the exception
    print(f"An error occurred: {e}")
else:
    # Code that runs if no exceptions were raised in the try block
    print("No errors occurred!")

#Example: 
try:
    num = int(input("Enter a number: "))
    result = 10 / num
except ValueError:
    print("Invalid input! Please enter a valid integer.")
except ZeroDivisionError:
    print("Division by zero is not allowed.")
else:
    print(f"The result is {result}.")
# O/P: 
Enter a number: 5
The result is 2.0
Enter a number: 0
Division by zero is not allowed.
```

---

## `pass` Statements

The `pass` statement does nothing and serves as a placeholder where **a statement is syntactically required but no action is needed**.

### Example: Infinite Loop

```python
while True:
    pass  # Busy-wait for keyboard interrupt (Ctrl+C)
```

### Example: Minimal Class Definition

```python
class MyEmptyClass:
    pass
```

### Example: Placeholder for Future Code

```python
def initlog(*args):
    pass  # Remember to implement this later!
```

## `match` Statements 

The `match` statement in Python **enables structured pattern matching**, offering a powerful way to handle various data scenarios. This feature is inspired by languages like Rust and Haskell and is more versatile than traditional `switch` statements in languages like C, Java, or JavaScript.

### Basic Syntax and Operation
A `match` statement takes an expression and compares its value to successive patterns, executing the first matching `case` block. Patterns can include literals, variables, tuples, objects, and more.

#### Example: Simple Literal Matching
```python
def http_error(status):
    match status:
        case 400:
            return "Bad request"
        case 404:
            return "Not found"
        case 418:
            return "I'm a teapot"
        case _:
            return "Something's wrong with the internet"
```
Here, the `_` serves as a **wildcard**, matching any value not explicitly handled by other cases.

#### Combining Patterns with `|`
Use the `|` operator to match multiple literals:
```python
case 401 | 403 | 404:
    return "Not allowed"
```

### Pattern Matching with Variables
Patterns can bind variables, extracting components from the matched value.

#### Example: Tuple Matching
```python
# `point` is an (x, y) tuple
match point:
    case (0, 0):
        print("Origin")
    case (0, y): # binding the value of y from point
        print(f"Y={y}")
    case (x, 0): # binding the value of x from point
        print(f"X={x}")
    case (x, y): # essentially unpacking the point, (x, y) = point
        print(f"X={x}, Y={y}")
    case _:
        raise ValueError("Not a point")
```

In the above, `x` and `y` are **capture variables**, they fetch the value from the expression.

Now, that we have worked with tuple, it's not a big stretch to talk about Classes and Objects. 

### Matching Objects with Attributes
Class instances can be matched using patterns resembling constructors, binding attributes to variables.

```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

def where_is(point):
    match point:
        case Point(x=0, y=0): # these are matching varialbes. 
            print("Origin")
        case Point(x=0, y=y): # y is capture variable. 
            print(f"Y={y}")
        case Point(x=x, y=0): # x is capture variable.
            print(f"X={x}")
        case Point():
            print("Somewhere else")
        case _:
            print("Not a point")
```

### Using `__match_args__`
The `__match_args__` attribute specifies the **order of attributes** for positional matching that can be used in `match` statements.
```python
class Point:
    __match_args__ = ('x', 'y')
    def __init__(self, x, y):
        self.x = x
        self.y = y

match point:
    case Point(1, var): # var is capture variable. 
        print(f"Y={var}")
    case Point(x=1, y=var): # var is capture variable. 
        print(f"Y={var}")
```

### Nested Patterns
Patterns can be nested for complex matching scenarios.

```python
class Point:
    __match_args__ = ('x', 'y')
    def __init__(self, x, y):
        self.x = x
        self.y = y

match points:
    case []:
        print("No points")
    case [Point(0, 0)]:
        print("The origin")
    case [Point(x, y)]: 
        print(f"Single point {x}, {y}")
    case [Point(0, y1), Point(0, y2)]:
        print(f"Two on the Y axis at {y1}, {y2}")
    case _:
        print("Something else")
```

### Using Guards with `if`
Guards can **add conditions to patterns**, filtering matches further.

```python
match point:
    case Point(x, y) if x == y:
        print(f"Y=X at {x}")
    case Point(x, y):
        print(f"Not on the diagonal")
```

### Additional Features of `match`
#### Sequence Patterns:
Match arbitrary sequences like lists or tuples (not iterators or strings). Support extended unpacking with `*`:
 ```python
 case [x, y, *rest]:
     print(f"First: {x}, Second: {y}, Rest: {rest}")
 ```

#### Mapping Patterns:
Match dictionaries by keys:
 ```python
 case {"bandwidth": b, "latency": l}: # other keys are ignored
     print(f"Bandwidth={b}, Latency={l}")
 ```

#### Capturing Subpatterns with `as`:
Capture parts of a pattern:
```python
case (Point(x1, y1), Point(x2, y2) as p2):
   print(f"Second point: {p2}")
```

#### Literal Comparison:
Most **literals are compared by equality**. However **singleton** `True`, `False`, and `None` are compared by identity.

#### Named Constants:
Prevent interpretation as capture variables using dotted names:
```python
from enum import Enum

class Color(Enum):
   RED = 'red'
   GREEN = 'green'
   BLUE = 'blue'

match color:
   case Color.RED:
       print("I see red!")
   case Color.GREEN:
       print("Grass is green")
   case Color.BLUE:
       print("I'm feeling the blues :(")
```

## `in` Keyword

The `in` keyword is used to check for **membership** in sequences (like lists, strings, tuples, or sets) or to iterate through items in an iterable. This check involves examining the elements of the list one at a time, which means that you probably shouldn't use it unless you know your list is pretty small (or unless you don't care how long the check takes).

### Uses of `in`

#### Membership Testing:
Checks if an element exists in a sequence.

```python
fruits = ["apple", "banana", "cherry"]
print("apple" in fruits)  # True
print("grape" in fruits)  # False
```

#### Iteration in Loops:
Used in `for` loops to iterate over elements in an iterable.

```python
for fruit in fruits:
   print(fruit)
# Output:
# apple
# banana
# cherry
```

---

#### Negation with `not in`
Checks if an element does **not** exist in a sequence.

```python
print("grape" not in fruits)  # True
```
---

## Function

### Key Features of Defining Functions

#### Basic Syntax:  
- The `def` keyword introduces a function definition.  
- The function name is followed by parentheses containing a comma-separated list of parameters.  
- The function body is indented and may include a **docstring** as its first statement to document the function.

```python
def fib(n):
   """Print Fibonacci series less than n."""
   a, b = 0, 1
   while a < n:
       print(a, end=' ')
       a, b = b, a + b
   print()
```

##### Calling Functions:  
Functions are executed when called, e.g., `fib(2000)`.

##### Docstrings:  
 A function can have an optional docstring (enclosed in triple quotes) to describe its purpose. Docstrings are good practice and **help in generating documentation** or for interactive use.

---

### Variable Scope and Symbol Tables

#### Local Symbol Table:  
Each function call creates a new local symbol table for its variables. Variables are first looked up in the local table, then in enclosing functions' tables, global scope, and finally in built-in names.

#### Assigning to Global Variables
The `global` keyword is used **declare** that you want to modify a variable defined at the global (module) level inside a function.

```python
# Global variable
counter = 0

def increment():
    global counter  # Declare that we want to modify the global variable
    counter += 1
    print(f"Counter inside function: {counter}")

increment()
increment()
print(f"Counter outside function: {counter}")

# Output
Counter inside function: 1
Counter inside function: 2
Counter outside function: 2
```

Without the `global` statement, the function would create a new local variable `counter`, and the global `counter` would remain unchanged.

#### Assigning to Nonlocal Variables:
The `nonlocal` keyword is used when you need to modify a variable from an enclosing (non-global) scope, such as in a nested function.

```python
def outer_function():
    count = 0  # Enclosing variable

    def inner_function():
        nonlocal count  # Declare that we want to modify the enclosing variable
        count += 1
        print(f"Count inside inner function: {count}")

    inner_function()
    inner_function()
    print(f"Count in outer function: {count}")

outer_function()

# Output
Count inside inner function: 1
Count inside inner function: 2
Count in outer function: 2
```

Without the `nonlocal` statement, `count` inside `inner_function` would be treated as a local variable, and modifying it would result in an error since it's referenced before assignment.

#### Combining both Global and NonLocal

You can use both `global` and `nonlocal` in different parts of a nested function hierarchy.

```python
# Example
x = 10  # Global variable

def outer_function():
    x = 5  # Enclosing variable

    def inner_function():
        global x  # Modifies the global x
        x += 1
        print(f"Global x modified: {x}")

    def another_inner_function():
        nonlocal x  # Modifies the enclosing x
        x += 1
        print(f"Enclosing x modified: {x}")

    inner_function()
    another_inner_function()

outer_function()
print(f"Global x outside: {x}")

# Output
Global x modified: 11
Enclosing x modified: 6
Global x outside: 11
```
---

### Argument Passing:  
Arguments are passed by **object reference** (commonly called "call by value" where the value is a reference to the object). Mutable objects can be modified within the function.

---

### Functions are First Class Entities

Functions are first-class entities in Python, meaning they have the following properties:

#### They themselves are Objects
```python
def add(x, y):
    return x + y
type(add)
# Output
<class 'function'>
```

#### They can be assigned to variables
Functions can be treated as values and assigned to variables, which can then be used to call the function.

```python
def greet(name):
   return f"Hello, {name}!"

say_hello = greet  # Assign the function to a variable
print(say_hello("Naveen"))  # Output: Hello, Naveen!
```

#### They can be passed as arguments to other functions: 

```python
def execute_function(func, value):
   return func(value)

print(execute_function(len, "Python"))  # Output: 6
```

#### They can be returned from other functions:
Functions can be returned as values from other functions, enabling higher-order functions.

```python
def outer_function(prefix):
   def inner_function(name):
       return f"{prefix}, {name}!"
   return inner_function

greet = outer_function("Hi")
print(greet("Naveen"))  # Output: Hi, Naveen!
```

#### They can be stored in data structures like lists or dictionaries:
Functions can be elements of collections such as lists or values in dictionaries.

```python
def add(x, y):
   return x + y

def subtract(x, y):
   return x - y

operations = {'add': add, 'subtract': subtract}
print(operations['add'](5, 3))       # Output: 8
print(operations['subtract'](5, 3))  # Output: 2
```

This flexibility enables functional programming paradigms and powerful abstractions in Python.

---

### Returning Values
Every function returns a value, even if it does not explicitly include a return statement. If no return statement is specified, the function implicitly returns None. Explicitly returning None or allowing the function to reach the end without a return statement has the same effect.

Unlike some programming languages, Python does not distinguish between functions and procedures (which typically do not return a value). Every function in Python is guaranteed to return something, ensuring consistency and flexibility in its design.

### Notable Python Features Demonstrated

#### Method Calling:  
In Python, we have Methods, apart from function since it is object oriented programming language. For example, he `append()` method adds elements to a list efficiently.

```python
result.append(a)
```
This is equivalent to `result = result + [a]` but more efficient.

#### Returning Multiple Values:  
Python allows returning multiple values as a tuple.  
```python
def example():
   return 1, 2, 3
x, y, z = example()
```

#### Call by Object Reference:  
If a mutable object (e.g., a list) is passed as an argument, modifications inside the function are reflected outside.

---

### Default Argument Values

Default argument values in Python allow functions to be called with fewer arguments than they are defined to accept. This provides flexibility and avoids repetitive argument passing in common use cases.

#### Basic Syntax:
Default values are defined by assigning values to parameters in the function definition. For example:
 ```python
 def ask_ok(prompt, retries=4, reminder='Please try again!'):
     ...
 ```

#### Function Usage:
You can call such functions in multiple ways:
 - **Only mandatory argument**: `ask_ok('Do you really want to quit?')`
 - **One optional argument**: `ask_ok('OK to overwrite the file?', 2)`
 - **All arguments**: `ask_ok('OK to overwrite the file?', 2, 'Come on, only yes or no!')`

#### Evaluation of Default Values:
Default values are evaluated **at the time of function definition**, not at runtime. For example:
```python
i = 5
def f(arg=i):
   print(arg)
i = 6
f()  # Prints 5 because the value of `i` was captured when the function was defined.
```

#### Using Mutable Default Arguments:
Default values are evaluated **only once**, which can lead to unintended behavior if the default is a mutable object (like a list or dictionary). Example of unintended behavior:
```python
def f(a, L=[]): # L = [] get's a location and points to it across calls.
   L.append(a)
   return L
print(f(1))  # [1]
print(f(2))  # [1, 2]
print(f(3))  # [1, 2, 3]
```
The list `L` persists across calls because it is shared between calls.

#### Avoiding Mutable Defaults:
To avoid this issue, use `None` as the default value and initialize the mutable object inside the function:
```python
def f(a, L=None):
   if L is None:
       L = []
   L.append(a)
   return L
print(f(1))  # [1]
print(f(2))  # [2]
print(f(3))  # [3]
```

---

#### Best Practices
- Avoid using mutable objects as default values to prevent unexpected behavior.
- Use `None` as the default and explicitly initialize mutable objects inside the function body.
- Always consider how the default value's evaluation timing might affect function behavior.

### Keyword Arguments (Named Arguments)

Keyword arguments allow functions to be called with arguments explicitly named using the format `kwarg=value`. This enhances flexibility, clarity, and allows positional and optional arguments to be mixed effectively.

#### Basic Usage:
A function can have required positional arguments and optional (default argument ones) keyword arguments:
```python
def parrot(voltage, state='a stiff', action='voom', type='Norwegian Blue'):
   print("-- This parrot wouldn't", action, end=' ')
   print("if you put", voltage, "volts through it.")
   print("-- Lovely plumage, the", type)
   print("-- It's", state, "!")

# Valid Calls
parrot(1000)                                        # 1 positional argument
parrot(voltage=1000)                                # 1 keyword argument
parrot(voltage=1000000, action='VOOOOOM')           # 2 keyword arguments
parrot(action='VOOOOOM', voltage=1000000)           # Order doesn't matter for keyword arguments
parrot('a million', 'bereft of life', 'jump')       # 3 positional arguments
parrot('a thousand', state='pushing up  daisies')   # Mixed positional and keyword
```

#### Invalid Calls:
- Missing required arguments: `parrot()` → Error.
- Mixing positional arguments **after** keyword arguments: `parrot(voltage=5.0, 'dead')` → Error.
- Providing multiple values for the same argument: `parrot(110, voltage=220)` → Error.
- Using unknown arguments: `parrot(actor='John Cleese')` → Error.

#### Rules for Keyword Arguments:
- Keyword arguments must **follow all positional arguments**.
- Each argument can **receive a value only once**.
- The order of keyword arguments in the function call does not matter.
- All keyword arguments must match the parameter names in the function definition.

### Using `*args` and `**kwargs`**:
The `*args` parameter collects additional positional arguments into a tuple. This should be placed before all keyword arguments. The `**kwargs` parameter collects additional keyword arguments into a dictionary. The order in which keyword arguments are printed matches the order they are provided during the function call.

**Example**:
```python
def cheeseshop(kind, *arguments, **keywords):
   print("-- Do you have any", kind, "?")
   print("-- I'm sorry, we're all out of", kind)
   for arg in arguments:
       print(arg)
   print("-" * 40)
   for kw in keywords:
       print(kw, ":", keywords[kw])

# Example
cheeseshop(
   "Limburger",
   "It's very runny, sir.",
   "It's really very, VERY runny, sir.",
   shopkeeper="Michael Palin",
   client="John Cleese",
   sketch="Cheese Shop Sketch"
)

# Output
-- Do you have any Limburger ?
-- I'm sorry, we're all out of Limburger
It's very runny, sir.
It's really very, VERY runny, sir.
----------------------------------------
shopkeeper : Michael Palin
client : John Cleese
sketch : Cheese Shop Sketch
```

#### Best Practices
- Use keyword arguments to improve function call clarity and avoid mistakes in argument order.
- Use `*args` and `**kwargs` when creating flexible functions that can handle variable numbers of arguments.
- Ensure that all required arguments are provided, either positionally or by name.

---

### Special Parameters

Python allows arguments to be passed to functions by position or by keyword. For clarity and better control, **the way arguments are passed can be restricted** using special symbols (`/` and `*`) in function definitions. These symbols define **positional-only**, **positional-or-keyword**, and **keyword-only** arguments.

#### Positional-or-Keyword Arguments:
This is the **default behavior** when `/` and `*` are not used. Arguments can be passed by position or keyword. And the old rules follow shere, positional arguments come before keyword arguments. For Example: 
```python
def standard_arg(arg):
   print(arg)
standard_arg(2)         # Positional
standard_arg(arg=2)     # Keyword
```

#### Positional-Only Parameters:
This is defined by placing a `/` in the function definition. **Arguments must be passed by position**; using keywords for these parameters raises an error. Useful for enforcing strict argument order or preventing reliance on parameter names. For example: 
```python
def pos_only_arg(arg, /):
   print(arg)
pos_only_arg(1)         # Valid
pos_only_arg(arg=1)     # TypeError: argument must be positional
```

#### Keyword-Only Parameters:
Defined by placing a `*` before the first keyword-only parameter. These arguments must be passed by keyword, not position. Useful for explicit function calls where argument names add clarity. For example: 
```python
def kwd_only_arg(*, arg):
   print(arg)
kwd_only_arg(arg=3)     # Valid
kwd_only_arg(3)         # TypeError: argument must be a keyword
```

#### Combined Use of `/` and `*`:
A function can mix all three parameter types: positional-only, positional-or-keyword, and keyword-only. For example, 
```python
def combined_example(pos_only, /, standard, *, kwd_only):
   print(pos_only, standard, kwd_only)

combined_example(1, 2, kwd_only=3)                      # Valid
combined_example(1, standard=2, kwd_only=3)             # Valid 
combined_example(pos_only=1, standard=2, kwd_only=3)    # TypeError
combined_example(1, 2, 3)                               # TypeError
```

#### Handling Name Collisions:
Positional-only arguments can avoid conflicts with `**kwargs`. For example, 
```python
def foo(name, /, **kwds):
   return 'name' in kwds

foo(1, **{'name': 2})   # True
foo(1, name=2)          # True
foo(name=1)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: foo() missing 1 required positional argument: 'name'
>>> 

```
In the above, by using `/` we instructure that the positional argument `name` in formal parameter an never be passed as keyword argument, this helps thwart ambiguity. 

#### Errors and Ambiguities:
Using the same parameter as both positional and keyword:
```python
def foo(name, **kwds):
   return 'name' in kwds
foo(1, **{'name': 2})  # TypeError: multiple values for argument 'name'
```

#### Guidelines for Usage

1. **Positional-Only Parameters**:
   - Use when **parameter names are irrelevant** or could change without breaking the API.
   - Enforce strict argument order for **performance**.

2. **Keyword-Only Parameters**:
   - Use when argument names are meaningful and enhance code readability.
   - Ensure users cannot rely on the position of arguments.

3. **Combining Both**:
   - Combine `/` and `*` to create clear and precise APIs.
   - Example:
     ```python
     def f(pos1, pos2, /, pos_or_kwd, *, kwd1, kwd2):
         pass
     ```
#### Advantages

- **Readability**: Restricting argument passing improves code clarity by showing intent directly in the function signature.
- **Robust APIs**: Helps prevent breaking changes in APIs when parameter names are modified.
- **Control**: Allows developers to enforce positional arguments or require explicit naming for clarity and maintainability.

---

### Arbitrary Argument Lists
Functions can accept an arbitrary number of arguments, which are gathered into a tuple using the `*args` syntax. These variadic arguments must appear after any normal positional arguments. For example `write_multiple_items(file, separator, *args)` where `args` is **a tuple** containing extra arguments. Keyword-only arguments must be placed after the `*args` parameter and can only be passed as keywords, not positional arguments.
```python
def concat(*args, sep="/"):
    return sep.join(args)

concat("earth", "mars", "venus")  # 'earth/mars/venus'
concat("earth", "mars", "venus", sep=".")  # 'earth.mars.venus'
```

### Unpacking Argument Lists
When arguments are already stored in a list or tuple, they can be unpacked using the **`*` operator** in function calls that require separate positional arguments. Example of unpacking arguments for the `range()` function:
```python
args = [3, 6]
list(range(*args))  # [3, 4, 5]
```
Similarly, dictionaries can be used to pass keyword arguments to functions using the `**` operator. Example of using a dictionary for keyword arguments:
```python
def parrot(voltage, state='a stiff', action='voom'):
    print(f"-- This parrot wouldn't {action} if you put {voltage} volts through it. E's {state}!")
d = {"voltage": "four million", "state": "bleedin' demised", "action": "VOOM"}
parrot(**d)  # Output: -- This parrot wouldn't VOOM if you put four million volts through it. E's bleedin' demised!
```


A common idiom is to use an underscore for a value you're going to throw
away:
```python
_, y = [1, 2] # now y == 2, didn't care about the first element
```
---

### Function Annotations

**Function annotations** provide a way **to add metadata** to the parameters and return values of functions. They **are optional** and serve as **a way to document** the types or other properties of function inputs and outputs. Function annotations have **no impact on the execution of the function**, but they can be accessed programmatically for **purposes such as documentation or type checking**.

#### Syntax of Annotations:
**Parameter Annotations**: A colon `:` is used after the parameter name, followed by an expression that evaluates to the annotation.  
**Return Annotations**: A literal `->` is used before the return type annotation, placed between the parameter list and the colon that ends the `def` statement.

**For example**
```python
def f(ham: str, eggs: str = 'eggs') -> str:
   return ham + ' and ' + eggs
```

#### How Annotations are Stored:
Annotations are stored in the **`__annotations__` attribute** of the function as a dictionary. The dictionary keys are the parameter names (and 'return' for the return type), and the values are the corresponding annotations.

In the following example, the function `f` has annotated parameters and a return type:
```python
def f(ham: str, eggs: str = 'eggs') -> str:
   print("Annotations:", f.__annotations__)
   print("Arguments:", ham, eggs)
   return ham + ' and ' + eggs

f('ham') 
# Outputs: 
# Annotations: {'ham': <class 'str'>, 'eggs': <class 'str'>, 'return': <class 'str'>}
# Arguments: spam eggs
# 'spam and eggs'
```

#### Good Reasons to use function annotations
Types are an important form of documentation. Compare the following two function stubs, the second one is more informative:
```python
def dot_product(x, y): ...
def dot_product(x: Vector, y: Vector) -> float: ...
```


There are external tools (the most popular is mypy) that will read your code, inspect the type annotations, and let you know about type errors before you ever run your code. For example, if you ran mypy over a file containing add("hi ", "there"), it would warn you:

```python
error: Argument 1 to "add" has incompatible type "str"; expected
"int"
```
Like assert testing, this is a good way to find mistakes in your code before you ever run it. The narrative in the book will not involve such a type checker; however, behind the scenes I will be running one, which will help ensure that the book itself is correct.


Having to think about the types in your code forces you to design cleaner functions and interfaces:
```python
from typing import Union
def secretly_ugly_function(value, operation): ...
def ugly_function(value: int,
operation: Union[str, int, float, bool]) -> int:
...
```

Here we have a function whose operation parameter is allowed to be a string, or an int, or a float, or a bool. It is highly likely that this function is fragile and difficult to use, but it becomes farmore clear when the types are made explicit. Doing so, then, will force us to design in a less clunky way, for which our users will thank us.

For more on this checkout [typing module](#typing)



---

## Lambda Expressions

Lambda expressions provide a concise way to define **small, anonymous** functions. These functions are syntactically limited to a single expression, but they can be used wherever a function object is required. Although lambda functions are often viewed as a more compact alternative to traditional function definitions, they are **semantically equivalent to standard functions**. Just like functions they can access variables from the enclosing scope. 

A lambda expression follows this syntax:
```python
lambda arguments: expression
```
- **Arguments**: The input parameters to the function (can be zero or more).
- **Expression**: A single expression that gets evaluated and returned when the function is called.

A simple lambda function that adds two arguments:
```python
lambda a, b: a + b
```

> ### Note: 
> Assigning lambdas to variables is bad practice and needs to be avoided.

### Example of Lambda in Practice:
A function `make_incrementor` returns a lambda function that increments its argument by a given value:
```python
def make_incrementor(n):
    return lambda x: x + n
```
Usage:
```python
inc_42 = make_incrementor(42)
print(inc_42(0))  # Output: 42
print(inc_42(1))  # Output: 43
```
Here, the lambda function adds `n` (in this case, 42) to its argument `x`. The lambda expression is returned and stored in `f`.

### Lambda Functions as Arguments:
Lambda expressions are often used as arguments in functions that require a function object. For example, `sort()`, `map()`, `filter()`, and `reduce()`. This allows for passing small, one-off functions without having to define a full function.

#### Example of Using Lambda in Sorting:
In this example, we use a lambda function to specify the key by which a list of tuples should be sorted:
```python
pairs = [(1, 'one'), (2, 'two'), (3, 'three'), (4, 'four')]
pairs.sort(key=lambda pair: pair[1])
print(pairs)  # Output: [(4, 'four'), (1, 'one'), (3, 'three'), (2, 'two')]
```

## Documentation Strings

Documentation strings (also known as docstrings) in Python provide a way to document the purpose, behavior, and usage of functions, classes, and modules. Python has a specific convention for formatting these docstrings to ensure consistency and clarity. 

### Key Conventions for Writing Documentation Strings:

#### Concise Summary in the First Line
- The first line of a docstring should offer a short and clear summary of the object's purpose or behavior. 
- **Do not include the object's name or type** in this summary unless the name is a verb describing the function's operation (e.g., `fetch_data()` might be summarized as "Fetches data from the server").
- The first line should begin with a capital letter and end with a period.

Example:
```python
def fetch_data():
   """Fetches data from the server."""
   pass
```

#### Blank Line Separating Summary from Further Details
- If the docstring contains more than one line, the second line should be **blank**. This blank line visually separates the concise summary from the rest of the documentation.
- After the blank line, you can provide additional details such as the function's parameters, return values, side effects, exceptions, and usage examples.

Example:
```python
def fetch_data(url):
   """Fetches data from the server.

   This function makes a GET request to the provided URL and returns the response content.
   It raises a ValueError if the URL is invalid.
   """
   pass
```

#### Multi-line Docstrings and Indentation
- In Python, the parser does not automatically strip indentation from multi-line string literals. Therefore, documentation tools that process docstrings must account for indentation.
- The convention to handle this is:
  - **The first non-blank line after the docstring's opening quotes** determines the indentation level for the entire docstring.
  - Any leading whitespace "equivalent" to this indentation is stripped from all subsequent lines.
  - Whitespace equivalency is checked after tabs are expanded to spaces (usually 8 spaces).
  - **Indentation**: Ensure that the docstring is properly aligned with the function's or class's code indentation. The documentation should be indented the same amount as the code block it is in.

Example:
```python
def my_function():
    """Do nothing, but document it.

    This line determines the indentation here after. 
    """
    pass

print(my_function.__doc__)
```
Output:
```
Do nothing, but document it.

This line determines the indentation here after.
```

### Content of Documentation Strings
Beyond the initial summary, the docstring should provide:
- **Function or Method Behavior**: A description of what the function or method does.
- **Parameters**: A description of each parameter, including their expected types.
- **Return Values**: A description of what the function returns (if applicable), including the return type.
- **Side Effects**: Any effects the function has beyond returning a value, such as modifying data or interacting with external systems.
- **Exceptions**: A list of exceptions the function might raise, and under what circumstances.
- **Examples**: Optional, but useful examples demonstrating how to use the function or class.

Example:
```python
def fetch_data(url):
    """Fetches data from the server.

    Arguments:
        url (str): The URL to fetch data from.

    Returns:
        str: The content of the response.

    Raises:
        ValueError: If the URL is invalid or the request fails.
   """
   pass
```

### Best Practices for Formatting Docstrings
- **Keep the first line brief**: It should only provide a high-level summary.
- **Use reStructuredText**: This is a lightweight markup language commonly used for docstring formatting in Python. Tools like Sphinx can process reStructuredText-formatted docstrings to generate documentation.
- **Be consistent**: Follow the same formatting conventions throughout the codebase for readability and maintainability.

## Intermezzo - Coding Style

Let's look at coding style guidelines that promote readability and maintainability in Python code. By adhering to these conventions, developers can write code that is easier for others to read, understand, and maintain. The guidelines are based on **[PEP 8](https://peps.python.org/pep-0008/)**, which is the **official style guide** for Python.

### Key Guidelines from PEP 8:

#### Indentation:
- Use **4 spaces** for indentation, not tabs.
- **Why?**: 4 spaces provide a good balance between readability and compactness, while tabs can cause confusion due to potential tab width differences across environments.

#### Line Length:
- Wrap lines so that they **don't exceed 79 characters**.
- **Why?**: This makes it easier to read code on smaller displays and allows multiple files to be viewed side-by-side on larger screens.

#### Blank Lines:
- Use **blank lines** to separate functions, classes, and larger code blocks inside functions.
- **Why?**: Blank lines improve readability and help separate logical sections of the code.

#### Comments:
- When possible, place comments **on their own line**.
- Use **docstrings** for documenting functions, classes, and methods.
- **Why?**: Clear and concise comments help explain the code's logic, making it easier for others to understand.

#### Spacing Around Operators:
- Use **spaces around operators** and **after commas**, but **not inside brackets** (e.g., `a = f(1, 2) + g(3, 4)`).
- **Why?**: Consistent spacing makes the code more visually appealing and easier to read.

#### Naming Conventions:
- **Classes** should be named using **UpperCamelCase**.
- **Functions and methods** should be named using **lowercase_with_underscores**, **snake_case**.
- Always use `self` as the first argument for methods in classes.
- **Why?**: Consistent naming makes it easier to recognize different types of code elements (classes vs. functions).

#### Character Encoding:
- **Avoid using fancy encodings**. Stick to **UTF-8** or **plain ASCII**.
- **Why?**: Using a standard encoding ensures compatibility across various environments and platforms.

#### Non-ASCII Characters:
- Avoid **non-ASCII characters in identifiers** if the code is likely to be used or maintained by people who may not speak the same language.
- **Why?**: Using non-ASCII characters can cause issues in international environments and may be confusing to non-native speakers.

---

## Zen of Python

This is **The Zen of Python**, a collection of guiding principles for writing Pythonic code, authored by Tim Peters. It's a playful yet insightful set of aphorisms that encapsulate Python's philosophy and best practices. To view it just type `import this` in interactive shell. 

```
>>> import this
The Zen of Python, by Tim Peters

Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!
```

### Explanation
1. **Beautiful is better than ugly.**
   - Strive for code that is aesthetically pleasing and clean, as it's easier to read and maintain.

2. **Explicit is better than implicit.**
   - Code should clearly express its intent, avoiding hidden or ambiguous behavior.

3. **Simple is better than complex.**
   - Opt for simplicity in your design and implementation. Complexity should only be introduced when absolutely necessary.

4. **Complex is better than complicated.**
   - When complexity is unavoidable, ensure it is well-organized and understandable, not convoluted or messy.

5. **Flat is better than nested.**
   - Minimize deep levels of nesting in structures or logic, as they can make code harder to follow.

6. **Sparse is better than dense.**
   - Avoid cramming too much into one line or block of code. Allow your code to "breathe."

7. **Readability counts.**
   - Prioritize readability, as code is often read more times than it is written.

8. **Special cases aren't special enough to break the rules.**
   - Stick to consistent rules and patterns; exceptions should be rare.

9. **Although practicality beats purity.**
   - Pragmatism is valued over strict adherence to theoretical ideals.

10. **Errors should never pass silently.**
    - Errors should be detected and addressed, not ignored.

11. **Unless explicitly silenced.**
    - If an error needs to be suppressed, do so explicitly (e.g., with proper error-handling mechanisms).

12. **In the face of ambiguity, refuse the temptation to guess.**
    - Code should avoid ambiguous behavior; clarity and determinism are key.

13. **There should be one-- and preferably only one --obvious way to do it.**
    - Python aims for a single clear approach to solving a problem, promoting consistency and simplicity.

14. **Although that way may not be obvious at first unless you're Dutch.**
    - A playful nod to Python's creator, Guido van Rossum, who is Dutch. Some solutions might require deeper understanding.

15. **Now is better than never.**
    - Don't procrastinate; start solving problems now.

16. **Although never is often better than *right* now.**
    - Rushing to implement something without proper planning can lead to poor decisions.

17. **If the implementation is hard to explain, it's a bad idea.**
    - Complicated solutions are usually not ideal.

18. **If the implementation is easy to explain, it may be a good idea.**
    - Solutions that are straightforward to explain are more likely to be robust and maintainable.

19. **Namespaces are one honking great idea -- let's do more of those!**
    - Namespaces (e.g., modules, classes) help organize and isolate code, making it more modular and reusable.

---

# Data Structures

Python has a number of built-in collection classes. Lists, string, and tuples are ordered collections, sets and dictionaries are unordered collections. 

## Operations on Any Sequence in Python

| **Operation Name** | **Operator** | **Explanation**                                |
|---------------------|--------------|------------------------------------------------|
| **Indexing**        | `[ ]`        | Access an element of a sequence               |
| **Concatenation**   | `+`          | Combine sequences together                    |
| **Repetition**      | `*`          | Concatenate a repeated number of times        |
| **Membership**      | `in`         | Ask whether an item is in a sequence          |
| **Length**          | `len`        | Ask the number of items in the sequence       |
| **Slicing**         | `[ : ]`      | Extract a part of a sequence                  |

## List 

Python lists are versatile, mutable sequences that can hold an ordered collection of items. 

The following table summarizes the key methods available for Python lists:

| **Method**            | **Description**                                                                                       | **Return Type**  | **Example Usage**                                    |
|------------------------|-------------------------------------------------------------------------------------------------------|-------------------|-----------------------------------------------------|
| `list.append(x)`      | Adds `x` to the end of the list. Similar to `a[len(a):] = [x]`.                                         | `None`           | `a.append(10)`                                      |
| `list.extend(iterable)` | Appends all elements from `iterable` to the list. Similar to `a[len(a):] = iterable`.                | `None`           | `a.extend([4, 5, 6])`                              |
| `list.insert(i, x)`   | Inserts `x` at position `i`.                                                                          | `None`           | `a.insert(1, "item")`                              |
| `list.remove(x)`      | Removes the first occurrence of `x`. Raises `ValueError` if `x` is not found.                         | `None`           | `a.remove("item")`                                 |
| `list.pop(i)`         | Removes and returns the element at position `i` (last item if `i` is omitted). Raises `IndexError`.   | `Element`        | `a.pop(2)`                                         |
| `list.clear()`        | Removes all elements from the list. Similar to `list[:] = []`.                                                                 | `None`           | `a.clear()`                                        |
| `list.index(x, start, end)` | Returns the index of the first occurrence of `x` in the list. Searches within `[start:end]`.      | `int`            | `a.index("item", 1, 5)`                            |
| `list.count(x)`       | Counts the number of occurrences of `x` in the list.                                                  | `int`            | `a.count(10)`                                      |
| `list.sort(*, key=None, reverse=False)` | Sorts the list in-place. Accepts optional `key` for custom sorting and `reverse`.      | `None`           | `a.sort(reverse=True)`                             |
| `list.reverse()`      | Reverses the list in-place.                                                                           | `None`           | `a.reverse()`                                      |
| `list.copy()`         | Returns a shallow copy of the list.                                                                   | `list`           | `b = a.copy()`                                     |
| `del list` <br> `del list[index]` | Delete list or an item in list.  | `None` | `del task_list` <br> `del alist[4]` |
---

Let's look at how some of these methods work: 

### `list.append()`
Add item to end of the list. 

```python
>>> list = [1,2,3,4]
>>> list.append(5)
>>> list
[1, 2, 3, 4, 5]


>>> list += 6
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'int' object is not iterable

# Append alternatives - Concatenation
>>> list += [6]
>>> list
[1, 2, 3, 4, 5, 6]

# Append alternatives - Slicing
>>> list[len(list):] = [7]
>>> list
[1, 2, 3, 4, 5, 6, 7]
>>> 
```

### `list.extend()`

Add bunch of items to the end of list. 

```python
>>> list
[1, 2, 3, 4, 5, 6, 7]
>>> list.extend([8,9])
>>> list
[1, 2, 3, 4, 5, 6, 7, 8, 9]

# Extend can take any iterable.
>>> list.extend("Hello")
>>> list
[1, 2, 3, 4, 5, 6, 7, 8, 9, 'H', 'e', 'l', 'l', 'o']

# Extend alternatives - Slicing
>>> list[len(list):] = "World"
>>> list
[1, 2, 3, 4, 5, 6, 7, 8, 9, 'H', 'e', 'l', 'l', 'o', 'W', 'o', 'r', 'l', 'd']
>>> 
```

### `list.insert(i, x)`
Insert the element `x` at index `i`.

```python
>>> list.insert(0, 0)
>>> list
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 'H', 'e', 'l', 'l', 'o', 'W', 'o', 'r', 'l', 'd']

>>> list.insert(10, 10)
>>> list
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 'H', 'e', 'l', 'l', 'o', 'W', 'o', 'r', 'l', 'd']

# Handles out of index gracefully.
>>> list.insert(len(list) +5, 'some_value')
>>> list
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 'H', 'e', 'l', 'l', 'o', 'W', 'o', 'r', 'l', 'd', 'some_value']
>>> 
```

#### `list.count(x)` 
```python
fruits = ['orange', 'apple', 'pear', 'banana', 'kiwi', 'apple', 'banana']
print(fruits.count('apple'))  # Output: 2
print(fruits.count('tangerine'))  # Output: 0
```

#### `list.index(x, start_index, end_index)` 
```python
print(fruits.index('banana'))  # Output: 3
print(fruits.index('banana', 4))  # Search starting at position 4. Output: 6
```

#### `list.reverse()` and `list.sort(*, key=None, reverse=False)`
```python
fruits.reverse()
print(fruits)  # Output: ['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange']

fruits.sort()
print(fruits)  # Output: ['apple', 'apple', 'banana', 'banana', 'grape', 'kiwi', 'orange', 'pear']
```

#### `list.pop(index)`
```python
fruits.append('grape')
print(fruits)  # Adds 'grape' to the list.

last_item = fruits.pop()
print(last_item)  # Removes and returns 'pear'.
```


### Note

1. **Methods Without Return Values:**
   - Methods like `insert`, `remove`, `sort`, `reverse`, and `append` modify the list in place and return `None`. This design ensures clarity when dealing with mutable structures.

2. **Type Restrictions in Sorting:**
   - Sorting is not defined for all data types.
     - Example: `[None, 'hello', 10]` will raise an error because integers cannot be compared with strings, nor can `None` be compared to other types.
     - Similarly, complex numbers do not have a defined ordering: `3+4j < 5+7j` is invalid.

3. **Mutability:**
   - Lists are mutable, meaning their contents can be changed after creation.

---

### Using Lists as Stacks

A **stack** operates on a Last-In, First-Out (LIFO) principle. Python lists support stack operations with the following methods:
- **`append()`**: Adds an item to the top of the stack. 
- **`pop()`**: Removes and returns the item from the top of the stack.
The are efficient since they occur at the end of the list. Hence list is very suitable data structure for implementing Stacks. 

```python
stack = [3, 4, 5]
stack.append(6)  # Add 6 to the stack
stack.append(7)  # Add 7 to the stack
print(stack)     # Output: [3, 4, 5, 6, 7]

stack.pop()      # Removes and returns 7
print(stack)     # Output: [3, 4, 5, 6]

stack.pop()      # Removes and returns 6
stack.pop()      # Removes and returns 5
print(stack)     # Output: [3, 4]
```

### Using Lists as Queues

A **queue** operates on a First-In, First-Out (FIFO) principle. While Python lists can be used as queues:
- **`pop(0)`**: Removes and returns the first element.
- **`append()`**: Adds an item to the end of the list.

However, **lists are not ideal for queues** due to inefficiency:
- **Removing from the beginning (`pop(0)`)** requires shifting all subsequent elements, which is slow for large lists.

```python
queue = [3, 4, 5]
queue.append(6)  # Add 6 to the stack
queue.append(7)  # Add 7 to the stack
print(queue)     # Output: [3, 4, 5, 6, 7]

queue.pop(0)      # Removes and returns 3
print(queue)     # Output: [4, 5, 6, 7]

queue.pop()      # Removes and returns 4
queue.pop()      # Removes and returns 5
print(queue)     # Output: [6, 7]
```

#### Recommended Alternative: `collections.deque`
Pronunced as **deck**, it is designed for fast appends and pops at both ends. Efficient for queue implementations. Here are some `deque` methods: 
* `append(x)`
* `appendleft(x)`
* `pop(i)`
* `popleft(i)`
* `extend(iterable)`
* `extendleft(iterable)` inserted in reverse order. 

```python
from collections import deque

queue = deque(["Eric", "John", "Michael"])
queue.append("Terry")  # Add Terry to the queue
queue.append("Graham")  # Add Graham to the queue

queue.popleft()  # Removes and returns 'Eric'
queue.popleft()  # Removes and returns 'John'
print(queue)     # Output: deque(['Michael', 'Terry', 'Graham'])
```

---

### List Comprehensions

List comprehensions offer a concise, readable way to construct lists, applying operations or filters to elements from other sequences or iterables. It consists of brackets containing an expression followed by a `for` clause, then zero or more `for` or `if` clasues.

```python
[expression for item in iterable if condition]
```
- **`expression`**: Defines how each element is processed.
- **`for item in iterable`**: Iterates over the sequence.
- **`if condition`** *(optional)*: Filters elements based on a condition.

---

#### Example: Creating a List of Squares
```python
squares = [x**2 for x in range(10)]
print(squares)  # Output: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

#### Example: Combining Elements from Two Lists (With a Condition)
```python
combs = [(x, y) for x in [1, 2, 3] for y in [3, 1, 4] if x != y]
print(combs)  
# Output: [(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
```

#### Examples: Operation on list Elements
**Doubling Elements:**
```python
vec = [-4, -2, 0, 2, 4]
doubled = [x * 2 for x in vec]
print(doubled)  # Output: [-8, -4, 0, 4, 8]
```

**Filtering Negative Numbers:**
```python
filtered = [x for x in vec if x >= 0]
print(filtered)  # Output: [0, 2, 4]
```

**Applying a Function:**
```python
abs_values = [abs(x) for x in vec]
print(abs_values)  # Output: [4, 2, 0, 2, 4]
```

**Calling Methods:**
```python
freshfruit = [' banana', ' loganberry ', 'passion fruit ']
stripped = [fruit.strip() for fruit in freshfruit]
print(stripped)  # Output: ['banana', 'loganberry', 'passion fruit']
```

#### Example: Creating Tuples
```python
squares_tuples = [(x, x**2) for x in range(6)]
print(squares_tuples)  
# Output: [(0, 0), (1, 1), (2, 4), (3, 9), (4, 16), (5, 25)]
```

#### Exmaple: Flattening Nested Lists
```python
vec = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flattened = [num for sublist in vec for num in sublist]
print(flattened)  # Output: [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

#### Example: Using Mathematical Functions
```python
from math import pi
rounded_pi = [str(round(pi, i)) for i in range(1, 6)]
print(rounded_pi)  # Output: ['3.1', '3.14', '3.142', '3.1416', '3.14159']
```

---


Nested list comprehensions allow processing nested structures, such as lists of lists. The later `for`s can you the result of earlier ones. A Simple example demonstrating syntax: 

```python
increasing_pairs = [(x, y)
for x in range(10)
for y in range(x+1, 10)]
```

#### Example: Matrix Transposition
```python
matrix = [
    [1, 2, 3, 4],
    [5, 6, 7, 8],
    [9, 10, 11, 12]
]
```

##### Nested List Comprehension
```python
transposed = [[row[i] for row in matrix] for i in range(4)]
print(transposed)
# Output: [[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```

##### Equivalent Code Without List Comprehension:
```python
transposed = []
for i in range(4):
    transposed_row = []
    for row in matrix:
        transposed_row.append(row[i])
    transposed.append(transposed_row)
print(transposed)
```

##### Using Built-In Functions:
The `zip()` function simplifies matrix transposition:
```python
transposed = list(zip(*matrix))
print(transposed)
# Output: [(1, 5, 9), (2, 6, 10), (3, 7, 11), (4, 8, 12)]
```

---

#### Key Considerations
1. **Parentheses for Tuples:**
   When creating tuples in a comprehension, enclose them in parentheses to avoid syntax errors:
   ```python
   [(x, x**2) for x in range(6)]
   ```

2. **Performance:**
   - List comprehensions are **faster** and **more readable** for simpler cases than loops.
   - Avoid excessive nesting for maintainability; use built-ins like `zip()` when possible.

3. **Readability:**
   - Complex comprehensions may reduce clarity. Favor simplicity or explanatory comments for nested structures.

---

## The `del` Statement

The `del` statement in Python provides a flexible way to remove elements from lists, slices of lists, or even entire variables. Unlike the `pop()` method, which removes an element and returns its value, `del` **removes elements without returning anything**. This makes it ideal for scenarios where returning a value is unnecessary.

`del` statement are anlogous with `list.pop()` and `list[start:end] = []`.

### Key Features and Use Cases

#### 1. Removing an Item by Index
The `del` statement removes an element from a list based on its **index**. 
```python
a = [-1, 1, 66.25, 333, 333, 1234.5]
del a[0]  # Removes the first element
print(a)  # Output: [1, 66.25, 333, 333, 1234.5]
```


#### 2. Removing Slices
It can also delete multiple elements by specifying a **slice**.

```python
a = [1, 66.25, 333, 333, 1234.5]
del a[2:4]  # Removes elements from index 2 to 3
print(a)  # Output: [1, 66.25, 1234.5]
```


#### 3. Clearing the Entire List
Assigning an empty slice effectively clears all elements of the list.

```python
a = [1, 66.25, 1234.5]
del a[:]  # Removes all elements
print(a)  # Output: []
```
---

#### 4. Deleting Entire Variables
The `del` statement can delete an entire variable, making it unavailable for further use.

```python
del a  # Deletes the variable `a`
# Accessing `a` now would raise a NameError
```

#### 5. Deleting Variables vs. Collection Types

#### Case 1: Deleting a Variable
When you use `del` on a variable, it removes the variable but **does not affect the object it references** if other variables still hold references to it.

The reference remains unaffected. 
```python
>>> list = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 'H', 'e', 'l', 'l', 'o']
>>> another_list = list  # Both `list` and `another_list` reference the same object.
>>> del another_list     # Deletes only the `another_list` variable, not the object.
>>> list                 # The object remains accessible via `list`.
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 'H', 'e', 'l', 'l', 'o']
```

#### Case 2: Deleting Collection Contents
If you use `del` with slicing (e.g., `del variable[:]`), it removes the contents of the collection while keeping the object itself intact. This affects all variables referencing the same object.

The varialbe itself remains unaffected. 
```python
>>> another_list = list  # Both `list` and `another_list` reference the same object.
>>> del another_list[:]  # Clears the contents of the object.
>>> another_list         # The `another_list` is now empty.
[]
>>> list                 # The original reference (`list`) is also affected.
[]
```

### Advantages of Using `del`
1. **Flexibility**: 
   - Can handle individual elements, slices, or the entire list.
   - Works on non-list objects, such as deleting variables.

2. **Efficiency**: 
   - Eliminates the need for iterative loops when removing multiple elements or slices.

3. **Clear Intent**: 
   - Explicitly communicates the intention to delete an item, slice, or variable.

### Practical Considerations
- **Safety**: Use `del` cautiously when deleting slices or variables, as unintended deletions may lead to runtime errors.
- **Readability**: In cases where the list must be cleared, `a[:] = []` is a more explicit alternative than `del a[:]`.

---

## Tuples

Tuples are one of Python's sequence data types, alongside lists and strings. While they share certain properties with other sequences, like indexing and slicing, they have distinct features and use cases

### Definition and Syntax
A tuple is a collection of values separated by commas. For example, 
```python
t = 12345, 54321, 'hello!'
print(t[0])  # Output: 12345
print(t)     # Output: (12345, 54321, 'hello!')
```
Parentheses are optional when defining tuples, but they are often required for clarity or in larger expressions.

### Immutability
Tuples are immutable, meaning their elements cannot be modified after creation. For example:
```python
t[0] = 88888  # Raises TypeError
```

### Heterogeneous and Nested Elements
Tuples often hold heterogeneous data (elements of different types), while lists typical hold homogenous elements. They also support nesting: 
```python
u = t, (1, 2, 3, 4, 5)
print(u)  # Output: ((12345, 54321, 'hello!'), (1, 2, 3, 4, 5))
```

### Mutable Objects in Tuples
Tuples can contain mutable objects, such as lists:
```python
v = ([1, 2, 3], [3, 2, 1])
print(v)  # Output: ([1, 2, 3], [3, 2, 1])

# Making tuples mutable by making it hold lmutable objects
>>> l1 = [1,2]
>>> l2 = [3,4]
>>> t1 = (l1,l2)
>>> t1
([1, 2], [3, 4])
>>> l1[1] = 5
>>> t1
([1, 5], [3, 4])

```
### Empty Tuples
Defined using an empty pair of parentheses:
```python
empty = ()
print(len(empty))  # Output: 0
```

### Singleton Tuples (Tuples with One Element)
Require a trailing comma:
```python
singleton = 'hello',
print(singleton)  # Output: ('hello',)
```

### Tuple Packing
Packing multiple values into a tuple:
```python
t = 12345, 54321, 'hello!'
```

### Sequence Unpacking
Extracting elements from a sequence into variables:
```python
x, y, z = t
print(x, y, z)  # Output: 12345 54321 hello!
```
Requires the number of variables on the left to match the number of elements in the sequence.

### Multiple Assignment
Multiple assignment is just a combination of tuple packing and unpacking:
```python
x, y, z = 12345, 54321, 'hello!'
```

---

## Sets

**Sets** in Python are an **unordered collection of unique elements**. They are particularly useful for:
- Membership testing.
- Removing duplicate entries.
- Performing mathematical set operations like union, intersection, difference, and symmetric difference.


### Creation:
#### Using curly braces:
Use `{}` for non-empty sets.
```python
basket = {'apple', 'orange', 'banana'}
```

#### Using `set()` function:
For empty sets or dynamic construction.
```python
empty_set = set()
```

### Properties:

The order of elements is not guaranteed, **unordered**, contains only **unique elements**.
```python
basket = {'apple', 'orange', 'apple'}
print(basket)  # Output: {'orange', 'apple'}
```

### Membership Testing:
Fast testing using `in` or `not in`:
```python
'orange' in basket  # True
'grape' in basket   # False
```

### Mathematical Operations:

#### Union (`|`):
Combines all unique elements from both sets.  
Example:  
```python
set1 = {1, 2, 3}  
set2 = {3, 4, 5}  
result = set1 | set2  # {1, 2, 3, 4, 5}
```

#### Intersection (`&`):  
Common elements in both sets.  
Example:  
```python
set1 = {1, 2, 3}  
set2 = {3, 4, 5}  
result = set1 & set2  # {3}
```

#### Difference (`-`):  
Elements in the first set but not the second.  
Example:  
```python
set1 = {1, 2, 3}  
set2 = {3, 4, 5}  
result = set1 - set2  # {1, 2}
```

#### Symmetric Difference (`^`):  
Elements in either set but not both.  
Example:  
```python
set1 = {1, 2, 3}  
set2 = {3, 4, 5}  
result = set1 ^ set2  # {1, 2, 4, 5}
```

### Set Comprehensions:
Similar to list comprehensions, but for sets.
```python
a = {x for x in 'abracadabra' if x not in 'abc'}
print(a)  # Output: {'r', 'd'}
```

### Set Methods 

| **Method**               | **Description**                                              | **Return Type**  |
|--------------------------|--------------------------------------------------------------|------------------|
| `add(x)`                 | Adds an element `x` to the set.                              | `None`           |
| `remove(x)`              | Removes element `x` from the set. Raises `KeyError` if not present. | `None`           |
| `discard(x)`             | Removes element `x` if present; no error if absent.          | `None`           |
| `pop()`                  | Removes and returns an arbitrary element. Raises `KeyError` if empty. | Element Type     |
| `clear()`                | Removes all elements from the set.                           | `None`           |
| `copy()`                 | Returns a shallow copy of the set.                           | `set`            |
| `union(*others)` or `\|`  | Returns a new set with elements from the set and all others. | `set`            |
| `intersection(*others)` or `&` | Returns a new set with elements common to all sets.        | `set`            |
| `difference(*others)` or `-` | Returns a new set with elements in the set but not in others.  | `set`            |
| `symmetric_difference(other)` or `^` | Returns a new set with elements in either set but not both. | `set`            |
| `update(*others)` or `|=` | Updates the set with elements from others (union in-place).  | `None`           |
| `intersection_update(*others)` or `&=` | Updates the set with the intersection of itself and others. | `None`           |
| `difference_update(*others)` or `-=` | Updates the set by removing elements found in others. | `None`           |
| `symmetric_difference_update(other)` or `^=` | Updates the set with symmetric difference.            | `None`           |
| `issubset(other)`        | Checks if the set is a subset of another set.                | `bool`           |
| `issuperset(other)`      | Checks if the set is a superset of another set.              | `bool`           |
| `isdisjoint(other)`      | Checks if the set has no elements in common with another set. | `bool`           |

---


## Dictionaries

**Dictionaries** are **mutable, unordered collections** of key-value pairs where:
- **Keys**: Must be unique and immutable (e.g., strings, numbers, uples with immutable elements).
- **Values**: Can be of any data type and do not need to be unique.

Dictionaries are often referred to as "**associative arrays**" or "**hash maps**" in other programming contexts.


### Creation:
#### Empty Dictionary
Using `{}` or `dict()`

```python
empty_dict = {}
empty_dict = dict()
```

#### Non-empty Dictionary
Enclosing key-value pairs within `{}`. Or using `dict()` to create dictionary dynamically.
```python
tel = {'jack': 4098, 'sape': 4139}
dynamic_dict = dict(sape=4139, guido=4127, jack=4098)
a_dict = dict([('sape', 4139), ('guido', 4127), ('jack', 4098)])
```

### Basic Operations
- Adding/Updating: `d[key] = value` assigns a value to a key. Overwrites if the key exists.
- Deleting: `del d[key]` removes a key-value pair.
- Checking Existence: `key in d` checks if a key exists.

### Key Constraints
- Keys must be immutable (e.g., strings, numbers, tuples with immutable elements).
- Lists and other mutable types cannot be used as keys.

### Accessing Data
- Retrieve value by key: `d[key]`.
- Get all keys: `list(d)`.
- Get sorted keys: `sorted(d)`.

### Dictionary Comprehensions
Use expressions to create dictionaries dynamically:
```python
{x: x**2 for x in (2, 4, 6)}
# Output: {2: 4, 4: 16, 6: 36}
```


### Dictionary Methods

| **Method**                          | **Description**                                                                 | **Return Type**       |
|-------------------------------------|---------------------------------------------------------------------------------|-----------------------|
| `clear()`                           | Removes all key-value pairs from the dictionary.                                | `None`                |
| `copy()`                            | Returns a shallow copy of the dictionary.                                      | `dict`                |
| `fromkeys(iterable, value=None)`    | Creates a new dictionary with keys from the iterable and values set to `value`. | `dict`                |
| `get(key, default=None)`            | Returns the value for `key` if it exists; otherwise, returns `default`.         | Value Type or Default |
| `items()`                           | Returns a view object of key-value pairs.                                       | `dict_items`          |
| `values()`                          | Returns a view object of all values.                                            | `dict_values`         |
| `keys()`                            | Returns a view object of all keys.                                              | `dict_keys`           |
| `pop(key, default=None)`            | Removes the specified key and returns the corresponding value.                 | Value Type or Default |
| `popitem()`                         | Removes and returns the last inserted key-value pair as a tuple.               | `(key, value)` tuple  |
| `setdefault(key, default=None)`     | Returns the value for `key` if it exists; otherwise, inserts `key` with `default`. | Value Type           |
| `update([other])`                   | Updates the dictionary with key-value pairs from another dictionary or iterable. | `None`                |

---

## DefaultDict

Imagine that you're trying to count the words in a document. An obvious approach is to create a dictionary in which the keys are words and the values are counts. As you check each word, you can increment its count if it's already in the dictionary and add it to the dictionary if it's not:

```python
word_counts = {}
for word in document:
  if word in word_counts:
    word_counts[word] += 1
  else:
    word_counts[word] = 1
```

You could also use the “forgiveness is better than permission” approach and
just handle the exception from trying to look up a missing key:

```python
word_counts = {}
for word in document:
  try:
    word_counts[word] += 1
  except KeyError:
    word_counts[word] = 1
```

A third approach is to use get, which behaves gracefully for missing keys:
```python
word_counts = {}
for word in document:
  previous_count = word_counts.get(word, 0)
  word_counts[word] = previous_count + 1
```
Every one of these is slightly unwieldy, which is why defaultdict is useful. A defaultdict is like a regular dictionary, except that when you try to look up a key it doesn't contain, it first adds a value for it using a zero-argument function you provided when you created it. In order to use defaultdicts, you have to import them from collections:
```python
from collections import defaultdict
word_counts = defaultdict(int) # int() produces 0
for word in document:
  word_counts[word] += 1
```

They can also be useful with list or dict, or even your own functions:

```python
dd_list = defaultdict(list) # list() produces an empty list
dd_list[2].append(1) # now dd_list contains {2: [1]}

dd_dict = defaultdict(dict) # dict() produces an empty dict
dd_dict["Joel"]["City"] = "Seattle" # {"Joel" : {"City": Seattle"}}

dd_pair = defaultdict(lambda: [0, 0])
dd_pair[2][1] = 1 # now dd_pair contains {2: [0, 1]}
```
These will be useful when we're using dictionaries to “collect” results by some key and don't want to have to check every time to see if the key exists yet.


---

## Counter

A Counter turns a sequence of values into a defaultdict(int)-like object mapping keys to counts:
```python
from collections import Counter
c = Counter([0, 1, 2, 0]) # c is (basically) {0: 2, 1: 1, 2: 1}
```

This gives us a very simple way to solve our word_counts problem:
```python
# document is a list of words
word_counts = Counter(document) 
```

A Counter instance has a most_common method that is frequently useful:

```python
# print the 10 most common words and their counts
for word, count in word_counts.most_common(10):
  print(word, count)
```

---
## Looping Techniques

Python provides versatile tools for iterating over collections, enabling clear and concise iteration patterns for different use cases.

### `.items()`

Use the `.items()` method to loop through key-value pairs of a dictionary.
```python
knights = {'gallahad': 'the pure', 'robin': 'the brave'}
for k, v in knights.items():
    print(k, v)

# Output
gallahad the pure
robin the brave
```

### `enumerate(sequnce)`
Use the `enumerate()` function to get the index and corresponding value in a sequence.
```python
for i, v in enumerate(['tic', 'tac', 'toe']):
    print(i, v)

# Output
0 tic
1 tac
2 toe
```

The below are equivalents to above, but are not Pythonic way of doing it (doesn't follow the zen of python.)

```python
# Not Pythonic
for i in range(len(['tic', 'tac', 'toe'])): 
    print(f"word {i} is {word[i]}")

# Not Pythonic
i = 0
for word in ['tic', 'tac', 'toe']: 
    print(f"word {i} is {word}")
    i + =1 
```

### `zip()`
Use the `zip()` function to combine sequences element-wise and iterate over the paired results.
```python
questions = ['name', 'quest', 'favorite color']
answers = ['lancelot', 'the holy grail', 'blue']
for q, a in zip(questions, answers):
    print(f'What is your {q}? It is {a}.')

# Output
What is your name? It is lancelot.
What is your quest? It is the holy grail.
What is your favorite color? It is blue.
```
**Note**: if the lists are different lenghts, `zip` stops as soon as the first list ends. 


### `reversed(sequence)`
Use the `reversed()` function to loop over a sequence from the end to the beginning.
```python
for i in reversed(range(1, 10, 2)):
    print(i)

# Output
9
7
5
3
1
```


### `sorted()`
Use the `sorted()` function to loop through elements in ascending order without altering the original sequence.
```python
basket = ['apple', 'orange', 'apple', 'pear', 'orange', 'banana']
for i in sorted(basket):
    print(i)

# Output
apple
apple
banana
orange
orange
pear
```

### `sorted(set(sequnce))`
Combine `sorted()` with `set()` to remove duplicates and iterate in sorted order.
```python
for f in sorted(set(basket)):
    print(f)

# Output
apple
banana
orange
pear
```

## More on Conditions

In Python, conditions used in `while` and `if` statements can involve various operators beyond just comparisons.

### Membership Operators: `in` and `not in`

#### `in` Operator:
Checks if a value exists in a container. For example, 

```python
# Example with a list
fruits = ['apple', 'banana', 'cherry']
result = 'apple' in fruits  # True

# Example with a string
text = "Hello, World!"
result = 'Hello' in text  # True

# Example with a set
numbers = {1, 2, 3, 4, 5}
result = 3 in numbers  # True
```

#### `not in` Operator:
Checks if a value does not exist in a container. For example, 

```python
# Example with a list
fruits = ['apple', 'banana', 'cherry']
result = 'grape' not in fruits  # True

# Example with a string
text = "Hello, World!"
result = 'Python' not in text  # True

# Example with a set
numbers = {1, 2, 3, 4, 5}
result = 6 not in numbers  # True
```

### Identity Operators: `is` and `is not`

#### `is` Operator:
Checks if two variables refer to the same object in memory. For example, 
  
```python
x = [1, 2, 3]
y = x  # y references the same object as x
z = [1, 2, 3]  # z is a different object with the same values
result1 = x is y  # True
result2 = x is z  # False
```

#### `is not` Operator:
Checks if two variables do not refer to the same object in memory. For example, 

```python
x = [1, 2, 3]
y = [1, 2, 3]  # y is a different object with the same values as x
result = x is not y  # True

# Example with integers (small integers are cached by Python, so this may behave differently)
a = 100
b = 100
result = a is b  # True (both refer to the same cached object)
```

### Chained Comparisons
Comparisons can be chained together. For example:
```python
a < b == c
```
This checks if `a` is less than `b` **and** `a < b` equals `c`.


### Combining Comparisons with Boolean Operators: `and`, `or`, and `not`

#### Logical Operators 
- `and`, `or`, and `not` combine comparisons.
- `and` requires all conditions to be true.
- `or` requires at least one condition to be true.
- `not` negates a Boolean value.
  
#### Operator Precedence
- `not` has higher precedence than `and`, which has higher precedence than `or`.
- Parentheses can be used to control the evaluation order.
  
#### Short-Circuiting

- The evaluation stops as soon as the result is determined (left to right).
- For example, in `A and B and C`, if `B` is false, `C` isn't evaluated because the result is already false.
  
#### Return Value
The last evaluated argument is returned by `and` and `or` **when they are used as general values** (not just Booleans).
  

### Assigning Results of Comparisons
You can assign the result of a Boolean expression to a variable.
```python
string1, string2, string3 = '', 'Trondheim', 'Hammer Dance'
non_null = string1 or string2 or string3
print(non_null)  # Trondheim
```
The expression returns the **first non-empty value** from the sequence.
  
Consider this another construct: 
```python
s = some_function_that_returns_a_string()
if s:
  first_char = s[0]
else:
  first_char = ""
```
The above can be simplified using `and` operator: 
```python
first_char = s and s[0] # using 'short circuit' and 'returning' property
```

Similary: 
```python
safe_x = x or 0
```
Where `x` is checked for `None`. Alternatively: 
```python
safe_x = x if x is not None else 0
```

### `and()` and `any()`

Python has an all function, which takes an iterable and returns `True` precisely when every element is truthy, and an any function, which returns `True` when at least one element is truthy: 
```python
all([True, 1, {3}]) # True
all([True, 1, {}])  # False
any([True, 1, {}])  # True
all([])             # False
any([])             # False
```


### The Walrus Operator (`:=`)

The **walrus operator (`:=`)** allows you to assign a value to a variable as part of an expression. It is useful for reducing redundancy in code, especially in conditions or loops.

#### Example 1: Using `:=` in a `while` loop
```python
# Without walrus operator
n = 10
while n > 0:
    print(n)
    n -= 1

# With walrus operator
n = 10
while (n := n - 1) > 0:
    print(n)
```

#### Example 2: Using `:=` in an `if` condition
```python
# Without walrus operator
value = input("Enter a value: ")
if len(value) > 5:
    print(f"The input '{value}' has more than 5 characters.")

# With walrus operator
if (value := input("Enter a value: ")) and len(value) > 5:
    print(f"The input '{value}' has more than 5 characters.")
```

#### Example 3: Simplifying list comprehensions
```python
# Without walrus operator
numbers = [1, 2, 3, 4, 5, 6]
squared_even = [n * n for n in numbers if n % 2 == 0]

# With walrus operator
squared_even = [square for n in numbers if (square := n * n) and n % 2 == 0]
```

The **walrus operator** combines assignment and usage, making code cleaner and often more efficient!


## Comparing Sequences and Other Types

Python allows comparing sequences (like lists, tuples, and strings) with each other. The comparison follows **lexicographical order**.


### Lexicographical Ordering
Sequences are compared item by item. The **first pair of unequal items determines the comparison outcome**. If items are equal, the next items are compared, and so on. If one sequence is a prefix of the other (e.g., `[1, 2]` vs `[1, 2, 3]`), the shorter sequence is considered smaller.

Examples of comparisons:
- `(1, 2, 3) < (1, 2, 4)` (True)
- `('ABC' < 'C' < 'Pascal' < 'Python')` (True)
- `(1, 2, 3) == (1.0, 2.0, 3.0)` (True)

### Comparing Sequences with Different Types
- Sequences of different types can be compared if they have appropriate comparison methods (e.g., numbers). For example, `0 == 0.0`.
- If comparisons between unrelated types are attempted, Python raises a `TypeError`.


## `map()` Method in Python

The `map()` function in Python is a built-in function used to apply a function to every item in an iterable (like a list, tuple, or set) and return a map object (an iterator). It is particularly useful for transforming data in a concise and readable manner.

### Syntax:
```python
map(function, iterable, ...)
```
- **`function`**: A function to apply to each item in the iterable.
- **`iterable`**: An iterable like a list, tuple, etc. You can pass multiple iterables if the function accepts multiple arguments.

### Characteristics:
1. Returns a **map object**, which is **an iterator**.
2. You can convert the map object to a list, tuple, or other iterable types.
3. Works **efficiently with large datasets** because it **doesn't generate the entire result in memory (lazy evaluation)**.


### Example 1: Using `map()` with a single iterable
```python
# Function to square a number
def square(num):
    return num * num

numbers = [1, 2, 3, 4, 5]
result = map(square, numbers)

# Convert the map object to a list
print(list(result))  # Output: [1, 4, 9, 16, 25]
```

### Example 2: Using `map()` with a lambda function
```python
numbers = [1, 2, 3, 4, 5]
result = map(lambda x: x * x, numbers)
print(list(result))  # Output: [1, 4, 9, 16, 25]
```

### Example 3: Using `map()` with multiple iterables
```python
# Function to add two numbers
def add(a, b):
    return a + b

list1 = [1, 2, 3]
list2 = [4, 5, 6]
result = map(add, list1, list2)

# Convert the map object to a list
print(list(result))  # Output: [5, 7, 9]
```

### Example 4: Using `map()` with strings
```python
# Convert a list of strings to uppercase
names = ['alice', 'bob', 'charlie']
result = map(str.upper, names)
print(list(result))  # Output: ['ALICE', 'BOB', 'CHARLIE']
```

### Key Points:
- `map()` is often combined with `lambda` for inline, anonymous functions.
- For simple transformations, list comprehensions may be more Pythonic:
  ```python
  # Using list comprehension
  squared = [x * x for x in numbers]
  ```


# Modules

A **module** is a file (`.py` file) containing Python definitions (functions, variables, etc.) and statements. Modules facilitate the reuse of code without duplicating definitions in multiple programs. Modules enable:
- **Code reuse**: Functions or variables in a module can be used across multiple scripts or programs.
- **Organization**: Large programs can be split into smaller, manageable files.
- **Improved maintenance**: Changes in a single module reflect across all scripts importing it.

## What a Module Contains?
A Python module can include:
- **Executable Statements**: These run when the module is first imported or executed as a standalone script. These statements help initialize the module.
- **Function and Variable Definitions**: These are reusable components that other scripts can import and use.

Each module has its **own private namespace**, meaning the global variables within a module are not accessible directly by other scripts unless explicitly referenced.

## Creating a Module
A module is created by saving a Python script (`.py` file) with the desired functions and variables. For example, (`fibo.py`):
```python
# Fibonacci numbers module

def fib(n):
    """Prints Fibonacci series up to n."""
    a, b = 0, 1
    while a < n:
        print(a, end=' ')
        a, b = b, a + b
    print()

def fib2(n):
    """Returns a list of Fibonacci numbers up to n."""
    result = []
    a, b = 0, 1
    while a < n:
        result.append(a)
        a, b = b, a + b
    return result
```


## Importing Modules
To use a module in Python, it needs to be **imported** using the `import` statement:
```python
import module_name
```
When a module is imported:
- The module name is added to the current namespace.
- The functions and variables within the module are accessed using the **dot notation**.

```python
module_name.function_name(arguments)

# Example
import fibo
fibo.fib(1000)  # Calls the `fib` function from the `fibo` module
```
> **Note**
> Subsequent imports of the same module within the same session **do not reinitialize** it. Check [Efficiency Of Importing](#efficiency-of-importing)

---

## Accessing Module Functions
After importing a module, its functions and variables can be accessed using the dot operator `.`:
```python
>>> import fibo
>>> fibo.fib(100)   # Prints Fibonacci numbers up to 100
0 1 1 2 3 5 8 13 21 34 55 89
>>> fibo.fib2(50)   # Returns a list of Fibonacci numbers up to 50
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
```
The module name can be checked using the `__name__` attribute:
```python
>>> fibo.__name__
'fibo'
```

> **Note**: The statement, `import fibo.fib`, where `fib` is a method is **invalid**. When just `import` keyword is used, it can be accompanied by modules, submodules, or packages alone. 

---

## Assigning Module Functions to Local Names
A function from a module can be assigned to a local variable to simplify access:
```python
>>> fib = fibo.fib
>>> fib(200)  # Calls the `fib` function without using `fibo.`
0 1 1 2 3 5 8 13 21 34 55 89 144
```


## Importing Specific Components
To reduce namespace clutter, specific items can be imported from a module:
```python
from fibo import fib, fib2
fib(500)  # Directly calls the 'fib' function
```
Here, only `fib` and `fib2` are imported, and the module name `fibo` is not added to the local namespace.

## Importing All Names
Using `from module import *` imports all items from a module except those starting with an underscore (`_`):
```python
from fibo import *
fib(500)
```
**Drawback**: This practice can lead to namespace conflicts and less readable code. For example, it may unintentionally **hide** existing variables or functions.

## Using Aliases for Modules and Components

Modules and their components can be given alternative names using the `as` keyword. This is useful for simplifying long or frequently used names:
```python
import fibo as fib
fib.fib(500)  # Calls 'fib' from the module 'fibo'

from fibo import fib as fibonacci
fibonacci(500)  # Calls 'fib' with the alias 'fibonacci'
```

## Efficiency of Importing
A module is imported only **once per interpreter session** for efficiency. If the module code changes during the session, the **interpreter must be restarted** or the **module reloaded interactively**:
```python
import importlib
importlib.reload(fibo)
```


## Best Practices
- Use explicit imports (`from module import name`) to maintain clarity in your code.
- Avoid `from module import *` in production code to prevent namespace conflicts.
- Use aliases for long or frequently referenced module names to improve code readability.


## Executing Modules as Scripts
Python modules can act as both reusable components and standalone scripts. When executed as a script, the `__name__` variable of the module is set to `"__main__"`. This allows developers to add code specifically designed to run only when the module is executed directly, not when imported.

### Example 1: Basic Module Execution
Assume `fibo.py` contains:
```python
def fib(n):
  a, b = 0, 1
  while a < n:
      print(a, end=' ')
      a, b = b, a + b
  print()

if __name__ == "__main__":
  import sys
  fib(int(sys.argv[1]))

# when we run `$ python fibo.py 50` in command line:
0 1 1 2 3 5 8 13 21 34
```

Importing `fibo` in another script:
```python
import fibo
fibo.fib(30)
```
The `if __name__ == "__main__":` block is **not executed**. Only the `fib` function is available.

---

### Example 2: Testing Code
Modules often include test cases or examples under the `__main__` block. For instance:
```python
if __name__ == "__main__":
    print("Testing fib(10):")
    fib(10)

# Output:
Testing fib(10):
0 1 1 2 3 5 8
```
This makes it easy to validate functionality without affecting the module's behavior when imported.


### The Module Search Path

When importing a module, Python follows a specific search path to locate it. The interpreter searches the below in order:
#### 1. **Current Directory**: 
If the module is not built-in, Python looks in the directory of the script being executed (or the current working directory in interactive sessions).

**Example: Local Module Precedence**
Suppose the directory contains `math.py` with the following:
```python
def my_func():
    print("This is a custom math module!")


# Examlle
import math
math.my_func()
```
The local `math.py` will be imported instead of Python's standard library `math`.

---

#### 2. Environment Variable `PYTHONPATH`: 
You can define additional directories to include in the search path using `PYTHONPATH`.
```bash
export PYTHONPATH=/custom/modules
```
Python will include `/custom/modules` when searching for modules.

**Example: Custom Search Path**
Given `/custom/modules/util.py`:
```python
def greet():
    print("Hello from util!")
```
Running:
```bash
export PYTHONPATH=/custom/modules
```
And in Python:
```python
import util
util.greet()
```
Output:
```
Hello from util!
```

---

#### 3. **Built-in Modules**: 
Names like `os` or `sys` are built-in.
```python
import sys
print(sys.builtin_module_names)
```
Output:
```

('_ast', '_io', '_thread', ..., 'sys', ...)
```


#### 4. Installation-Dependent Defaults: 
These include standard library paths and the `site-packages` directory for third-party modules.


### Modifying the Module Search Path
The search path is stored in `sys.path`, a list of directories. You can inspect and modify it:
```python
import sys
print(sys.path)

# Adding a directory
sys.path.append('/additional/path')
```

**Example: Dynamically Adding a Path**
Suppose `/extra/modules` contains `extra.py`:
```python
def say_hello():
    print("Hello from extra!")
```

Adding it dynamically:
```python
import sys
sys.path.append('/extra/modules')
import extra
extra.say_hello()

# Outputs
Hello from extra!
```

### Important Considerations

#### Symlink Behavior: 
On systems supporting symlinks, When the symlink is used, the directory of the **resolved target** is used for the search path, not the directory containing the symlink. Basically, simlink itself is considered as directory. 

#### Precedence: 
The current directory takes precedence over standard libraries. Be cautious when naming local scripts, as they may shadow standard modules.

**Example: Shadowing Issue**
A local file named `random.py` could interfere with importing the standard library module:
```python
import random
```
Instead of Python's `random`, the local file will be used, possibly leading to errors.


### “Compiled” Python Files

Python employs a **caching mechanism** to speed up module loading by storing compiled versions of Python files (`.py`) in a special directory named `__pycache__`. These compiled files are identified by the `.pyc` extension and include metadata, such as the Python version used to compile them, ensuring compatibility across different versions and platforms.

#### How Compiled Python Files Work

##### Compilation and Caching:
- When a module is imported, Python compiles the `.py` file into bytecode and saves it as a `.pyc` file in the `__pycache__` directory.
- The compiled file is named using the format:  
 `module.version.pyc`  
 Example:
 - `spam.py` in Python 3.11 would be compiled and saved as:
   ```bash
   __pycache__/spam.cpython-311.pyc
   ```

##### Automatic Recompilation:
- Python automatically checks the modification date of the `.py` file against its cached `.pyc` counterpart.
- If the source file has been updated, Python recompiles it, replacing the cached version.

##### Platform Independence:
- Compiled files are architecture-independent, allowing them to be used across different systems as long as the Python versions match.


#### Scenarios Where Python Does Not Use the Cache

##### 1. Direct Execution:
- When a module is executed directly using:
 ```bash
 python module.py
 ```
 Python recompiles the file and does not store the resulting `.pyc`.

**Example**:
```bash
$ python spam.py
```
- The `spam.py` file will not have a cached `.pyc` in `__pycache__`.

##### 2. Missing Source File:
- If the `.py` file is not present and only the `.pyc` file exists, Python does not check the cache.

**Example: Distribution Without Source**:
- For deploying without source files:
 - Place the `.pyc` file in the same directory as the module.
 - Ensure the `.py` file is removed to prevent recompilation.

---

#### Optimizations with `.pyc` Files Using `-O` and `-OO` Flags:
- The `-O` flag removes `assert` statements.
- The `-OO` flag removes both `assert` statements and `__doc__` strings.

**Example**:
- Run Python with `-O`:
 ```bash
 python -O script.py
 ```
The resulting `.pyc` will be smaller and saved as:
 ```
 __pycache__/script.cpython-311.opt-1.pyc
 ```

- Run Python with `-OO`:
 ```bash
 python -OO script.py
 ```
The resulting `.pyc` will exclude even more information and will be named:
 ```
 __pycache__/script.cpython-311.opt-2.pyc
 ```

**Caution**:
- Removing `assert` and `__doc__` strings can cause issues in programs relying on these features.


#### Performance Insights: Loading Speed:
- Using `.pyc` files improves load time but does not enhance runtime performance.
- Programs read from `.py` files and `.pyc` files **execute at the same speed** because the execution is bytecode-based in both cases.


#### Advanced Tools and Techniques

1. **Creating `.pyc` Files Manually**:
   - Use the `compileall` module to precompile all modules in a directory.

   **Example**:
   ```bash
   python -m compileall /path/to/modules
   ```
   - This generates `.pyc` files for all `.py` files in the specified directory.

2. **Exploring Details in PEP 3147**:
   - Python's `.pyc` file caching mechanism is detailed in [PEP 3147](https://peps.python.org/pep-3147/), which includes a flowchart of how Python decides to recompile or use cached files.



## Standard Modules

Python's standard library is an extensive collection of modules that come bundled with the Python interpreter. These modules provide a wide range of functionality, from system-level access to high-level utilities, making Python a versatile language for diverse use cases. 

---

### Built-in Standard Modules

#### Definition and Scope:
Some modules are built into the Python interpreter for efficiency or to provide low-level access to operating system features. The availability of certain modules depends on the platform. For example, `winreg` module is exclusive to Windows.

#### Key Built-in Module: `sys`:
The `sys` module provides access to system-specific parameters and functions.

##### Example 1: Prompt Customization:
The `sys.ps1` and `sys.ps2` variables define the primary (`>>>`) and secondary (`...`) prompts in interactive mode.
```python
import sys
print(sys.ps1)  # Output: '>>>'
print(sys.ps2)  # Output: '...'

# Customizing the prompt
sys.ps1 = 'C> '
print(sys.ps1)  # Output: 'C> '
```

Interaction after setting `sys.ps1`:
```python
C> print('Hello, World!')
Hello, World!
C>
```

##### Example 2: Managing the Module Search Path:
The `sys.path` variable is a list of strings indicating the directories searched for modules. It can be modified to include custom paths dynamically.
```python
import sys
print(sys.path)  # Displays the default search paths
sys.path.append('/custom/path/to/modules')
```


## The `dir()` Function

The `dir()` function is a powerful tool for introspection, allowing users to list the names defined within a module, variable, or current namespace.

### Usage with Modules:
Lists all names (functions, variables, etc.) defined in a module.
```python
import fibo, sys
print(dir(fibo))  # Output: ['__name__', 'fib', 'fib2']
print(dir(sys))   # Outputs names defined in the `sys` module
```

### Usage Without Arguments:
Displays names defined in the **current namespace**.
```python
a = [1, 2, 3, 4, 5]
import fibo
fib = fibo.fib

print(dir())  
# Output: ['__builtins__', '__name__', 'a', 'fib', 'fibo', 'sys']
```

### Discovering Built-in Functions:
The `dir()` function **does not display built-in functions or variables** by default.Use the **`builtins`** module to access this list:
```python
import builtins
print(dir(builtins))
# Output includes names like 'abs', 'all', 'any', 'bin', 'bool', etc.
```

## Customization and Practical Scenarios

### Interactive Debugging:
Use `sys.ps1` and `sys.ps2` to create custom prompts in interactive Python sessions, **aiding in debugging and testing**. For example, you can change `PS1` and `PS2` variables when you are debugging or testing, to add a visual cue. 

### Custom Module Paths:
Dynamically add paths to `sys.path` to organize large projects or load modules from non-standard locations.
```python
import sys
sys.path.append('/my_project/lib')
```

### Exploring Modules:
Use `dir()` to explore the contents of unfamiliar modules interactively.
```python
import random
print(dir(random))  
# Explore the functions like 'choice', 'randint', 'shuffle', etc.
```

### Checking Current Namespace:
View all **currently defined names**, useful for managing the workspace in interactive sessions.
```python
x = 42
print(dir())  
# Output: ['__builtins__', '__name__', 'x']
```

---

# Packages

Python packages provide a way to organize and structure code into logical modules using "dotted module names." This organization helps developers manage larger projects, avoid name conflicts, and reuse code effectively. 

## What Are Packages?

**Definition**: A package is a collection of modules organized in directories that use a special `__init__.py` file to indicate they are Python packages.  
**Dotted Names**: Packages allow hierarchical access to modules via dotted module names, e.g., `package.submodule`.  

**Example**: In the package `A`, a submodule `B` can be accessed as `A.B`. This system is especially useful for large projects like `NumPy` or `Pillow`, where it prevents naming collisions across modules.


## Example: Sound Package

Let's consider a package for handling sound files and operations. Sound files come in various formats (`.wav`, `.aiff`, `.au`), and you might need functionalities like conversion, equalizing, or applying effects.

### File Structure:  
```plaintext
sound/                       # Top-level package
    __init__.py              # Initializes the sound package
    formats/                 # Subpackage for file format conversions
        __init__.py
        wavread.py           # Read .wav files
        wavwrite.py          # Write .wav files
        aiffread.py          # Read .aiff files
    effects/                 # Subpackage for sound effects
        __init__.py
        echo.py              # Add echo effect
        surround.py          # Add surround effect
    filters/                 # Subpackage for filters
        __init__.py
        equalizer.py         # Equalize audio
```

This structure organizes related functionalities into logical subdirectories.


## How Packages Work

### The `__init__.py` File:
Every package directory must contain an `__init__.py` file. It signals Python that the directory is a package. And, also Prevents accidental shadowing of modules with common directory names (e.g., `string`).

It can be empty:
```plaintext
__init__.py
```
Can also have initialization code:
```python
# sound/__init__.py
print("Initializing the sound package")
```
It can also set variables like `__all__`:
```python
# sound/effects/__init__.py
__all__ = ["echo", "surround"]
```

### Importing Modules**:
To use submodules, import them explicitly:
```python
import sound.effects.echo
sound.effects.echo.echofilter(input, output, delay=0.7, atten=4)
```
Use `from` for convenience:
```python
from sound.effects import echo
echo.echofilter(input, output, delay=0.7, atten=4)
```
Import specific functions or classes directly:
```python
from sound.effects.echo import echofilter
echofilter(input, output, delay=0.7, atten=4)
```

## Key Concepts

### Using `from package import item`
`item` can be a submodule (e.g., `echo`), or a function, class, or variable defined in the package.

For example, consider the content of the file `sound/effects/__init__.py`: 
```python
def initialize_effects():
    print("Effects initialized")
```

In another file, we can import it. 
```python
from sound.effects import initialize_effects
initialize_effects()
```

Python first looks for `initialize_effects` in the package. If not found, it checks for a module with that name.

---

### Using `import item.subitem.subsubitem`
In the above syntax, each `item` except the last must be a package. The last can **only be, a package or module**. 

**Invalid Example**:  
```python
import sound.effects.echo.some_function  # Error: `some_function` is not a module or package
```

---

## Advantages of Using Packages

1. **Avoid Naming Conflicts**:
   - Submodules in different packages can have the same name.
   - Example:
     ```plaintext
     sound/effects/echo.py
     video/effects/echo.py
     ```
     These can coexist without conflicts due to their distinct namespaces.

2. **Code Organization**:
   - Large codebases can be split into logically grouped subpackages.

3. **Reusability**:
   - Modules in packages can be reused in multiple projects.


## Examples in Action

1. **Importing Submodules**:
   ```python
   import sound.effects.echo
   sound.effects.echo.echofilter(input, output, delay=0.5, atten=2)
   ```

2. **Using `from` Imports**:
   ```python
   from sound.effects import echo
   echo.echofilter(input, output, delay=0.5, atten=2)
   ```

3. **Direct Function Import**:
   ```python
   from sound.effects.echo import echofilter
   echofilter(input, output, delay=0.5, atten=2)
   ```

4. **Mixing Submodules**:
   ```python
   from sound.effects import surround, echo
   surround.apply_surround(input)
   echo.echofilter(input, output)
   ```


## Import Best Practices

- Use specific imports:
  ```python
  from sound.effects.echo import echofilter
  ```
  This avoids namespace pollution and makes code more readable.

- Avoid wildcard imports (`*`):
  ```python
  from sound.effects import *
  ```
  - Can lead to unexpected behavior.
  - Only use if `__all__` is defined.

- Group related imports:
  ```python
  from sound.effects import echo, surround
  ```


## Importing `*` From a Package

The `from package import *` statement allows importing multiple submodules or names from a package into the current namespace. However, its behavior is nuanced, with potential caveats, limitations, and best practices. 


### How Does `from package import *` Work?

1. **Default Behavior**:
   - By default, `from package import *` does **not** automatically import all submodules from the package.
   - Instead, it:
     - Imports the package itself.
     - Executes any initialization code in the package's `__init__.py`.
     - Imports all names explicitly defined in the package's `__init__.py`.

2. **Defining `__all__`**:
   - Package authors can control what gets imported using `*` by defining a special list named `__all__` in the package's `__init__.py`.
   - `__all__` specifies the submodules or names that should be imported when `*` is used.

**Example**:  
In `sound/effects/__init__.py`:
```python
__all__ = ["echo", "surround", "reverse"]
```
Now, `from sound.effects import *` will import only the submodules `echo`, `surround`, and `reverse`.

---

### Why Avoid Automatically Importing All Submodules?

1. **Performance Concerns**:
   - Automatically searching the filesystem for submodules and importing them can be time-consuming.
   - This approach might also trigger unwanted side effects from the initialization code of submodules.

2. **Control and Intent**:
   - Importing all submodules might lead to **namespace pollution** and unintended behavior.
   - Explicit imports are preferable because they make the code more readable and predictable.

---

### Examples of Importing `*`

#### Example 1: Using `__all__`

Consider the following **Structure**:  
```plaintext
sound/
    __init__.py
    effects/
        __init__.py
        echo.py
        surround.py
        reverse.py
```

**Contents of `sound/effects/__init__.py`**:
```python
__all__ = ["echo", "surround"]
```

**Code**:
```python
from sound.effects import *
print(echo)      # Imported because it's in __all__
print(surround)  # Imported because it's in __all__
print(reverse)   # Error: Not imported, as it's not in __all__
```

#### Example 2: Shadowing Submodules

When a name defined in `__init__.py` conflicts with a submodule name, the local definition takes precedence.

**Contents of `sound/effects/__init__.py`**:
```python
__all__ = ["echo", "surround", "reverse"]

# Local function named `reverse`
def reverse(msg: str):
    return msg[::-1]
```

**Code**:
```python
from sound.effects import *
print(reverse("hello"))  # Outputs: "olleh" (uses the local function)
```

**Impact**:
- The local `reverse` function shadows the `reverse` submodule.
- The `reverse.py` submodule is not imported into the namespace.

---

#### Example 3: Without `__all__`

If `__all__` is not defined, `from package import *`:
- Does not import all submodules.
- Only imports names explicitly defined or loaded in `__init__.py`.

**Structure**:
```plaintext
sound/
    effects/
        __init__.py
        echo.py
        surround.py
```

**Contents of `sound/effects/__init__.py`**:
```python
# Initialization code
print("Initializing sound.effects package")

# Define a local variable
default_effect = "reverb"
```

**Code**:
```python
import sound.effects.echo
from sound.effects import *
print(default_effect)  # Works: Defined in __init__.py
print(echo)            # Error: Not imported
```

**Behavior**:
- Only `default_effect` is imported because it is defined in `__init__.py`.
- The `echo` module is not imported unless explicitly loaded beforehand.

---

### Best Practices

1. **Avoid `import *` in Production**:
   - It's considered bad practice due to potential namespace conflicts and reduced code readability.
   - Explicit imports (e.g., `from package.submodule import specific_function`) are preferred.

2. **Use `__all__` Judiciously**:
   - If `import *` must be supported, define `__all__` explicitly to control what gets imported.
   - Keep `__all__` updated with new submodules or names as the package evolves.

3. **Explicit Imports for Submodules**:
   - Import submodules explicitly to prevent unintended behavior.
   - Example:
     ```python
     from sound.effects import echo, surround
     echo.echofilter(input, output)
     surround.apply_surround(input)
     ```

4. **Use `import *` for Interactive Sessions Only**:
   - It can be convenient in interactive sessions or testing environments where brevity is desirable.


## Intra-package References

When working with Python packages, you may often need to reference submodules within the same package or sibling subpackages. Python offers two main types of imports for this purpose: **absolute imports** and **relative imports**.


### Absolute Imports:
Absolute imports refer to modules or submodules by their full path, starting from the root package. For example, in the package `sound`, if the module `sound.filters.vocoder` needs to use the `echo` module from `sound.effects`, it can use an absolute import like this:

```python
from sound.effects import echo
```
**Explanation**: This line imports the `echo` submodule from the `effects` subpackage, starting from the root `sound` package.

---

### Relative Imports:
Relative imports allow you to refer to other modules or submodules within the same package or its parent packages. These are useful when you're working within a nested package structure, as they allow for more concise and flexible imports. Relative imports use **leading dots** to refer to the current and parent packages. The **number of dots indicates the level of the package structure** to move up:
- A single dot (`.`) refers to the **current package**.
- Two dots (`..`) refer to the **parent package**.
- Three dots (`...`) would refer to the **grandparent package**, and so on.

### Examples:

#### Import from the Current Package:
If you're in the `surround` module within `sound.effects` and want to import the `echo` module from the same `effects` package, you can use:
```python
from . import echo
```
The single dot (`.`) indicates that `echo` is a sibling submodule in the same package (`sound.effects`).

#### Import from the Parent Package:
If you're in the `surround` module and want to access something from the `formats` subpackage (which is at the same level as `effects`), you would use:
 ```python
 from .. import formats
 ```
The two dots (`..`) indicate that `formats` is a sibling subpackage to `effects` and `surround`, but one level up in the package hierarchy.

#### Import from a Sibling Subpackage's Submodule:
To access `equalizer` from the `filters` subpackage, you can write:
```python
from ..filters import equalizer
```
The two dots (`..`) indicate moving one level up to `sound` and then into the `filters` subpackage to import `equalizer`.

---

### Important Note on Relative Imports:
- **Relative imports are based on the module's name** in the package structure. This means that they are typically used within modules that are part of a larger package or subpackage. 
- **Special Case for the Main Module**:
  - The main module, usually identified as **`"__main__"`, cannot use relative imports because it's not part of any package**. When running a script directly (e.g., `python myscript.py`), Python considers it the top-level module, and relative imports would not work.
  - In such cases, only **absolute imports** should be used to ensure proper module resolution.

---

### Multiple Directories

In some cases, a package may be distributed across **multiple directories**. Python supports this scenario using the special `__path__` attribute.

#### The `__path__` Attribute**:
 - The `__path__` attribute is a list initialized with the directory containing the package's `__init__.py` file.
 - This attribute is important because it defines where Python looks for submodules and subpackages when importing a package.
 - It can be modified to include additional directories, allowing you to extend the search path for modules within a package.

#### Extending the Package Search Path**:
 - By modifying `__path__`, you can make Python search for modules in multiple locations.
 - For example, if a package is split across two directories, you can modify `__path__` to include both directories. This is useful for large projects where the package's components may reside in different locations but still need to be considered part of the same logical package.

**Example**:
```python
# sound/__init__.py
__path__.append('/path/to/other/directory')
```
- This adds `/path/to/other/directory` to the package search path for the `sound` package, allowing Python to find and import submodules from that directory.

---

# Input and Output

## Fancier Output Formatting

### `str()` and `repr()` Functions

Both `str()` and `repr()` are used to convert objects into string representations, but they serve different audiences and purposes:

- **`str()`**: Designed for **humans**. It provides a readable and clean string suitable for display or end-user interaction.
- **`repr()`**: Designed for **developers**. It provides a detailed, unambiguous representation, often including information helpful for debugging or recreating the object.

#### Key Differences:
1. **Audience**:
   - `str()`: End-users, focusing on readability.
   - `repr()`: Developers, focusing on accuracy and detail.

2. **Purpose**:
   - `str()`: Makes objects look "nice" and easy to understand.
   - `repr()`: Shows a representation that could recreate the object when passed to `eval()` (in most cases).

#### Examples:

```python
# A simple string
s = 'Hello, world.'
print(str(s))   # Output: Hello, world.
print(repr(s))  # Output: 'Hello, world.'

# Notice how `repr()` adds quotes around the string
# and escapes special characters for clarity:
special = 'hello, world\n'
print(str(special))  # Output: hello, world
print(repr(special)) # Output: 'hello, world\\n'

# For more complex objects, the difference becomes clearer:
import datetime
now = datetime.datetime.now()
print(str(now))   # Output: 2025-01-09 12:34:56.789123 (friendly format)
print(repr(now))  # Output: datetime.datetime(2025, 1, 9, 12, 34, 56, 789123)
```

#### Usage Guidelines:
- Use **`str()`** when you need a **readable string** for end-users, such as in UI or logs.
- Use **`repr()`** when you need a **precise representation** for debugging, logging, or when working with developers. 

#### Rule of Thumb:
If you implement a custom object class, define both `__str__()` and `__repr__()` methods to ensure clear and meaningful string representations for different contexts.

### Formatted String Literals (f-strings)

Formatted string literals, or **f-strings**, are a powerful Python feature that enables embedding expressions within strings by prefixing the string with `f` or `F`. These expressions, enclosed in curly braces `{}`, are evaluated at runtime and inserted directly into the string. This method is concise, efficient, and offers advanced formatting capabilities.


####  Embedding Expressions in Strings
Any Python expression can be placed inside `{}` within an f-string. The expression is evaluated, and its result is included in the string.

```python
name = "Alice"
age = 30
f"My name is {name} and I am {age} years old."
# Output: 'My name is Alice and I am 30 years old.'
```

#### Using Format Specifiers
**Format specifiers** control the presentation of values, such as the number of decimal places, width, or type of alignment. To use a format specifier, include a colon (`:`) after the expression, followed by the desired specification.

**Example**: Rounding values
```python
import math
f"The value of pi is approximately {math.pi:.3f}."
# Output: 'The value of pi is approximately 3.142.'
```

**Example**: Aligning columns with minimum width
```python
table = {'Sjoerd': 4127, 'Jack': 4098, 'Dcab': 7678}
for name, phone in table.items():
    print(f'{name:10} ==> {phone:10d}')
# Output:
# Sjoerd     ==>       4127
# Jack       ==>       4098
# Dcab       ==>       7678
```
  - `{name:10}` ensures the `name` field is at least 10 characters wide.
  - `{phone:10d}` ensures the `phone` field is a 10-character wide integer.

---

#### Value Conversion Modifiers
F-strings allow modifying values before formatting:
- **`!a`**: Applies `ascii()` (produces ASCII-safe representations).
- **`!s`**: Applies `str()` (converts to a string).
- **`!r`**: Applies `repr()` (produces interpreter-readable representation).

```python
animals = 'eels'
f"My hovercraft is full of {animals}."
# Output: 'My hovercraft is full of eels.'

f"My hovercraft is full of {animals!r}."
# Output: "My hovercraft is full of 'eels'."
```

---

#### Self-Documenting Expressions with `=`
The `=` specifier automatically expands expressions to **include the expression itself, followed by its evaluated result**. This is useful for debugging or self-documenting code.

```python
bugs = 'roaches'
count = 13
area = 'living room'
f"Debugging {bugs=} {count=} {area=}"
# Output: "Debugging bugs='roaches' count=13 area='living room'"
```

---

#### Advanced Format Specifiers
F-strings use the same format specifications as the `str.format()` method. For a full reference, consult the `formatspec` documentation.

**Fixed-point formatting**:
```python
value = 123.45678
f"{value:.2f}"  # Output: '123.46'
```

**Zero-padding**:
```python
number = 42
f"{number:05d}"  # Output: '00042'
```

**Hexadecimal or binary**:
```python
num = 255
f"{num:#x}"  # Output: '0xff'
f"{num:#b}"  # Output: '0b11111111'
```

#### Formatting option for Floating Point Numbers

| **Modifier** | **Example**   | **Description**                                                                 |
|--------------|---------------|---------------------------------------------------------------------------------|
| **number**   | `:20d`        | Put the value in a field width of 20                                            |
| **<**        | `:<20d`       | Put the value in a field 20 characters wide, left-aligned                       |
| **>**        | `:>20d`       | Put the value in a field 20 characters wide, right-aligned                      |
| **^**        | `:^20d`       | Put the value in a field 20 characters wide, center-aligned                     |
| **0**        | `:020d`       | Put the value in a field 20 characters wide, fill in with leading zeros         |
| **.**        | `:20.2f`      | Put the value in a field 20 characters wide with 2 characters to the right of the decimal point |

---

#### Advantages of F-strings
1. **Concise and Readable**:
   - Embed variables and expressions directly into strings without additional function calls.
2. **Powerful Formatting**:
   - Provides granular control over presentation using format specifiers.
3. **Debugging Aid**:
   - The `=` specifier helps self-document code and debug variable values easily.
4. **Performance**:
   - Faster than alternatives like `str.format()` or string concatenation due to direct evaluation.

---

#### Comparison with Other Methods
- **F-strings**:
  ```python
  name = "Alice"
  f"My name is {name}."
  # Output: 'My name is Alice.'
  ```
- **`str.format()`**:
  ```python
  name = "Alice"
  "My name is {}.".format(name)
  # Output: 'My name is Alice.'
  ```
- **Concatenation**:
  ```python
  name = "Alice"
  "My name is " + name + "."
  # Output: 'My name is Alice.'
  ```

F-strings are generally preferred for their clarity and simplicity.

---

### The `str.format()` Method

The `str.format()` method in Python is a flexible way to format strings by substituting values into placeholders denoted by curly braces `{}`. It supports both positional and keyword arguments, allowing for advanced customization of string formatting.


#### Basic Usage

The placeholders `{}` in a string are replaced by the arguments passed to the `format()` method.

**Example:**
```python
print('We are the {} who say "{}!"'.format('knights', 'Ni'))
# Output: We are the knights who say "Ni!"
```

#### Positional Arguments

You can specify the order of substitution using numbers inside the curly braces.

**Default order**:
```python
print('{0} and {1}'.format('spam', 'eggs'))
# Output: spam and eggs
```

**Reversed order**:
```python
print('{1} and {0}'.format('spam', 'eggs'))
# Output: eggs and spam
```


#### Keyword Arguments

Keyword arguments are referenced by their names within the placeholders.

```python
print('This {food} is {adjective}.'.format(food='spam', adjective='absolutely horrible'))
# Output: This spam is absolutely horrible.
```


#### Mixing Positional and Keyword Arguments

You can combine positional and keyword arguments arbitrarily.

```python
print('The story of {0}, {1}, and {other}.'.format('Bill', 'Manfred', other='Georg'))
# Output: The story of Bill, Manfred, and Georg.

print('The story of {0}, {2}, and {other}.'.format('Bill', 'Manfred', other='Georg'))
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: Replacement index 2 out of range for positional args tuple
```

#### Formatting with Width and Alignment

The `str.format()` method allows precise control over spacing and alignment.

**Example: Formatting integers with aligned columns:**
```python
for x in range(1, 11):
    print('{0:2d} {1:3d} {2:4d}'.format(x, x*x, x*x*x))
# Output:
#  1    1     1
#  2    4     8
#  3    9    27
#  ...
# 10  100  1000
```
- `{0:2d}`: Ensures a width of 2 characters for the first value.
- `{1:3d}`: Ensures a width of 3 characters for the second value.
- `{2:4d}`: Ensures a width of 4 characters for the third value.

#### Accessing Values in Dictionaries

You can use dictionary keys as references within the placeholders:

**Using direct dictionary access:**
```python
table = {'Sjoerd': 4127, 'Jack': 4098, 'Dcab': 8637678}
print('Jack: {0[Jack]:d}; Sjoerd: {0[Sjoerd]:d}; Dcab: {0[Dcab]:d}'.format(table))
# Output: Jack: 4098; Sjoerd: 4127; Dcab: 8637678
```

**Using `**` to unpack the dictionary:**
```python
print('Jack: {Jack:d}; Sjoerd: {Sjoerd:d}; Dcab: {Dcab:d}'.format(**table))
# Output: Jack: 4098; Sjoerd: 4127; Dcab: 8637678
```


#### Using `vars()` for Local Variables

The `vars()` function returns **a dictionary of all local variables**. This can be used with `**` to dynamically format strings.

**Example:**
```python
x = 42
y = 'example'
table = vars()
print('x: {x}, y: {y}'.format(**table))
# Output: x: 42, y: example
```

#### Advantages of `str.format()`
1. **Flexibility**: Combine positional and keyword arguments.
2. **Readability**: Reference variables by name or position for clarity.
3. **Customizability**: Control width, alignment, and type-specific formatting (e.g., integers, floats).
4. **Dictionary Access**: Format strings using values from dictionaries, including dynamically generated ones.


#### Comparison with f-strings

| Feature                      | `str.format()`                                  | f-strings                       |
|------------------------------|-----------------------------------------------|--------------------------------|
| Basic Syntax                | `'{0}, {1}'.format(val1, val2)`               | `f"{val1}, {val2}"`           |
| Positional Arguments         | Supported                                     | Not directly supported        |
| Keyword Arguments            | Supported                                     | Supported                     |
| Accessing Dictionaries       | `'{key}'.format(**dict)`                     | `f"{dict['key']}"`            |
| Readability                  | Less concise                                 | More concise                  |
| Performance                  | Slower due to method calls                   | Faster due to direct evaluation |

---

### Manual String Formatting

Manual string formatting involves directly manipulating strings using methods like `rjust()`, `ljust()`, `center()`, and `zfill()` for precise control over layout and alignment. This approach does not involve placeholders like `str.format()` or f-strings but instead **relies on string methods** to create properly formatted output.


#### Right-Justifying with `str.rjust()`

The `rjust()` method aligns text to the right within a specified width by padding it with spaces on the left. 

```python
for x in range(1, 11):
    print(repr(x).rjust(2), repr(x * x).rjust(3), end=' ')
    print(repr(x * x * x).rjust(4))
# Output:
#  1   1    1
#  2   4    8
#  3   9   27
#  4  16   64
#  5  25  125
#  6  36  216
#  7  49  343
#  8  64  512
#  9  81  729
# 10 100 1000
```
- **`repr()`**: Ensures that numbers are converted to strings.
- **Alignment**: Columns are aligned using `rjust()`.


#### Left-Justifying with `str.ljust()`

The `ljust()` method aligns text to the left within a specified width by padding it with spaces on the right.

```python
print('Hello'.ljust(10) + 'World')
# Output: Hello     World
```


#### Centering with `str.center()`

The `center()` method centers text within a specified width, padding both sides with spaces.

```python
print('Python'.center(10))
# Output:   Python  
```

#### Zero-Padding with `str.zfill()`

The `zfill()` method pads a string on the left with zeros, and it recognizes signs (`+` or `-`) for numeric strings.

**Examples:**
```python
print('12'.zfill(5))          # Output: 00012
print('-3.14'.zfill(7))       # Output: -003.14
print('3.14159265359'.zfill(5))  # Output: 3.14159265359 (unchanged because it's longer than 5)
```


#### Truncating Strings

If you need a fixed width and truncation, you can use slicing in combination with `ljust()` or `rjust()`.

```python
print('Hello, world!'.ljust(10)[:10])
# Output: Hello, wo
```


#### Spaces Between Arguments in `print()`

The `print()` function automatically adds a space between arguments. To avoid extra spaces, use string concatenation or formatting.

```python
print('Hello', 'World')  # Output: Hello World
print('Hello' + 'World')  # Output: HelloWorld
print('Hello', 'World', sep="") # Output: HelloWorld
```
---

### Old String Formatting with the `%` Operator

Old-style string formatting in Python uses the `%` operator, also known as the modulo operator, to substitute values into a format string. This approach was prevalent before `str.format()` and f-strings were introduced. The `%` operator offers several format specifiers to control how values are inserted into a string.

```python
format % values
```
- **`format`**: A string containing placeholders.
- **`values`**: A single value or a tuple of values to replace the placeholders.

---

#### Placeholders and Specifiers

Placeholders are introduced with `%` (**format operator**) followed by format specifiers that define how the value will be formatted.

##### Common Format Specifiers
| Specifier | Meaning                         | Example Input | Example Output      |
|-----------|---------------------------------|---------------|---------------------|
| `%s`      | String                          | `'Python'`    | `Python`            |
| `%d` or `%i`     | Integer                         | `42`          | `42`                |
| `%f`      | Floating-point number           | `3.14159`     | `3.141590`          |
| `%x`      | Hexadecimal (lowercase)         | `255`         | `ff`                |
| `%X`      | Hexadecimal (uppercase)         | `255`         | `FF`                |
| `%e`      | Scientific notation (lowercase) | `12345.67`    | `1.234567e+04`      |
| `%E`      | Scientific notation (uppercase) | `12345.67`    | `1.234567E+04`      |
| `%c`      | Single character                | `65`          | `A` (ASCII 65)      |

##### Additional Format Options

| **Modifier** | **Example**   | **Description**                                                                 |
|--------------|---------------|---------------------------------------------------------------------------------|
| **number**   | `%20d`        | Put the value in a field width of 20                                            |
| **-**        | `%-20d`       | Put the value in a field 20 characters wide, left-justified                     |
| **+**        | `%+20d`       | Put the value in a field 20 characters wide, right-justified                    |
| **0**        | `%020d`       | Put the value in a field 20 characters wide, fill in with leading zeros         |
| **.**        | `%20.2f`      | Put the value in a field 20 characters wide with 2 characters to the right of the decimal point |
| **(name)**   | `%(name)d`    | Get the value from the supplied dictionary using name as the key                |
---

#### Examples of Basic Usage

**Substituting a Single Value**
```python
print('Hello, %s!' % 'world')
# Output: Hello, world!
```

**Multiple Values**
Use a tuple to pass multiple values:
```python
name = 'Alice'
age = 25
print('My name is %s, and I am %d years old.' % (name, age))
# Output: My name is Alice, and I am 25 years old.
```

**Floating-Point Numbers**
You can control the precision of floating-point numbers:
```python
import math
print('The value of pi is approximately %.2f.' % math.pi)
# Output: The value of pi is approximately 3.14.
```

#### Formatting with Width and Precision

The `%` operator allows specifying the width (minimum number of characters) and precision for numeric values.

**Syntax:**
```
%[flags][width][.precision]specifier
```

**Example: Width and Right-Justification**:
```python
print('Value: %5d' % 42)
# Output: Value:    42
```

**Example: Width with Zero-Padding**:
```python
print('Value: %05d' % 42)
# Output: Value: 00042
```

**Example: Floating-Point Precision**:
```python
print('Value: %.3f' % 3.14159)
# Output: Value: 3.142
```

**Example: Combining Width and Precision**:
```python
print('Value: %8.2f' % 3.14159)
# Output: Value:     3.14
```


#### Using `%s` for Strings

The `%s` specifier converts any value into a string.

```python
print('Name: %s' % 'Bob')
# Output: Name: Bob

print('List: %s' % [1, 2, 3])
# Output: List: [1, 2, 3]
```

#### Escape Characters

To include a literal `%` in the string, use `%%`:
```python
print('Discount: %d%%' % 20)
# Output: Discount: 20%
```


#### Limitations of `%` Formatting

- **Readability**: Formatting with `%` can become hard to read, especially with multiple placeholders.
  ```python
  print('Coordinates: (%d, %d)' % (10, 20))
  # Output: Coordinates: (10, 20)
  ```
- **Flexibility**: It lacks features like alignment and nested formatting available in `str.format()` and f-strings.


### Using the `Template` Class from the `string` Module:
Templates offer basic string substitution using placeholders like `$x`. Substitutions are made from a dictionary.

```python
from string import Template
t = Template('Total: $total, Discount: $discount')
t.substitute(total=100, discount=10)
# Output: 'Total: 100, Discount: 10'
```

---



## Reading and Writing Files

Python provides a straightforward way to handle file operations through the `open()` function. File handling is a critical feature for reading data from files and writing data to them. This section delves into the various modes, practices, and precautions when working with files in Python.

### `open()` Function

The `open()` function is the entry point for file operations. It returns a file object used to read, write, or manipulate the file.

```python
open(filename, mode, encoding=None)
```

- **`filename`**: Name of the file to open (string).
- **`mode`**: Describes the purpose of file access.
- **`encoding`**: Specifies the text encoding; recommended to use `"utf-8"` unless otherwise required.


### File Modes

The `mode` parameter determines how the file is opened. Below are the common modes:

| Mode | Description                                                                                   |
|------|-----------------------------------------------------------------------------------------------|
| `r`  | Read-only mode (default). The **file must exist**.                                                |
| `w`  | Write mode. Creates a new file or truncates an existing file.                                 |
| `a`  | Append mode. Writes data to the end of the file, creating it if it doesn't exist.             |
| `r+` | Read and write mode. The **file must exist**.                                                     |
| `b`  | Binary mode. Appends to `r`, `w`, or `a` to handle files as bytes objects (e.g., `rb`, `wb`). |


### Text Mode vs Binary Mode

#### Text Mode (Default)
- Reads and writes strings.
- Converts platform-specific line endings (in windows it is `\r\n`) to `\n` (reading) and back to platform-specific endings (writing).
- Suitable for text files like `.txt` or `.csv`.

#### Binary Mode
- Reads and writes data as bytes objects.
- Does not modify line endings.
- Essential for handling binary data like images (`.jpeg`), executables (`.exe`), or audio files.

### Using the `with` Keyword

The `with` statement is the preferred way to handle file objects. It ensures the file is automatically closed after its block is executed, even if an exception occurs.

```python
with open('example.txt', 'r', encoding='utf-8') as f:
    data = f.read()

print(f.closed)  # Output: True
```

**Advantages:**
1. Automatically closes the file after use.
2. Eliminates the need for explicitly calling `f.close()`.
3. Prevents resource leaks.

**Without `with`:**
```python
f = open('example.txt', 'r', encoding='utf-8')
data = f.read()
f.close()
```

### Writing to Files

Use the `write()` method to write strings or bytes to a file.

**Example: Writing Strings**
```python
with open('example.txt', 'w', encoding='utf-8') as f:
    f.write('Hello, World!\n')
```

**Precaution:** Always use `with` or ensure `f.close()` is called to flush data to disk properly.

**Example: Appending Data**
```python
with open('example.txt', 'a', encoding='utf-8') as f:
    f.write('Appending new line.\n')
```

### Reading from Files

Use methods like `read()`, `readline()`, or `readlines()` to read data from a file.

- **`read(size)`**: Reads the specified number of characters (or bytes in binary mode).
- **`readline()`**: Reads a single line. Includes the new line by default. 
- **`readlines()`**: Reads all lines and returns a list.

**Example: Reading Entire File**
```python
with open('example.txt', 'r', encoding='utf-8') as f:
    content = f.read()
print(content)
```

**Example: Reading Line by Line**
```python
with open('example.txt', 'r', encoding='utf-8') as f:
    for line in f:
        print(line.strip())
```

---

### Handling Closed Files

Once a file is closed (either manually or automatically with `with`), any operations on it will raise an error.

```python
f = open('example.txt', 'r')
f.close()
print(f.read())  # Raises ValueError: I/O operation on closed file
```


### Error Handling

Be cautious when handling files:
1. Use `with` to ensure proper cleanup.
2. Avoid hardcoding paths; use libraries like `os` or `pathlib` for path manipulations.
3. Handle exceptions using `try-except` blocks when necessary.

```python
try:
    with open('nonexistent.txt', 'r') as f:
        content = f.read()
except FileNotFoundError:
    print('File does not exist!')
```

### Summary of Good Practices

1. Always use the `with` statement for file operations.
2. Specify `encoding="utf-8"` for text files unless another encoding is required.
3. Use binary mode for non-text files.
4. Avoid performing operations on closed files.
5. Handle exceptions gracefully to avoid crashes.

### Methods of File Objects

File objects in Python provide numerous methods to interact with files effectively, whether reading, writing, or manipulating file positions.

### 1. Reading File Contents

#### `f.read(size)`
- Reads a specified quantity of data and returns it as a string (text mode) or a bytes object (binary mode).
- **`size`** (optional): Number of characters or bytes to read.
  - Omitted or negative: Reads the entire file.
  - Reaches the end of the file: Returns an empty string (`''`).

**Examples:**
```python
# Reading the entire file
with open('example.txt', 'r') as f:
    content = f.read()
print(content)

# Reading with a size limit
with open('example.txt', 'r') as f:
    print(f.read(10))  # Reads first 10 characters
    print(f.read(5))   # Reads next 5 characters

# Reading beyond the end of the file
with open('example.txt', 'r') as f:
    print(f.read())  # Reads the content
    print(f.read())  # Returns '' since end of the file is reached
```

#### `f.readline()`
- Reads one line from the file.
- Keeps the newline character (`\n`) at the end of the string unless the file doesn't end with one.
- Returns an empty string (`''`) if the end of the file is reached.

```python
with open('example.txt', 'r') as f:
    print(f.readline())  # First line
    print(f.readline())  # Second line
    print(f.readline())  # Returns '' if no more lines exist
```

**Handling Blank Lines:**
- A blank line is represented as `'\n'`.

`f.readline()` reads a single line from the file; a newline character (`\n`) is left at the end of the string, and is only omitted on the last line of the file if the file doesn't end in a newline. This makes the return value unambiguous; if `f.readline()` returns an empty string, the end of the file has been reached, while a blank line is represented by `\n`, a string containing only a single newline.

---

#### Reading Lines Efficiently
Iterating over a file object is an efficient and straightforward way to read lines.

```python
with open('example.txt', 'r') as f:
    for line in f:
        print(line.strip())  # Removes trailing newline
```

#### `f.readlines()` or `list(f)`
Reads all lines from a file and returns them as a list of strings.

```python
with open('example.txt', 'r') as f:
    lines = f.readlines()
print(lines)

with open('example.txt', 'r') as f:
    lines = list(f)
print(lines)
```

### Writing to Files

#### `f.write(string)`
- Writes the given string to the file.
- Returns the number of characters written.

```python
with open('example.txt', 'w') as f:
    num_chars = f.write('This is a test\n')
print(num_chars)  # Output: 15
```

#### Writing Non-String Objects
- Non-string objects must be converted to strings or bytes before writing.

```python
value = ('the answer', 42)
with open('example.txt', 'w') as f:
    f.write(str(value))  # Converts tuple to string
```

---

### File Positioning

#### `f.tell()`
- Returns the current position in the file.
- In binary mode: Number of bytes from the start.
- In text mode: An ???opaque value that represents the position.

```python
with open('example.txt', 'r') as f:
    print(f.read(10))  # Reads first 10 characters
    print(f.tell())    # Shows the position after 10 characters
```


#### `f.seek(offset, whence)`
- Changes the current position in the file.
- **`offset`**: Number of bytes/characters to move.
- **`whence`**: Reference point for movement.
  - `0`: Beginning of the file (default).
  - `1`: Current position.
  - `2`: End of the file.

**Examples:**
```python
# Binary mode example
with open('example.bin', 'wb+') as f:
    f.write(b'0123456789abcdef')  # Writes bytes

    f.seek(5)            # Move to the 6th byte
    print(f.read(1))     # Output: b'5'

    f.seek(-3, 2)        # Move 3 bytes before the end
    print(f.read(1))     # Output: b'd'

# Text mode example
with open('example.txt', 'w+') as f:
    f.write('Hello, World!')
    f.seek(0)            # Go to the start
    print(f.read(5))     # Reads 'Hello'
```

**Text Mode Restrictions:**
- Seeks relative to the beginning (`0`) are **only** allowed.
- Seeking beyond valid offsets produces undefined behavior.

---

### Miscellaneous Methods

#### `isatty()`
- Checks if the file object is connected to a terminal.
- Rarely used in general file handling.

#### `truncate(size)`
- Truncates the file to the specified size.
- If size is omitted, it truncates from the current position.

**Example:**
```python
with open('example.txt', 'w+') as f:
    f.write('This is a test.')
    f.truncate(10)  # Truncates to the first 10 characters
    f.seek(0)
    print(f.read())  # Output: 'This is a'
```

---

### Good Practices and Tips

1. **Iterating Over Files**: Use `for line in f` for efficient line-by-line reading.
2. **Avoid Reading Large Files Fully**: Use `f.read(size)` to limit memory usage.
3. **Always Close Files**: Use the `with` keyword to handle files automatically.
1. **Binary Data**: Use binary mode (`'rb'` or `'wb'`) for non-text files.
2. **Position Handling**: Use `tell()` and `seek()` for precise control over file navigation.

## Saving Structured Data with JSON

Python's `json` module provides an efficient way to serialize and deserialize data for saving and sharing structured data like lists, dictionaries, and nested objects. JSON (JavaScript Object Notation) is a widely used data interchange format, making it a great choice for interoperability.


### Understanding JSON Serialization and Deserialization

#### Serialization (Converting Python Objects to JSON)
- Serializing is the process of converting Python objects (like lists, dictionaries, or other data hierarchies) into a JSON string representation.
- This is helpful for saving data to files or transferring it over a network.

#### Deserialization (Converting JSON to Python Objects)
- Deserializing is the process of reconstructing Python objects from a JSON string.
- Useful for reading structured data stored in JSON format.

### Why Use JSON?
- Simplifies saving and retrieving complex data types like nested lists and dictionaries.
- Eliminates the need to manually parse and serialize data.
- JSON is widely supported, making it a great format for data exchange across applications and languages.

### Key Functions in the `json` Module

#### `json.dumps(obj)`
Serializes a Python object into a JSON string.

```python
import json

data = [1, 'simple', 'list']
json_string = json.dumps(data)
print(json_string)  # Output: '[1, "simple", "list"]'
```

#### `json.dump(obj, file)`
Serializes a Python object and writes it directly to a file.

```python
data = {'name': 'Alice', 'age': 30, 'is_member': True}

with open('data.json', 'w', encoding='utf-8') as f:
    json.dump(data, f)
```


#### `json.loads(json_string)`
Deserializes a JSON string into a Python object.

```python
json_string = '{"name": "Alice", "age": 30, "is_member": true}'
data = json.loads(json_string)
print(data)  # Output: {'name': 'Alice', 'age': 30, 'is_member': True}
```


#### `json.load(file)`
Deserializes JSON content from a file and reconstructs it into a Python object.

```python
with open('data.json', 'r', encoding='utf-8') as f:
    data = json.load(f)
print(data)  # Output: {'name': 'Alice', 'age': 30, 'is_member': True}
```

### Examples of Using JSON

#### Saving a Nested Dictionary
```python
nested_data = {
    "user": {
        "id": 1,
        "name": "John",
        "preferences": {
            "language": "English",
            "timezone": "UTC"
        }
    }
}

with open('user_data.json', 'w', encoding='utf-8') as f:
    json.dump(nested_data, f, indent=4)  # `indent` for pretty formatting
```

#### Reading and Modifying JSON Data
```python
with open('user_data.json', 'r', encoding='utf-8') as f:
    data = json.load(f)

# Modify the data
data['user']['preferences']['language'] = 'French'

# Save changes back to the file
with open('user_data.json', 'w', encoding='utf-8') as f:
    json.dump(data, f, indent=4)
```


### Important Notes
#### UTF-8 Encoding:
- JSON files must use UTF-8 encoding. Always specify `encoding="utf-8"` when opening files for reading or writing.

#### Handling Arbitrary Python Objects:
- JSON supports common data types like strings, numbers, lists, and dictionaries.
- Arbitrary Python objects (e.g., instances of custom classes) require additional effort to serialize.

**Example with Custom Serialization:**
```python
class User:
   def __init__(self, name, age):
       self.name = name
       self.age = age

def user_to_dict(user):
   return {'name': user.name, 'age': user.age}

user = User('Alice', 25)
json_string = json.dumps(user, default=user_to_dict)
print(json_string)  # Output: '{"name": "Alice", "age": 25}'
```

#### Comparison with `pickle`:
`pickle` is a protocol which allows serializing and deserializing arbitrarily complex **Python objects**. It converts Python objects into a byte stream (`pickling`) and back into objects (`unpickling`). It's useful for saving objects to files or transmitting them over networks.

- **Advantages of JSON**:
 - Language-independent: JSON can be used across different programming languages.
 - Safer: JSON doesn't execute arbitrary code during deserialization.
- **Advantages of `pickle`**:
 - Can serialize arbitrary Python objects, but it's Python-specific.
 - Less secure: Deserializing untrusted `pickle` data can execute malicious code.

**When to Use**:
- Use JSON for interoperability and when sharing data between different systems.
- Use `pickle` for Python-specific projects requiring more complex object serialization.

---

### Best Practices
1. **Always Close Files**:
   - Use `with` to ensure proper file handling.
   
   **Example:**
   ```python
   with open('data.json', 'r', encoding='utf-8') as f:
       data = json.load(f)
   ```

2. **Use `indent` for Readability**:
   - When saving JSON data to a file, use the `indent` parameter for pretty-printed output.

3. **Avoid Circular References**:
   - JSON serialization doesn't support circular references in data structures.

---

### Advanced Example: Logging JSON Data
```python
import json
import datetime

log_entry = {
    "timestamp": datetime.datetime.now().isoformat(),
    "event": "user_login",
    "details": {
        "user_id": 12345,
        "ip_address": "192.168.1.1"
    }
}

with open('log.json', 'a', encoding='utf-8') as f:
    json.dump(log_entry, f)
    f.write('\n')  # Add a newline for each log entry
```

---

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

# Classes

Classes allow **bundling data and functionality together** to create **new type** of objects. A class defines the structure and behavior of its instances, which can have attributes (to store data) and methods (to modify data or perform actions). Python's class system is relatively simple compared to other languages like C++ and Modula-3, yet it supports all the core features of Object-Oriented Programming (OOP).

### Class Features:
- **Inheritance:** A class can inherit from one or more base classes, allowing for method overrides and access to base class methods.
- **Data Members:** Class instances can contain arbitrary data, which can be modified by the class's methods. Coming from C++, all class memebers are **public**, and all methods are **virtual**. 
- **Dynamic Nature:** Classes in Python are created at runtime, and they can be modified after creation, providing flexibility.
- **Method Binding:** Methods have an explicit first argument (typically named `self`) which refers to the object instance calling the method, unlike C++ where the object is implicitly passed.

### Comparison with Other Languages:
- **C++ and Modula-3:** Python's class mechanism borrows features from both C++ and Modula-3, like supporting multiple base classes and redefining operators. Unlike C++, Python allows built-in types to be used as base classes.
- **Smalltalk:** In Python, classes themselves are objects, similar to how Smalltalk treats classes. This enables dynamic behaviors like renaming or importing classes at runtime.

### Aliasing in Python:
Multiple names can refer to the same object, a concept known as aliasing. This is often unnoticed with immutable objects (like numbers or strings), but it plays a significant role with mutable objects (like lists or dictionaries). Aliases behave like **pointers**.

Assignment do not copy data, they just bind names to objects. 
  
```python
a = [1, 2, 3]
b = a  # b is an alias for a
b[0] = 10  # Modifies the object a points to
print(a)  # Output: [10, 2, 3]
```

**Implications of Aliasing:**
- **Efficient Argument Passing:** When objects are passed to functions, only a reference (pointer) to the object is passed, making the process efficient. Changes to mutable objects inside functions affect the original object.
- **No Need for Multiple Argument Passing Mechanisms:** Unlike languages like Pascal that require separate mechanisms for passing by reference or value, Python's aliasing allows simple passing of objects.

## Python Scopes and Namespaces

In Python, **scopes** and **namespaces** are essential concepts for managing the visibility and accessibility of variables and objects in different parts of a program. 

### Namespaces
A **namespace** is essentially a mapping from names to objects. It determines which object corresponds to a given name in the current context. Common examples of namespaces include:
- **Built-in Namespace**: Contains names of built-in functions (e.g., `abs()`, `len()`) and exceptions.
- **Global Namespace**: Refers to the global variables defined at the module level.
- **Local Namespace**: Refers to the local variables inside a function.

Namespaces are typically **implemented as Python dictionaries**, though this detail is abstracted away for most users. Importantly, namespaces in different contexts are independent of each other. For example, two different modules may define a function `maximize`, but they will not conflict with each other because the function `maximize` belongs to different namespaces.

An **attribute** refers to a name following a dot notation (e.g., `z.real` where `real` is an attribute of object `z`). When accessing names in modules, such as `modname.funcname`, it is essentially an **attribute access**, where `modname` refers to a module object, and `funcname` is an attribute of that object.

Module objects have a secret read-only attribute called __dict__ which returns the dictionary used to implement the module's namespace; the name __dict__ is an attribute but not a global name. Obviously, using this violates the abstraction of namespace implementation, and should be restricted to things like post-mortem debuggers.

Attributes can be **read-only** or **writable**. For instance:
```python
modname.the_answer = 42  # writable attribute
del modname.the_answer   # delete the attribute
```

Each module get's their own **global** and **local** namespaces. If you execute Python script containing top level statements, then the name of the module `__name__` would be `__main__`. This `__main__` module will have it's own global and local namespace. Built-in functions like `print` and `len` reside in a separate module called builtins, which will again have it's own global and local namespace. 

#### Namespaces' Lifetime
- **Built-in Namespace**: Created when the Python interpreter starts up and exists throughout the program's execution (never deleted).
- **Global Namespace**: Created when a module is imported and persists until the interpreter quits (stays as long as built-in).
- **Local Namespace**: Created when a function is called and destroyed when the function returns or raises an unhandled exception.

Recursive function calls will create a **new local namespace** for each call, meaning each invocation has its own local namespace.

### Scopes
A **scope** is a region in the program where a namespace is directly accessible. The scope determines where a variable or function can be accessed. Python uses **static scoping**. There are four types of scopes, which Python searches in the following order:
1. **Innermost Scope (Local scope)**: The current function or block where the name is accessed.
2. **Enclosing Function Scopes**: The scopes of any functions that enclose the current function.
3. **Global Scope**: The global namespace of the current module.
4. **Built-in Scope**: The scope containing built-in names like `abs()` and `len()`.

Python resolves names dynamically at runtime by searching these scopes from the innermost to the outermost. If a variable is not found in the innermost scope, Python checks progressively more outer scopes.

#### Global and Nonlocal Declarations
- The `global` keyword tells Python that a variable should be bound to the **global scope** (module level). This means that assignments to that variable will modify the global variable, not create a local one.
  - You cannot create a global variable, if it doesn't exists (exists, imply that at least a reference of the varialbe should be present) in global scope. 
- The `nonlocal` keyword tells Python that a variable is in an **enclosing scope** (i.e., not the local or global scope), and any assignment to this variable will modify the variable in that enclosing scope, rather than creating a new local variable.

Without these keywords, assignments will always create variables in the innermost scope.

Consider the following example, which demonstrates how Python's scoping rules affect variable assignments and how `global` and `nonlocal` work:

```python
def scope_test():
    def do_local():
        spam = "local spam"  # Creates a local variable
    def do_nonlocal():
        nonlocal spam
        spam = "nonlocal spam"  # Modifies the variable in the enclosing scope
    def do_global():
        global spam
        spam = "global spam"  # Modifies the global variable
    
    spam = "test spam"
    do_local()
    print("After local assignment:", spam)  # "test spam", because local assignment didn't affect this scope
    do_nonlocal()
    print("After nonlocal assignment:", spam)  # "nonlocal spam", because nonlocal affects the enclosing scope
    do_global()
    print("After global assignment:", spam)  # "nonlocal spam", nonlocal assignment doesn't change global spam

scope_test()
print("In global scope:", spam)  # "global spam", because global assignment changed the global variable
```

**Output:**
```
After local assignment: test spam
After nonlocal assignment: nonlocal spam
After global assignment: nonlocal spam
In global scope: global spam
```

- **Local Assignment**: The assignment to `spam` within `do_local()` does not affect the `spam` variable in the outer `scope_test()` function, because the assignment creates a new local variable specific to `do_local`.
- **Nonlocal Assignment**: The assignment to `spam` inside `do_nonlocal()` affects the `spam` variable in the `scope_test` function, as `nonlocal` refers to the nearest enclosing scope.
- **Global Assignment**: The `global` keyword modifies the variable `spam` in the global namespace, making the change visible outside the function, in this case, in the global scope after `scope_test()` finishes.

### Key Points to Remember:
- **Namespaces** are mappings from names to objects, and there are multiple types of namespaces in Python: built-in, global, and local.
- **Scopes** define where names are directly accessible, and Python searches them dynamically in a set order: local, enclosing, global, and built-in.
- The `global` and `nonlocal` keywords control whether variables refer to the global or enclosing scopes, respectively, rather than being confined to the local scope.
- Assignments in Python do not copy data but bind names to objects in the current scope.

## A first look at classes

**Classes** in Python brings new syntax, object types, and semantics. It enables users to create custom types that can model real-world entities by encapsulating data and functionality.

### 1. Class Definition Syntax
A class is defined using the `class` keyword followed by a class name and a colon. The body of the class can contain statements, including function definitions and other code. Here's the basic syntax:
```python
class ClassName:
    <statement-1>
    .
    .
    .
    <statement-N>
```
- **Execution Order**: Like function definitions, class definitions must be executed before they have any effect. A class definition doesn't define a class until it's actually run.
- **Placement**: You can place a class definition inside functions or conditionals, just like any other statement.
  
**Example:**
```python
if some_condition:
    class MyClass:
        def greet(self):
            print("Hello!")
```
This will only define `MyClass` if `some_condition` is `True`. The scope of the class is restricted to the conditional construct. 

Inside a class, **function definitions** (methods) are common, but you can also use other statements, like variable assignments or print statements, although it is less common. When a class definition is entered:
- A **new namespace** is created for the class.
- Function definitions within the class bind function names in this new namespace.
  
When the class definition ends, a **class object** is created. This class object is a wrapper around the class's namespace, and it's bound to the class name given in the definition (e.g., `MyClass`).

**Example:**
```python
class MyClass:
    i = 12345
    def f(self):
        return 'hello world'
```
In this example, when `MyClass` is defined:
- `MyClass.i` will reference the integer `12345`.
- `MyClass.f` will reference the method `f(self)`.

### 2. Class Objects
Once the class is defined, it can be treated like an object, and **class objects** support two operations:
1. **Attribute References**: Access class attributes and methods using the standard attribute syntax `obj.name`.
2. **Instantiation**: Creating an instance (object) of the class using function notation.

**Example:**
```python
class MyClass:
    i = 12345
    def f(self):
        return 'hello world'

print(MyClass.i)  # Accessing class attribute
print(MyClass.f)  # Accessing class method (this is a function object)
```

### 3. Instantiating a Class
Class instantiation works like calling a function. When you call a class (e.g., `MyClass()`), it creates an **instance** of the class.

```python
x = MyClass()  # Create a new instance of MyClass
```
This creates a new **instance object** that is assigned to the variable `x`. At this point, `x` is an instance of `MyClass`.

### 4. The `__init__()` Method
Many classes want to initialize their instances with custom state. The `__init__()` method is the **initializer** method (constructor) for the class. When a class defines an `__init__()` method, Python automatically calls this method after creating an empty object during instantiation.

- `__init__()` is a special method in Python, and it can take parameters to initialize the object's state.
  
**Example:**
```python
class MyClass:
    def __init__(self):
        self.data = []  # Initialize an empty list for the instance

x = MyClass()  # Create an instance of MyClass
print(x.data)  # Outputs: []
```
In this example, when `x` is instantiated, the `__init__()` method initializes the `data` attribute as an empty list.

### 5. `__init__()` with Arguments
You can make the `__init__()` method more flexible by accepting arguments. These arguments are passed during instantiation and can be used to customize the object's initial state.

**Example:**
```python
class Complex:
    def __init__(self, realpart, imagpart):
        self.r = realpart
        self.i = imagpart

x = Complex(3.0, -4.5)  # Create an instance with specified arguments
print(x.r, x.i)  # Outputs: 3.0 -4.5
```
In this example, the `Complex` class represents complex numbers with `realpart` and `imagpart`. The `__init__()` method takes these as arguments and initializes the instance attributes `r` (real part) and `i` (imaginary part).

---

### Key Takeaways:
- **Class Definition**: Uses the `class` keyword. A new namespace is created for the class, and when the definition finishes, a class object is created and bound to the class name.
- **Class Attributes**: Variables and methods defined inside a class are part of the class's namespace and are accessed using `ClassName.attribute`.
- **Class Instantiation**: A new instance is created by calling the class object like a function (`x = MyClass()`).
- **`__init__()` Method**: A special method for initializing new objects with custom state when they are created.
- **Arguments to `__init__()`**: You can pass arguments to `__init__()` during instantiation to set up the instance's initial state.

Classes encapsulate both data (attributes) and behavior (methods) into a single entity, allowing for better organization and abstraction in programming.


## Magic Methods

Magic methods are methods that start with double underscores, they are also called "dunder" (double underscore). Any member of a class that start with double score are private members, and hence shouldn't be used outside of the class. Note, Python will not stop you even if you did use them outside class. There are many such dunder methods available for Python classes. Here is a table contain some of them: 

| **Category**       | **Method**                     | **Description**                                                                                                   |
|---------------------|---------------------------------|-------------------------------------------------------------------------------------------------------------------|
| **Initialization** | `__init__`                     | Constructor, initializes an instance of a class.                                                                 |
|                     | `__new__`                     | Called to create a new instance of a class before `__init__`.                                                    |
| **Object Representation** | `__str__`              | Returns a string representation for `str()` and `print()`.                                                       |
|                     | `__repr__`                    | Returns an official string representation of an object, often used for debugging.                                |
|                     | `__format__`                  | Defines custom string formatting behavior with `format()`.                                                       |
|                     | `__bytes__`                   | Converts the object to bytes using `bytes()`.                                                                    |
| **Comparison**      | `__eq__`                      | Defines behavior for the equality operator `==`.                                                                 |
|                     | `__ne__`                      | Defines behavior for the inequality operator `!=`.                                                               |
|                     | `__lt__`                      | Defines behavior for the less-than operator `<`.                                                                 |
|                     | `__le__`                      | Defines behavior for the less-than-or-equal-to operator `<=`.                                                    |
|                     | `__gt__`                      | Defines behavior for the greater-than operator `>`.                                                              |
|                     | `__ge__`                      | Defines behavior for the greater-than-or-equal-to operator `>=`.                                                 |
| **Arithmetic**      | `__add__`                     | Defines behavior for addition `+`.                                                                               |
|                     | `__sub__`                     | Defines behavior for subtraction `-`.                                                                            |
|                     | `__mul__`                     | Defines behavior for multiplication `*`.                                                                         |
|                     | `__matmul__`                  | Defines behavior for matrix multiplication `@`.                                                                  |
|                     | `__truediv__`                 | Defines behavior for division `/`.                                                                               |
|                     | `__floordiv__`                | Defines behavior for floor division `//`.                                                                        |
|                     | `__mod__`                     | Defines behavior for modulus `%`.                                                                                |
|                     | `__pow__`                     | Defines behavior for exponentiation `**`.                                                                        |
|                     | `__radd__`, `__rsub__`...     | Right-hand versions of arithmetic methods (e.g., `__radd__` for `b + a`).                                        |
|                     | `__iadd__`, `__isub__`...     | In-place versions of arithmetic methods (e.g., `__iadd__` for `+=`).                                             |
| **Unary Operations**| `__neg__`                     | Defines behavior for unary negation `-self`.                                                                     |
|                     | `__pos__`                     | Defines behavior for unary positive `+self`.                                                                     |
|                     | `__abs__`                     | Defines behavior for `abs(self)`.                                                                                |
|                     | `__invert__`                  | Defines behavior for bitwise NOT `~self`.                                                                        |
| **Type Conversion** | `__int__`                     | Converts an object to an integer using `int()`.                                                                  |
|                     | `__float__`                   | Converts an object to a float using `float()`.                                                                   |
|                     | `__complex__`                 | Converts an object to a complex number using `complex()`.                                                        |
|                     | `__bool__`                    | Converts an object to a boolean using `bool()`.                                                                  |
| **Attribute Access**| `__getattr__`                 | Called when accessing a missing attribute.                                                                       |
|                     | `__getattribute__`            | Called for all attribute accesses.                                                                               |
|                     | `__setattr__`                 | Called when setting an attribute.                                                                                |
|                     | `__delattr__`                 | Called when deleting an attribute.                                                                               |
|                     | `__dir__`                     | Called by `dir()` to list attributes.                                                                            |
| **Container Emulation** | `__len__`                | Returns the length of an object using `len()`.                                                                   |
|                     | `__getitem__`                 | Called to retrieve an item using `obj[key]`.                                                                     |
|                     | `__setitem__`                 | Called to set an item using `obj[key] = value`.                                                                  |
|                     | `__delitem__`                 | Called to delete an item using `del obj[key]`.                                                                   |
|                     | `__iter__`                    | Returns an iterator object using `iter(obj)`.                                                                    |
|                     | `__next__`                    | Returns the next item from an iterator.                                                                          |
|                     | `__contains__`                | Implements membership testing with `in`.                                                                         |
| **Callable Objects**| `__call__`                    | Makes an instance callable like a function.                                                                      |
| **Context Managers**| `__enter__`                   | Defines setup behavior for context management using `with`.                                                      |
|                     | `__exit__`                    | Defines cleanup behavior for context management using `with`.                                                    |
| **Descriptors**     | `__get__`                     | Defines behavior for attribute access in descriptors.                                                            |
|                     | `__set__`                     | Defines behavior for setting a value in descriptors.                                                             |
|                     | `__delete__`                  | Defines behavior for deleting a value in descriptors.                                                            |
| **Other Special Methods** | `__hash__`            | Returns the hash value for an object using `hash()`.                                                             |
|                     | `__del__`                     | Called when an object is about to be destroyed.                                                                  |
|                     | `__sizeof__`                  | Returns the size of an object in memory using `sys.getsizeof()`.                                                 |
|                     | `__copy__`                    | Defines behavior for shallow copies.                                                                             |
|                     | `__deepcopy__`                | Defines behavior for deep copies.                                                                                |
|                     | `__index__`                   | Converts an object to an integer for use as a sequence index.                                                    |

---


## Instance Objects

Instance objects in Python represent individual objects created from a class. They can hold attributes (both data and methods) that can be accessed or modified, enabling unique behavior and state for each object.

### 1. Instance Attributes: Data Attributes
- **Data Attributes** are similar to “instance variables” in languages like Smalltalk or “data members” in C++. They are attributes unique to each instance of a class and are created when first assigned, similar to local variables.
- **Dynamic Creation**: You don't need to declare data attributes in advance. They are created on-the-fly when you assign them to an instance.

**Example:**
```python
class MyClass:
    def __init__(self):
        self.name = "Ram"

x = MyClass()
x.counter = 1  # Creating the 'counter' data attribute dynamically
while x.counter < 10:
    x.counter = x.counter * 2
print(x.counter)  # Output: 16
del x.counter  # Deleting the attribute
```
- In this example:
  - `x.counter` is dynamically created and initialized to `1`.
  - The while loop modifies `x.counter` and eventually prints `16`.
  - The `del x.counter` line removes the attribute from the instance.

### 2. Instance Attributes: Methods
- **Methods** are functions that "belong" to an instance object. They are essentially bound functions that can operate on the instance's data and are defined within the class.
- **Calling Methods**: When calling a method on an instance (e.g., `x.f()`), the method behaves like a normal function, but with one special feature: the **instance object** (`x`) is automatically passed as the **first argument** (usually named `self`).

**Example:**
```python
class MyClass:
    def greet(self):
        return "Hello, world!"

x = MyClass()
print(x.greet())  # Output: Hello, world!
```
- `greet(self)` is a method of the class. When called on `x`, `x` is passed as the `self` argument.

### 3. Method Objects
- **Method Object**: When referencing a method without calling it (e.g., `x.f`), Python returns a "method object," which is a function that has already been bound to the instance.
- You can store this method object and call it later. The method still knows which instance it is bound to.

**Example:**
```python
class MyClass:
    def greet(self):
        return "Hello, world!"

x = MyClass()
xf = x.greet  # Storing the method object
while True:
    print(xf())  # Continuously prints "Hello, world!"
```
- Here, `xf` is a method object bound to the `x` instance. Calling `xf()` prints `"Hello, world!"` indefinitely.

> Here is something cool, you make x.f point to some other function!

### 4. Calling Methods
- When calling a method like `x.f()`, Python translates this into a function call with the instance as the first argument: `MyClass.f(x)`.
- **Method Binding**: The method is a function that is bound to the instance (`x`) and is called with the instance (`x`) as the first argument.

**Example:**
```python
class MyClass:
    def greet(self, name):
        return f"Hello, {name}!"

x = MyClass()
print(x.greet("Alice"))  # Output: Hello, Alice!
```
- Here, the call `x.greet("Alice")` is internally translated to `MyClass.greet(x, "Alice")`, where `x` is passed as the first argument (`self`).

### 5. Class and Instance Variables
- **Instance Variables**: These are attributes unique to each instance, defined inside the `__init__()` method. They store data that can vary from one instance to another.
  
- **Class Variables**: These are shared across all instances of the class. They are **defined within the class but outside the `__init__()` method**. They are useful for storing data that is common to all instances.

**Example of Class and Instance Variables:**
```python
class Dog:
    kind = 'canine'  # class variable shared by all instances

    def __init__(self, name):
        self.name = name  # instance variable unique to each instance

# Creating instances of Dog
d = Dog('Fido')
e = Dog('Buddy')

# Accessing class variables
print(d.kind)  # Output: canine
print(e.kind)  # Output: canine

# Accessing instance variables
print(d.name)  # Output: Fido
print(e.name)  # Output: Buddy
```
- `kind` is a **class variable** shared by all instances, while `name` is an **instance variable**, unique to each `Dog` object.

### 6. Mutable Objects in Class Variables
- **Pitfall with Mutable Class Variables**: If you use mutable objects (like lists or dictionaries) as class variables, they will be shared among all instances. This can lead to unintended behavior.

**Example of Shared Class Variables with Mutable Objects:**
```python
class Dog:
    tricks = []  # class variable (shared across all instances)

    def __init__(self, name):
        self.name = name

    def add_trick(self, trick):
        self.tricks.append(trick)

# Creating instances of Dog
d = Dog('Fido')
e = Dog('Buddy')
d.add_trick('roll over')
e.add_trick('play dead')

print(d.tricks)  # Output: ['roll over', 'play dead']
print(e.tricks)  # Output: ['roll over', 'play dead']
```
- Here, the `tricks` list is shared across all instances, meaning that adding a trick for one `Dog` instance affects all instances. This is usually not the desired behavior.

### 7. Correct Design with Instance Variables
To avoid the shared mutable object issue, it's better to use instance variables to store mutable data. Each instance will then have its own separate list or dictionary.

**Correct Design with Instance Variables:**
```python
class Dog:
    def __init__(self, name):
        self.name = name
        self.tricks = []  # instance variable (unique to each instance)

    def add_trick(self, trick):
        self.tricks.append(trick)

# Creating instances of Dog
d = Dog('Fido')
e = Dog('Buddy')
d.add_trick('roll over')
e.add_trick('play dead')

print(d.tricks)  # Output: ['roll over']
print(e.tricks)  # Output: ['play dead']
```
- Now each instance (`d` and `e`) has its own `tricks` list, and adding tricks for one instance does not affect the other.

---

### Key Takeaways:
- **Instance Variables** are unique to each instance and are created when first assigned, whereas **class variables** are shared by all instances of the class.
- **Methods** are functions bound to instance objects, and they can be called with the instance automatically passed as the first argument.
- **Method Objects**: Methods can be stored and called later, just like function objects.
- **Pitfall with Mutable Class Variables**: Mutable objects like lists or dictionaries should not be used as class variables if they are meant to be unique to each instance.

## Some Remarks

Let's look at some important points regarding attributes, methods, and conventions in Python classes. Looking into the behavior of instance and class attributes, method conventions, and some additional aspects related to how Python handles classes and objects.

### 1. Instance vs. Class Attributes
- **Priority of Instance Attributes**: If an attribute with the same name exists in both the instance and the class, the instance attribute takes priority during attribute lookup.

**Example:**
```python
class Warehouse:
    purpose = 'storage'  # Class attribute
    region = 'west'      # Class attribute

w1 = Warehouse()
print(w1.purpose, w1.region)  # Output: storage west

w2 = Warehouse()
w2.region = 'east'  # Overriding the 'region' attribute at the instance level
print(w2.purpose, w2.region)  # Output: storage east
```
- Here, `w2.region` is overridden at the instance level, so it prints `'east'` while the class attribute `purpose` remains `'storage'`.

### 2. Data Attributes and Methods
- **Access to Data Attributes**: Data attributes are accessible both by methods within the class and by users (clients) of the object. However, Python does not enforce **data hiding** (like private attributes in other languages). It's up to conventions to ensure safe usage.
  
- **Data Integrity**: Methods maintain control over the state of an object, and clients can add data attributes to an instance. However, if the client overwrites data attributes, it may break invariants or assumptions made by the methods.

**Example:**
```python
class Counter:
    def __init__(self):
        self.count = 0  # Instance data attribute
    
    def increment(self):
        self.count += 1

    def reset(self):
        self.count = 0

c = Counter()
c.increment()
print(c.count)  # Output: 1
c.count = 100  # Client can modify data attribute directly
print(c.count)  # Output: 100
```
- The client can overwrite the `count` attribute, potentially disrupting the intended behavior of the `increment` and `reset` methods.

### 3. No Shorthand for Accessing Data Attributes
- Python does not provide shorthand syntax for accessing instance variables from within methods. This design choice improves code readability and reduces confusion between local variables and instance variables. 
- If you want to access instance variables, you will have to use `self` key word. 
**Example**: 
```python
class MyClass: 
    def __init__(self):
        self.variable_1 = 1

    def a_method(self): 
        variable_1 = 2 # local variable
        self.variable_1 = 2 # instance variable
```

### 4. The `self` Convention
- **The `self` argument**: The first argument of a method is conventionally named `self`. This is just a naming convention, and **Python doesn't enforce it**. However, following this convention improves the readability and maintainability of the code, especially for others working with your code or using code analysis tools.

**Example:**
```python
class Person:
    def __init__(self, name):
        self.name = name  # 'self' refers to the instance of the object
    
    def greet(self):
        return f"Hello, {self.name}!"

p = Person('Alice')
print(p.greet())  # Output: Hello, Alice!
```
- `self` is a reference to the instance of the class and allows methods to access instance variables.

### 5. Function Objects as Methods
- A **function object** can be assigned as a class attribute and will become a method for instances of that class. This can be done even if the function is defined outside the class.

**Example:**
```python
# Function defined outside the class
def f1(self, x, y):
    return min(x, x + y)

class C:
    f = f1  # Assigning the function as a method
    def g(self):
        return "Hello, World!"

h = C.g  # Method 'g' assigned to variable 'h'
print(h(C()))  # Output: Hello, World!
```
- Here, `f1` is assigned to `f` inside the class `C`, and `f1` becomes a method of `C`. Similarly, `h` is assigned `C.g` and can be called as `h()`.

### 6. Calling Methods within Other Methods
- **Method Calling**: Methods can call other methods by **using `self`** to reference other methods within the same class.

**Example:**
```python
class Bag:
    def __init__(self):
        self.data = []
    
    def add(self, x):
        self.data.append(x)
    
    def addtwice(self, x):
        self.add(x)  # Calling 'add' method
        self.add(x)  # Calling 'add' method again

b = Bag()
b.addtwice(5)
print(b.data)  # Output: [5, 5]
```
- In the `addtwice` method, the `add` method is called twice to add the same value `5` to the `data` list.

### 7. Global Names in Methods
- Methods can reference **global variables** in the same way as functions. The global scope is the module containing the method definition, but the class itself is not considered part of the global scope.

??? Do we access global variables using `global` keyword?

**Example:**
```python
x = 10  # Global variable

class MyClass:
    def print_x(self):
        print(x)  # Accessing the global variable x

obj = MyClass()
obj.print_x()  # Output: 10
```
- In this case, `x` is a global variable accessed by the `print_x` method of `MyClass`.

### 8. Object Classes and Types
- Every object in Python is an instance of a **class** (also called its **type**). This can be accessed via the `__class__` attribute, which returns the class of the object.

??? does `type()` method use `__class__` internally?
**Example:**
```python
class MyClass:
    pass

obj = MyClass()
print(obj.__class__)  # Output: <class '__main__.MyClass'>
```
- Here, `obj.__class__` returns the class type of `obj`, which is `MyClass`.

---

### Key Takeaways:
- **Instance vs. Class Attributes**: Instance attributes take priority over class attributes when they share the same name.
- **Data Hiding**: Python doesn't enforce data hiding; it's up to conventions to ensure safe access to attributes.
- **Self Convention**: The `self` parameter is a naming convention in method definitions that helps clarify the instance to which the method belongs.
- **Methods Calling Other Methods**: Methods can call other methods within the same class using the `self` object.
- **Global Scope**: Methods can access global variables but typically operate in the module's scope.

## Inheritance 

### 1. Basic Inheritance Syntax
Inheritance is a core feature of object-oriented programming that allows a class (derived class) to inherit properties and behaviors (methods) from another class (base class). In Python, a class is defined as a derived class by specifying the base class(es) in parentheses:

**Syntax:**
```python
class DerivedClassName(BaseClassName):
    <class-body>
```

- The base class name (`BaseClassName`) must be defined in the same namespace where the derived class is defined. In case the base class is defined in another module, the fully qualified name (including the module name) can be used.
  
**Example:**
```python
class Animal:
    def speak(self):
        return "Animal sound"

class Dog(Animal):  # Derived class from Animal
    def speak(self):
        return "Woof"
    
dog = Dog()
print(dog.speak())  # Output: Woof
```
In this example, `Dog` inherits from `Animal`. The method `speak()` is overridden in the `Dog` class.

### 2. Attribute Lookup in Inheritance
When an attribute (or method) is requested from an instance, Python looks for it in the derived class first. If it's not found, the search continues up the inheritance chain to the base class, and so on, until the attribute is found or the search reaches the top of the chain.

- **Method Resolution Order (MRO)**: This mechanism ensures that the correct method is invoked when a method is called. Python follows a depth-first, left-to-right approach for attribute lookup.

**Example:**
```python
class A:
    def speak(self):
        return "A speaks"
        
class B(A):
    def speak(self):
        return "B speaks"
        
class C(B):
    pass  # C does not override speak

c = C()
print(c.speak())  # Output: B speaks
```
Here, `C` inherits from `B`, and `B` overrides the `speak()` method from `A`. Since `C` doesn't override `speak()`, the method from class `B` is called.

### 3. Overriding Methods
In Python, a method in a derived class can **override** a method in the base class. This means that the derived class can define its own version of the method, replacing the one from the base class.

**Example:**
```python
class Animal:
    def sound(self):
        return "Animal sound"
        
class Dog(Animal):
    def sound(self):
        return "Woof"
        
dog = Dog()
print(dog.sound())  # Output: Woof
```
In this case, `Dog` overrides the `sound()` method from `Animal`. When `dog.sound()` is called, it uses the version from `Dog`, not from `Animal`.

### 4. Calling Base Class Methods
Sometimes, a derived class might want to **extend** (rather than completely replace) the functionality of a method from the base class. In such cases, it can call the method from the base class using `super().method(self, ...)`.

**Example:**
```python
class Animal:
    def sound(self):
        return "Animal sound"
        
class Dog(Animal):
    def sound(self):
        return super().sound() + " and Woof"  # Calling base class method
        
dog = Dog()
print(dog.sound())  # Output: Animal sound and Woof
```
Here, `Dog` extends `sound()` from `Animal` by calling the base class method with `super()`, and appending additional behavior.

### 5. The `isinstance()` Function
Python provides the built-in function `isinstance()` to check whether an object is an instance of a given class or a subclass of it.

**Example:**
```python
class Animal:
    pass

class Dog(Animal):
    pass

d = Dog()
print(isinstance(d, Dog))  # Output: True
print(isinstance(d, Animal))  # Output: True
```
- `isinstance(d, Dog)` returns `True` because `d` is an instance of `Dog`.
- `isinstance(d, Animal)` also returns `True` because `Dog` is a subclass of `Animal`.

#### 6. The `issubclass()` Function
`issubclass()` checks whether a class is a subclass of another class. It returns `True` if the first class is a subclass of the second.

**Example:**
```python
print(issubclass(Dog, Animal))  # Output: True
print(issubclass(Dog, str))     # Output: False
```
- `issubclass(Dog, Animal)` returns `True` because `Dog` is a subclass of `Animal`.
- `issubclass(Dog, str)` returns `False` because `Dog` is not a subclass of `str`.

### 7. Multiple Inheritance
Python supports **multiple inheritance**, meaning a derived class can inherit from more than one base class. The derived class inherits attributes and methods from all its base classes. The syntax for defining a class with multiple base classes is as follows:

**Syntax:**
```python
class DerivedClassName(Base1, Base2, Base3):
    <class-body>
```

In this case, Python uses a **left-to-right, depth-first** search to find attributes and methods in the classes, ensuring that if an attribute is not found in the derived class, it is searched for in the base classes in the specified order.

**Example:**
```python
class A:
    def speak(self):
        return "A speaks"
        
class B:
    def greet(self):
        return "Hello from B"
        
class C(A, B):  # Multiple inheritance
    pass

c = C()
print(c.speak())  # Output: A speaks
print(c.greet())  # Output: Hello from B
```
- `C` inherits from both `A` and `B`. It can access methods from both parent classes.

### 8. Method Resolution Order (MRO) in Multiple Inheritance
In multiple inheritance, the **Method Resolution Order (MRO)** determines the order in which the classes are searched for attributes and methods. This order ensures that each class in the inheritance chain is only accessed once, and that classes are not revisited during the search.

Python uses a **dynamic algorithm** to calculate the MRO, which is based on the **C3 Linearization** algorithm. This allows for cooperative multiple inheritance, meaning that methods from parent classes can be called in a predictable order.

**Example with Diamond Problem:**
```python
class A:
    def method(self):
        print("Method from A")
        
class B(A):
    def method(self):
        print("Method from B")
        
class C(A):
    def method(self):
        print("Method from C")
        
class D(B, C):  # D inherits from B and C
    pass

d = D()
d.method()  # Output: Method from B
```
- In this example, `D` inherits from both `B` and `C`. The MRO ensures that the method from `B` is called first, not `C`, even though both `B` and `C` inherit from `A`. This is a result of the C3 linearization of the MRO.

### 9. Dynamic Changes in MRO
The MRO can be checked at runtime using the `mro()` method or the `__mro__` attribute of a class.

**Example:**
```python
class D(B, C):
    pass

print(D.mro())  # Output: [<class '__main__.D'>, <class '__main__.B'>, <class '__main__.C'>, <class '__main__.A'>, <class 'object'>]
```
- This shows the order in which Python will look for methods when they are called on an instance of `D`.

### Key Takeaways:
- **Basic Inheritance** allows a class to inherit methods and attributes from a base class.
- **Overriding Methods** enables derived classes to replace the behavior of base class methods.
- **Method Resolution Order (MRO)** ensures the correct method is called in cases of multiple inheritance.
- **Multiple Inheritance** allows a class to inherit from multiple base classes, with Python handling the complexity of the MRO.
- Python provides built-in functions like `isinstance()` and `issubclass()` to check types and class hierarchies.

## Private Variables

In Python, the concept of **private variables** does not exist in the same way as in many other object-oriented programming languages like Java or C++. Instead, Python follows conventions and uses a technique called **name mangling** to provide limited support for private variables. Here's a detailed explanation of how private variables work in Python, with examples.

### 1. No True Private Variables
In Python, there are no actual "private" instance variables that are completely inaccessible from outside the object. Any instance variable (or method) can be accessed by code outside the class if the variable or method is private.

However, Python follows a **convention** to indicate that certain variables should be treated as "private." This convention is based on the use of **a leading underscore (`_`)** in the variable or method name. The underscore is a signal to developers that the variable or method is intended for internal use within the class and should not be accessed directly from outside the class. This is not enforced by Python, but it helps maintain clean code and prevents accidental misuse.

**Example:**
```python
class MyClass:
    def __init__(self):
        self._private_variable = 42  # Conventionally private
        
obj = MyClass()
print(obj._private_variable)  # Not an error, but should not be done
```
In this example, `_private_variable` is conventionally private, but Python will not stop you from accessing it. It's just considered "non-public" and subject to change without notice.

### 2. Name Mangling for Private Variables
Python provides a feature called **name mangling** to support a limited form of private variables. This is useful when you want to avoid name clashes between class members, especially in cases involving inheritance and subclasses.

If a variable is prefixed with **at least two leading underscores** and **at most one trailing underscore** (e.g., `__variable`), Python automatically **mangles** the name by internally renaming it to include the class name. This prevents accidental overrides or clashes with names in subclasses.

- **Name mangling** replaces an identifier like `__variable` with a new name that incorporates the class name.
- This prevents subclasses from inadvertently overriding the variable or method in the base class.

**Example:**
```python
class MyClass:
    def __init__(self):
        self.__private_variable = 100
        
obj = MyClass()
# Accessing __private_variable directly will raise an AttributeError
# print(obj.__private_variable)  # AttributeError: 'MyClass' object has no attribute '__private_variable'

# However, name mangling allows access through the mangled name
print(obj._MyClass__private_variable)  # Output: 100
```
Here, `__private_variable` is name-mangled to `_MyClass__private_variable`. While this doesn't make it truly private, it **makes accidental access more difficult** by altering the variable's name internally.

### 3. Why Name Mangling is Useful
Name mangling primarily helps avoid **name conflicts** in the case of inheritance. When you have a base class and subclasses, name mangling ensures that attributes or methods that are supposed to be private to a class will not be accidentally overridden by subclasses with the same name.

**Example with Inheritance:**
```python
class Mapping:
    def __init__(self, iterable):
        self.items_list = []
        self.__update(iterable)  # Private method
        
    def update(self, iterable):
        for item in iterable:
            self.items_list.append(item)
    
    __update = update  # Private copy of the original update method

class MappingSubclass(Mapping):
    def update(self, keys, values):
        # This method overrides the parent method update, but does not affect __update
        for item in zip(keys, values):
            self.items_list.append(item)

# Create an instance of MappingSubclass
obj = MappingSubclass([1, 2, 3])

# The update method from MappingSubclass works without breaking the base class
obj.update([4, 5, 6])

# Accessing the original __update method through name mangling
print(obj._Mapping__update([7, 8, 9]))  # Works because of name mangling
```
In this example:
- The `Mapping` class defines a method `update()` and stores a private copy of it as `__update` using name mangling.
- The `MappingSubclass` overrides the `update()` method, but the `__update` method from the base class remains intact due to name mangling. The base class method is accessed using `_Mapping__update`.
- This allows `MappingSubclass` to add its own `update()` method without breaking the original functionality of `Mapping`.

### 4. Limited Privacy and Debugging
Even though Python provides name mangling, **privacy** is not strictly enforced. It is still possible to access or modify a mangled variable, which can be useful for debugging or special cases where direct access is needed. However, this should be done with caution.

**Example:**
```python
class MyClass:
    def __init__(self):
        self.__private_var = 50

obj = MyClass()
# Directly accessing the mangled name
print(obj._MyClass__private_var)  # Output: 50
```
While this is technically allowed, directly accessing a mangled variable defeats the purpose of making it private, and it can lead to unintended consequences if the variable name changes.

### 5. Considerations in Special Cases
- **`exec()` and `eval()`**: Code executed using `exec()` or `eval()` does not follow the same name-mangling rules because the invoking class is not considered the current class in that scope. This means that the mangling will not apply to code executed in this manner, which could result in unexpected behaviors.
  
**Example:**
```python
class MyClass:
    def __init__(self):
        self.__private_var = 100

# Using eval() to access the private variable will not apply name mangling
print(eval("obj.__private_var"))  # This will raise an AttributeError
```

- **`getattr()`, `setattr()`, and `delattr()`**: These functions do not apply name mangling when accessing or modifying attributes dynamically. Therefore, they can be used to access or modify a private variable if you know the mangled name.

**Example:**
```python
class MyClass:
    def __init__(self):
        self.__private_var = 200

obj = MyClass()

# Using getattr() to access the private variable via name mangling
print(getattr(obj, "_MyClass__private_var"))  # Output: 200
```

- **`__dict__`**: The `__dict__` attribute of a class or object provides a dictionary of all attributes, including private ones. You can directly manipulate private variables through `__dict__`, but this is also not recommended for regular code.

**Example:**
```python
print(obj.__dict__)  # Output: {'_MyClass__private_var': 200}
```

### 6. Key takeaways
- **Private variables** in Python are not truly private but are instead indicated through naming conventions (using `_` for non-public variables).
- **Name mangling** allows limited privacy, mainly to avoid name conflicts in inheritance scenarios. It helps prevent accidental overrides of private methods or attributes in subclasses.
- Python's approach to private variables is more about **convention** than enforcement, and it relies on developers respecting the intended privacy rather than strict language features.

## Odds and Ends

Let's look at some additional, useful Python concepts, including the idiomatic approach to creating simple data types using **dataclasses**, the concept of **abstract data types**, and details about **instance methods**. Here's a breakdown of these topics with examples to illustrate each concept.

### 1. Using Dataclasses for Bundling Data

In Python, a common task is bundling together a few related data items, which is similar to the "record" in Pascal or "struct" in C. The idiomatic way to handle such data structures in Python is to use **dataclasses**.

A **dataclass** is a Python class that is specifically designed to store data without having to write explicit methods for initialization, representation, and comparison. It is part of Python's `dataclasses` module, introduced in Python 3.7. A `dataclass` automatically generates boilerplate code for the class, making it much easier to create simple data types.

**Example of a Dataclass:**

```python
from dataclasses import dataclass

@dataclass
class Employee:
    name: str
    dept: str
    salary: int

# Creating an instance of the Employee class
john = Employee('john', 'computer lab', 1000)

# Accessing attributes
print(john.dept)    # Output: 'computer lab'
print(john.salary)  # Output: 1000
```

- **Explanation:**
  - The `@dataclass` decorator automatically adds an `__init__()` method, which initializes the attributes of the class (in this case, `name`, `dept`, and `salary`).
  - It also generates the `__repr__()` method, which provides a readable string representation of the instance, making debugging easier.
  - Additionally, it generates methods for comparison (`__eq__`, `__lt__`, etc.) so that instances of the `Employee` class can be compared based on their attributes.

This is an efficient and Pythonic way to represent simple objects that just need to hold data, similar to structs or records in other languages.

### 2. Emulating Abstract Data Types with Classes

Sometimes, you may need to write code that expects a certain abstract data type (ADT). Rather than creating an entirely new class that implements the ADT from scratch, you can use an existing class that **emulates** the expected methods of that ADT.

For instance, if you have a function that is designed to handle file-like objects (such as reading data from files), but you want to pass a string buffer instead of a file, you can create a class that implements the required file-like methods (`read()` and `readline()`), and pass this class to the function.

**Example of Emulating a File-like Object:**

```python
class StringBuffer:
    def __init__(self, data: str):
        self.data = data
        self.index = 0

    def read(self):
        # Read the entire string
        return self.data

    def readline(self):
        # Return the string up to the first newline character
        if self.index < len(self.data):
            line = self.data[self.index:self.data.find("\n", self.index) + 1]
            self.index += len(line)
            return line
        return ''

# Function that expects a file-like object
def print_file_content(file_obj):
    print(file_obj.read())

# Creating an instance of StringBuffer, which is a "file-like" object
buffer = StringBuffer("Hello, world!\nThis is a test.")

# Passing the StringBuffer object to a function that expects a file object
print_file_content(buffer)  # Output: Hello, world!
```

- **Explanation:**
  - The `StringBuffer` class implements `read()` and `readline()`, mimicking the behavior of a file object, even though it operates on an in-memory string.
  - This demonstrates Python's flexibility in allowing classes to emulate behaviors of abstract data types. The function `print_file_content` does not care whether the argument is a real file object or a string buffer as long as it has the expected methods.

This technique can be useful when you want to write functions that work with a variety of objects, as long as they implement a specific interface (i.e., set of methods).

### 3. Instance Method Objects and Their Attributes

In Python, **instance methods** are bound methods. When you call an instance method on an object, Python automatically passes the instance as the first argument to the method (typically named `self`).

An instance method object has several attributes that you can access, such as:
- `m.__self__`: The object instance to which the method is bound.
- `m.__func__`: The original function object (without the `self` argument) that corresponds to the method.

These attributes can be useful in certain situations, such as introspection or debugging.

**Example:**

```python
class MyClass:
    def greet(self):
        print(f"Hello from {self.__class__.__name__}")

# Creating an instance
obj = MyClass()

# Accessing the method and its attributes
method = obj.greet
print(method.__self__)  # Output: <__main__.MyClass object at 0x7f1f9c2c6c40>
print(method.__func__)  # Output: <function MyClass.greet at 0x7f1f9c2c6d30>

# Calling the method
method()  # Output: Hello from MyClass
```

- **Explanation:**
  - `method.__self__` gives you the instance of the object (`obj` in this case) that the method is bound to.
  - `method.__func__` provides the function object `greet`, which is the original method before it was bound to the instance.

This can be helpful if you need to analyze or manipulate the method's behavior or the instance it is bound to.

#### 4. Key Points
- **Dataclasses** provide an easy and efficient way to define classes that store simple data. They automatically generate methods like `__init__()`, `__repr__()`, and comparison methods.
- Python allows classes to **emulate abstract data types** by providing the required methods, making it possible to use custom objects in places where standard data types like file objects are expected.
- **Instance methods** have special attributes such as `__self__` (the bound instance) and `__func__` (the original function), which can be useful for introspection and advanced use cases.

This section provides useful techniques for handling data and methods efficiently in Python.

## Iterators

Let's look at **iterators**, and then explaining how Python's `for` loops work and how to create custom iterators in classes. Iterators are an essential part of Python that unify the process of accessing elements in containers (like lists, tuples, strings, etc.) in a consistent and convenient manner. This section discusses how Python handles iteration and shows you how to define your own iterators.

### 1. Iteration in Python

In Python, many container objects (like lists, tuples, dictionaries, and strings) can be looped over using the `for` loop. This is made possible through the concept of **iterators**.

**Examples of Iteration:**

```python
# Looping over a list
for element in [1, 2, 3]:
    print(element)

# Looping over a tuple
for element in (1, 2, 3):
    print(element)

# Looping over a dictionary (keys)
for key in {'one': 1, 'two': 2}:
    print(key)

# Looping over a string
for char in "123":
    print(char)

# Looping over a file (lines)
for line in open("myfile.txt"):
    print(line, end='')
```

- **Explanation:**
  - In each case, the `for` statement automatically calls the `iter()` function on the container (e.g., list, tuple, dictionary, string, or file).
  - The `iter()` function returns an **iterator object**, which is an object that follows the **iterator protocol**. This protocol includes two key methods: `__iter__()` and `__next__()`.

### 2. How the Iterator Protocol Works

The iterator protocol is the underlying mechanism that enables iteration in Python. It involves two main methods:
- `__iter__()`: This method returns the iterator object itself.
- `__next__()`: This method returns the next item in the sequence. When there are no more items, it raises the `StopIteration` exception to signal that the iteration is complete.

The `for` loop internally calls `iter()` to get the iterator, and then repeatedly calls `__next__()` to fetch each item. When `__next__()` raises `StopIteration`, the loop terminates.

**Example of Using `iter()` and `next()` with a String:**

```python
s = 'abc'
it = iter(s)  # Creating an iterator for the string
print(next(it))  # Output: 'a'
print(next(it))  # Output: 'b'
print(next(it))  # Output: 'c'
print(next(it))  # Raises StopIteration exception
```

- **Explanation:**
  - The string `s` is converted into an iterator object `it` using the `iter()` function.
  - The `next()` function is then used to retrieve each character in the string one by one.
  - After all elements have been accessed, calling `next()` raises a `StopIteration` exception, signaling that there are no more elements to retrieve.

### 3. Creating Custom Iterators

Python allows you to define your own iterators by implementing the `__iter__()` and `__next__()` methods in a class. This is useful when you want to iterate over a custom sequence or implement non-trivial iteration logic.

**Example: Creating a Reverse Iterator:**

```python
class Reverse:
    """Iterator for looping over a sequence backwards."""
    def __init__(self, data):
        self.data = data
        self.index = len(data)

    def __iter__(self):
        return self  # The object itself is the iterator

    def __next__(self):
        if self.index == 0:
            raise StopIteration  # No more elements
        self.index -= 1
        return self.data[self.index]

# Creating an instance of the Reverse class
rev = Reverse('spam')

# Iterating over the Reverse iterator
for char in rev:
    print(char)
```

**Output:**
```
m
a
p
s
```

- **Explanation:**
  - The `Reverse` class defines an iterator that allows iterating over a sequence (like a string or list) in reverse order.
  - The `__init__()` method initializes the iterator with the sequence (`data`) and the index to the end of the sequence.
  - The `__iter__()` method simply returns `self`, indicating that the object itself is the iterator.
  - The `__next__()` method returns the next element in the sequence, and when the index reaches 0, it raises `StopIteration`, signaling the end of the iteration.
  - The `for` loop automatically calls `iter()` to get the iterator and then calls `__next__()` on each iteration.

### 4. How Iterators Work Behind the Scenes

When you use a `for` loop, it abstracts away the details of the iteration. The loop is essentially doing the following:
1. It calls `iter()` on the container to get an iterator object.
2. It calls `__next__()` repeatedly on the iterator until `StopIteration` is raised.

This allows Python to handle iteration over a variety of objects (like lists, strings, or even custom objects) in a consistent manner.

### Key Points
- **Iterators** are objects that implement the `__iter__()` and `__next__()` methods. They are used to access elements in a container one by one.
- Python's `for` loop automatically handles iteration by calling `iter()` and `__next__()`.
- Custom iterators can be created by defining a class with `__iter__()` and `__next__()` methods, enabling custom iteration logic.
- **StopIteration** is raised by the `__next__()` method when there are no more elements to iterate over.

Iterators are a powerful and flexible tool in Python, enabling both simple and complex iteration patterns, and they provide a consistent interface for working with sequences.

## Generators

Generators in Python are a special type of iterable that allow you to generate values one at a time as needed, instead of storing all values in memory at once. They are more **memory efficient** and easier to write than traditional class-based iterators. A generator is written like a normal function but uses the `yield` keyword to return data.

### How Generators Work
- When you call a generator function, it doesn't execute the function immediately. Instead, it returns a generator object, which can be iterated over.
- The function's execution is paused when `yield` is encountered, and the value specified by `yield` is returned to the caller.
- When `next()` is called again on the generator, it resumes execution from where it left off, remembering all of its local variables and the execution state.
- **Note**: you can only only iterate through a generator once. If you need to iterate through something multiple times, you'll need to either re-create the generator each time or use a list. 
  
#### Example: Basic Generator

```python
def reverse(data):
    for index in range(len(data)-1, -1, -1):
        yield data[index]

# Using the generator
for char in reverse('golf'):
    print(char)
```

**Output:**
```
f
l
o
g
```

- **Explanation:**
  - The `reverse` function is a generator that yields each character from the input string in reverse order.
  - When `yield` is encountered, it returns the current character and pauses the function's execution.
  - On subsequent calls to `next()`, the function resumes from the last `yield`, continuing until all characters are returned.
  - This is more efficient than manually maintaining an index or creating a separate iterator class.

#### Example: Custom `range()` function

```python
def custom_range(start=0, stop=n, step=1):
    i = start
    while i < stop: 
        yield i
        i += step
```

### Benefits of Generators
- **Compact and Clear:** Generators are easy to write because they avoid the need for explicit `__iter__()` and `__next__()` methods (as seen in class-based iterators).
- **Automatic State Management:** The state of the generator is saved automatically between `yield` calls, making it simpler to write than using instance variables.
- **Memory Efficiency:** Since generators yield one item at a time and don't store the entire sequence in memory, they are more memory-efficient than creating lists.

#### Generator Termination:
- When the generator function runs out of values to yield, it automatically raises the `StopIteration` exception, which is handled by the iteration mechanism (`for` loop).
  
```python
# Example of generator exhaustion
gen = reverse('golf')
print(next(gen))  # 'f'
print(next(gen))  # 'l'
print(next(gen))  # 'o'
print(next(gen))  # 'g'
print(next(gen))  # Raises StopIteration
```

### Generator Expressions

Generator expressions are a compact way to create generators without writing a full generator function. They are similar to list comprehensions, but they use parentheses `()` instead of square brackets `[]`. These expressions are particularly useful when you want to pass a generator to a function immediately.

**Syntax of Generator Expressions:**
- They consist of a single expression followed by an optional `for` loop and `if` statement.
- Instead of returning a complete list, they return an iterator, which can be consumed lazily (one item at a time).


**Examples of Generator Expressions:**
1. **Sum of Squares**
   ```python
   sum(i*i for i in range(10))
   ```
   **Output:**
   ```
   285
   ```

   - **Explanation:** This generator expression computes the sum of squares of numbers from 0 to 9.
   - The expression `i*i` is generated for each value of `i` in the range, and the result is summed lazily.

2. **Dot Product**
   ```python
   xvec = [10, 20, 30]
   yvec = [7, 5, 3]
   sum(x*y for x, y in zip(xvec, yvec))
   ```
   **Output:**
   ```
   260
   ```

   - **Explanation:** This generator computes the dot product of two vectors (`xvec` and `yvec`). The `zip()` function pairs corresponding elements of the two lists, and for each pair, the product is generated and summed.

3. **Extracting Unique Words**
   ```python
   unique_words = set(word for line in page for word in line.split())
   ```

   - **Explanation:** This generator expression extracts words from each line of text (`page`), splits the lines into words, and adds them to a set (which ensures uniqueness).

4. **Finding the Maximum GPA**
   ```python
   valedictorian = max((student.gpa, student.name) for student in graduates)
   ```

   - **Explanation:** This expression finds the student with the highest GPA from the `graduates` list. For each student, it generates a tuple of GPA and name, and `max()` finds the one with the highest GPA.

5. **Reversing a String**
   ```python
   data = 'golf'
   list(data[i] for i in range(len(data)-1, -1, -1))
   ```
   **Output:**
   ```
   ['f', 'l', 'o', 'g']
   ```

   - **Explanation:** This generator expression reverses the string `data` by generating each character from the end to the beginning.

#### Advantages of Generator Expressions:
- **Compactness:** Generator expressions are shorter and more concise than defining full generator functions.
- **Memory Efficiency:** Like full generators, they do not store all the values in memory, making them more memory-efficient than list comprehensions, especially when dealing with large datasets.
  
#### Comparison with List Comprehensions:
- **List Comprehension:** Creates a full list in memory.
  ```python
  [i*i for i in range(10)]  # Creates a list in memory
  ```
- **Generator Expression:** Returns an iterator, which is lazy (only computes values as needed).
  ```python
  (i*i for i in range(10))  # Returns an iterator, not a list
  ```

#### Key points in Generators

- **Generators** allow for efficient, lazy iteration over data by using the `yield` statement. They automatically handle state between `yield` calls and raise `StopIteration` when the sequence is exhausted.
- **Generator Expressions** provide a more compact and memory-efficient way to create generators in a single line, similar to list comprehensions but with parentheses. They are particularly useful when a generator is passed directly to a function.

---

# Brief Tour of the Standard Library

## `os` Module

The `os` module provides several functions to interact with the operating system. It allows for file and directory management, running system commands, and more.
  
```python
# os.getcwd()
>>> import os
>>> print(os.getcwd())
/home/sri/Documents/Python
>>> 

# os.chdir(command)
>>> os.chdir('..')
>>> print(os.getcwd())
/home/sri/Documents
>>> 

# os.system(command)

os.chdir('/server/accesslogs')  # Change working directory
os.system('mkdir today')  # Execute system shell command
```

**Tip:** Use `import os` instead of `from os import *`, since `os.open()` will hide built-in `open()`.

The `shutil` module offers a higher-level interface for file operations such as copying and moving files:
```python
import shutil
shutil.copyfile('data.db', 'archive.db')  # Copy file
shutil.move('/build/executables', 'installdir')  # Move directory
```

## File Wildcards

The `glob` module helps in matching files with patterns using wildcard characters (`*`, `?`, etc.).

```python
import glob
files = glob.glob('*.py')  # Get all Python files in the directory
print(files)  # Output: ['primes.py', 'random.py', 'quote.py']
```

## Command Line Arguments

The `sys` module provides access to command-line arguments via `sys.argv`.

```python
import sys
print(sys.argv)  # Output: ['demo.py', 'one', 'two', 'three']
```
For more sophisticated argument parsing, the `argparse` module is used:
```python
import argparse
parser = argparse.ArgumentParser(description='Show top lines from each file')
parser.add_argument('filenames', nargs='+')
parser.add_argument('-l', '--lines', type=int, default=10)
args = parser.parse_args()
print(args)
```

## Error Output Redirection and Program Termination

The `sys` module provides access to `stdin`, `stdout`, and `stderr` for redirecting input, output, and error messages, respectively.

```python
import sys
sys.stderr.write('Warning: log file not found, starting a new one\n')
```

To terminate a script, use `sys.exit()`.

## String Pattern Matching

The `re` module provides regular expressions for pattern matching and string manipulation. Regular expressions offer concise and optimized solutions for complex string operations.

### Examples:
```python
import re
re.findall(r'\bf[a-z]*', 'which foot or hand fell fastest')  # Find words starting with 'f'
# Output: ['foot', 'fell', 'fastest']

re.sub(r'(\b[a-z]+) \1', r'\1', 'cat in the the hat')  # Remove duplicate words
# Output: 'cat in the hat'
```

For simpler string operations, native string methods like `replace()` are preferred for clarity.

More example: 

```python
import re
re_examples = [                         # All of these are True, because
not re.match("a", "cat"),               # 'cat' doesn't start with 'a'
re.search("a", "cat"),                  # 'cat' has an 'a' in it
not re.search("c", "dog"),              # 'dog' doesn't have a 'c' in it.
3 == len(re.split("[ab]", "carbs")),    # Split on a or b to ['c','r','s'].
"R-D-" == re.sub("[0-9]", "-", "R2D2")  # Replace digits with dashes.
]
assert all(re_examples), "all the regex examples should be True"

```

## Mathematics

The `math` module provides mathematical functions for floating-point math.

```python
import math
print(math.cos(math.pi / 4))  # Cosine of 45 degrees
# Output: 0.70710678118654757

print(math.log(1024, 2))  # Logarithm base 2 of 1024
# Output: 10.0
```

## Random
The `random` module is used for generating random numbers and making random selections:
```python
import random
print(random.choice(['apple', 'pear', 'banana']))  # Randomly choose a fruit
# Output: 'apple'
```

```Python
import random
random.seed(10) # this ensure we get the same results every time. 

four_uniform_randoms = [random.random() for _ in range(4)]
# [0.5714025946899135,  # random.random() produces numbers
# 0.4288890546751146,   # uniformly between 0 and 1.
# 0.5780913011344704,   # It's the random function we'll use
# 0.20609823213950174]  # most often.

random.randrange(10)    # returns a number [0,10)
random.randrange(3,6)   # returns a number [3,6)


up_to_ten = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
random.seed(10)
random.shuffle(up_to_ten)
print(up_to_ten)
# [7, 2, 6, 8, 9, 4, 10, 1, 3, 5]


random.sample(up_to_ten, 5) # Samples elements without replacement. 
# outputs [1,5,2,3,6]
[random.choice(up_to_ten) for _ in range(5)] # with replacement. 
# outputs [1,5,5,3,2]

```

# Statistics
The `statistics` module provides functions for basic statistical calculations:
```python
import statistics
data = [2.75, 1.75, 1.25, 0.25, 0.5, 1.25, 3.5]
print(statistics.mean(data))  # Calculate the mean
# Output: 1.6071428571428572
```

## Internet Access

The `urllib.request` module is used to retrieve data from URLs, while `smtplib` allows for sending emails.

```python
from urllib.request import urlopen
with urlopen('http://worldtimeapi.org/api/timezone/etc/UTC.txt') as response:
    for line in response:
        line = line.decode()  # Convert bytes to string
        if line.startswith('datetime'):
            print(line.rstrip())  # Print datetime
```

To send an email:
```python
import smtplib
server = smtplib.SMTP('localhost')
server.sendmail('soothsayer@example.org', 'jcaesar@example.org', """To: jcaesar@example.org
From: soothsayer@example.org

Beware the Ides of March.
""")
server.quit()
```

## Dates and Times

The `datetime` module provides tools for manipulating dates and times. It supports both simple and complex operations such as date arithmetic.

```python
from datetime import date
now = date.today()
print(now.strftime("%m-%d-%y. %d %b %Y is a %A on the %d day of %B."))
# Output: '12-02-03. 02 Dec 2003 is a Tuesday on the 02 day of December.'
```

## Data Compression

The `zlib` module supports data compression using the DEFLATE algorithm.

### Example:
```python
import zlib
s = b'witch which has which witches wrist watch'
t = zlib.compress(s)
print(len(t))  # Compressed length
# Output: 37
```

## Performance Measurement

The `timeit` module measures the execution time of small code snippets.

```python
from timeit import Timer
print(Timer('a, b = b, a', 'a=1; b=2').timeit())  # Measure time for swapping
```

## Quality Control


### `assert`
For simple testing, one can use assert statements, which will raise an `AssertionError` if the condition is failed. 

```python
assert 1 + 1 == 2
assert 1 + 1 == 2, "1 + 1 should equal 2 but didn't"
```
In the second assert statement we have added an optional message to be printed if the assertion fails. 

Another way to use assert statements: 
```python
assert name, "empty can't be accepted"
```

### `doctest`
Python offers tools like `doctest` and `unittest` for testing code. The `doctest` module checks that code examples in docstrings are correct.

```python
import doctest
doctest.testmod()
```

The `unittest` module supports more comprehensive testing:
```python
import unittest
class TestStatisticalFunctions(unittest.TestCase):
    def test_average(self):
        self.assertEqual(average([20, 30, 70]), 40.0)
        self.assertRaises(ZeroDivisionError, average, [])
unittest.main()
```

## Batteries Included

Python's "batteries included" philosophy is evident in the rich set of modules available for various tasks:
- **XML Processing:** `xmlrpc.client`, `xml.etree.ElementTree`
- **Email Handling:** `email`, `smtplib`
- **Data Interchange:** `json`, `csv`
- **Database Access:** `sqlite3`

These modules simplify complex tasks like remote procedure calls, email handling, and database interactions.

## Output Formatting

### `reprlib` Module

The `reprlib` module customizes the `repr()` function for large or nested containers, providing a summarized view. For example:

```python
import reprlib
reprlib.repr(set('supercalifragilisticexpialidocious'))
# Output: "{'a', 'c', 'd', 'e', 'f', 'g', ...}"
```

### `pprint` Module

The `pprint` module formats Python objects in a more readable way, adding indentation and line breaks for large data structures:

```python
import pprint
t = [[[['black', 'cyan'], 'white', ['green', 'red']], [['magenta', 'yellow'], 'blue']]]
pprint.pprint(t, width=30)
```

Output:
```
[[[['black', 'cyan'],
   'white',
   ['green', 'red']],
  [['magenta', 'yellow'],
   'blue']]]
```

### `textwrap` Module

The `textwrap` module formats text to fit a specified width:

```python
import textwrap
doc = """The wrap() method is just like fill() except that it returns
a list of strings instead of one big string with newlines to separate
the wrapped lines."""
print(textwrap.fill(doc, width=40))

# Output
The wrap() method is just like fill()
except that it returns a list of strings
instead of one big string with newlines
to separate the wrapped lines.
```

### `locale` Module

The `locale` module handles locale-specific data formats, including number formatting with group separators:

```python
import locale
locale.setlocale(locale.LC_ALL, 'English_United States.1252')
conv = locale.localeconv()
x = 1234567.8
print(locale.format_string("%d", x, grouping=True))
# Output: '1,234,567'
```

## Templating

### `string.Template`

The `string.Template` class allows users to create simple templates with placeholders. It is useful for applications where end-users might customize the content.

```python
from string import Template
t = Template('${village}folk send $$10 to $cause.')
print(t.substitute(village='Nottingham', cause='the ditch fund'))
# Output: 'Nottinghamfolk send $10 to the ditch fund.'
```

### Safe Substitution

The `safe_substitute()` method does not raise an error if a placeholder is missing:

```python
d = dict(item='unladen swallow')
print(t.safe_substitute(d))
# Output: 'Return the unladen swallow to $owner.'
```

### Custom Delimiters

You can also customize the delimiter used for placeholders:

```python
class BatchRename(Template):
    delimiter = '%'
fmt = input('Enter rename style (%d-date %n-seqnum %f-format): ')
t = BatchRename(fmt)
```

Example output:

```
img_1074.jpg --> Ashley_0.jpg
img_1076.jpg --> Ashley_1.jpg
```

## Working with Binary Data Record Layouts

The `struct` module provides `pack()` and `unpack()` functions for handling binary data. This example reads header information from a ZIP file:

```python
import struct
with open('myfile.zip', 'rb') as f:
    data = f.read()
    start = 0
    for i in range(3):
        start += 14
        fields = struct.unpack('<IIIHH', data[start:start+16])
        crc32, comp_size, uncomp_size, filenamesize, extra_size = fields
        start += 16
        filename = data[start:start+filenamesize]
        start += filenamesize
        extra = data[start:start+extra_size]
        print(filename, hex(crc32), comp_size, uncomp_size)
        start += extra_size + comp_size
```

## Multi-threading

The `threading` module allows you to run tasks in the background, improving the responsiveness of applications.

Example:

```python
import threading, zipfile
class AsyncZip(threading.Thread):
    def __init__(self, infile, outfile):
        threading.Thread.__init__(self)
        self.infile = infile
        self.outfile = outfile
    def run(self):
        f = zipfile.ZipFile(self.outfile, 'w', zipfile.ZIP_DEFLATED)
        f.write(self.infile)
        f.close()
        print('Finished background zip of:', self.infile)

background = AsyncZip('mydata.txt', 'myarchive.zip')
background.start()
background.join()
```

## Logging

The `logging` module offers a flexible logging system:

```python
import logging
logging.debug('Debugging information')
logging.info('Informational message')
logging.warning('Warning:config file %s not found', 'server.conf')
logging.error('Error occurred')
logging.critical('Critical error -- shutting down')
```

Output:

```
WARNING:root:Warning:config file server.conf not found
ERROR:root:Error occurred
CRITICAL:root:Critical error -- shutting down
```

## Weak References

The `weakref` module allows tracking objects without creating a reference, useful for caching. When the object is no longer in use, it is removed:

```python
import weakref, gc
class A:
    def __init__(self, value):
        self.value = value
    def __repr__(self):
        return str(self.value)

a = A(10)
d = weakref.WeakValueDictionary()
d['primary'] = a
del a
gc.collect()
```

## Tools for Working with Lists

### `array` Module

The `array` module provides a more compact way to store homogeneous data types, such as numbers:

```python
from array import array
a = array('H', [4000, 10, 700, 22222])
print(sum(a))
# Output: 26932
```

### `deque` from `collections`

The `deque` object is optimized for fast appends and pops from both ends. It's ideal for queues and breadth-first searches:

```python
from collections import deque
d = deque(["task1", "task2", "task3"])
d.append("task4")
print("Handling", d.popleft())
```

### `bisect` and `heapq`

- **`bisect`** helps maintain sorted order in a list:

```python
import bisect
scores = [(100, 'perl'), (200, 'tcl'), (400, 'lua'), (500, 'python')]
bisect.insort(scores, (300, 'ruby'))
```

- **`heapq`** provides an efficient way to handle heaps:

```python
from heapq import heapify, heappush, heappop
data = [1, 3, 5, 7, 9, 2, 4, 6, 8, 0]
heapify(data)
heappush(data, -5)
print([heappop(data) for _ in range(3)])
# Output: [-5, 0, 1]
```

## Decimal Floating-Point Arithmetic

The `decimal` module provides precise decimal floating-point arithmetic, useful for financial calculations:

```python
from decimal import *
round(Decimal('0.70') * Decimal('1.05'), 2)
# Output: Decimal('0.74')
```

## `typing` module

The `typing` module in Python provides support for **type hints**, which are a way to indicate the types of variables, function arguments, and return values in your code. Introduced in Python 3.5, it helps improve code readability, catch errors early using static type checkers (e.g., `mypy`), and provides better editor and IDE support.

---

### Why Use the `typing` Module?
- **Improved Readability**: Makes your code easier to understand by specifying types.
- **Error Detection**: Tools like `mypy` can catch type-related bugs without running the code.
- **Better Tooling**: IDEs can provide autocompletion and better suggestions with type hints.

---

### Common Features of `typing` Module

#### 1. Type Annotations for Variables
You can annotate variables to specify their types:
```python
from typing import List

x: int = 10
names: List[str] = ["Alice", "Bob", "Charlie"]
```

#### 2. Function Annotations
You can annotate function arguments and return types:
```python
from typing import List

def add_numbers(a: int, b: int) -> int:
    return a + b

def get_names() -> List[str]:
    return ["Alice", "Bob"]
```

#### 3. Built-in Generic Types
The `typing` module provides generic versions of Python's built-in types:

| **Type**         | **Description**                              | **Example**                  |
|-------------------|----------------------------------------------|------------------------------|
| `List[T]`         | List of elements of type `T`.               | `List[int]`                 |
| `Dict[K, V]`      | Dictionary with keys of type `K` and values of type `V`. | `Dict[str, int]`          |
| `Set[T]`          | Set of elements of type `T`.                | `Set[str]`                  |
| `Tuple[T1, T2]`   | Tuple with specific types for each element.  | `Tuple[int, str]`           |
| `Union[T1, T2]`   | A value that can be of type `T1` or `T2`.    | `Union[int, str]`           |
| `Optional[T]`     | A value of type `T` or `None`.               | `Optional[int]`             |

---

### Detailed Examples

#### 1. Using `List`, `Dict`, and `Set`
```python
from typing import List, Dict, Set

names: List[str] = ["Alice", "Bob"]
scores: Dict[str, int] = {"Alice": 90, "Bob": 80}
unique_ids: Set[int] = {1, 2, 3}
```

#### 2. Using `Union`
```python
from typing import Union

def get_value(value: Union[int, str]) -> str:
    return str(value)
```

#### 3. Using `Optional`
```python
from typing import Optional

def find_user(user_id: int) -> Optional[str]:
    if user_id == 1:
        return "Alice"
    return None
```

#### 4. Using `Tuple`
```python
from typing import Tuple

def get_coordinates() -> Tuple[int, int]:
    return (10, 20)
```

#### 5. Type Aliases
You can create custom type aliases for better readability:
```python
from typing import List

UserID = int
UserList = List[UserID]

def get_user_ids() -> UserList:
    return [1, 2, 3]
```

---

### Advanced Features

#### 1. Callable
Specifies a function's signature:
```python
from typing import Callable

def execute(func: Callable[[int, int], int], a: int, b: int) -> int:
    return func(a, b)
```

#### 2. Literal (Python 3.8+)
Restrict a value to specific literals:
```python
from typing import Literal

def set_mode(mode: Literal["auto", "manual"]) -> None:
    print(f"Mode set to {mode}")
```

#### 3. TypedDict (Python 3.8+)
Defines dictionaries with specific keys and value types:
```python
from typing import TypedDict

class User(TypedDict):
    name: str
    age: int

user: User = {"name": "Alice", "age": 30}
```

#### 4. NewType
Creates distinct types for better type checking:
```python
from typing import NewType

UserID = NewType('UserID', int)

def get_user_name(user_id: UserID) -> str:
    return f"User {user_id}"

uid = UserID(123)
print(get_user_name(uid))
```

#### 5. Generic
Allows for creating custom generic types:
```python
from typing import TypeVar, Generic

T = TypeVar('T')

class Stack(Generic[T]):
    def __init__(self):
        self.items: List[T] = []

    def push(self, item: T) -> None:
        self.items.append(item)

    def pop(self) -> T:
        return self.items.pop()

stack = Stack[int]()
stack.push(10)
stack.push(20)
print(stack.pop())  # Output: 20
```

---

### Static Type Checking
Using tools like `mypy`, you can check the types in your code:
```bash
pip install mypy
mypy your_script.py
```

---

The `typing` module is a powerful tool for maintaining robust, readable, and error-free code, especially for large and collaborative projects.

## Summary of Modules

| Module             | Functionality                                             |
|--------------------|------------------------------------------------------------|
| `os`               | Operating system interactions (e.g., file management)      |
| `shutil`           | Higher-level file operations (e.g., copy, move files)     |
| `glob`             | File matching with wildcards                              |
| `sys`              | Command-line arguments, stdin, stdout, stderr             |
| `argparse`         | Command-line argument parsing                              |
| `re`               | Regular expression matching                               |
| `math`             | Mathematical functions (e.g., trigonometry, logarithms)   |
| `random`           | Random number generation                                  |
| `statistics`       | Basic statistical operations                              |
| `urllib.request`   | Fetching data from URLs                                   |
| `smtplib`          | Sending emails                                            |
| `datetime`         | Date and time operations                                  |
| `zlib`             | Data compression                                           |
| `timeit`           | Performance measurement                                    |
| `unittest`         | Unit testing                                               |
| `xml`              | XML parsing and handling                                  |
| `reprlib`          | For customizing `repr()` method |
| `pprint`           | Format Python obects to be more readable |
| `textwrap`         | Format text to fit specified width | 
| `locale`           | Region format settings for numbers, date, etc |  
| `string.Template`  | Create text templates with placeholders | 
| `struct`           | Working with Binary Data Record Layouts | 
| `threading`        | For working with threads | 
| `logging`          | Provides flexible logging systems | 
| `weakref`          | Tracking objects without creating a reference, useful for caching | 
| `array` <br> `deque`<br> `bisect` <br>`heapq` | data structures | 
 `decimal` | For high precision computing | 

# Virtual Environments and Packages

In Python, applications may require external packages and modules that are not part of the standard library. Sometimes, different applications require different versions of the same package, which could lead to version conflicts. To solve this problem, Python provides the concept of **virtual environments**. 

A virtual environment is a self-contained directory tree that contains a specific version of Python along with additional packages. This allows different applications to use different versions of Python and libraries without interfering with each other.

For example:
- Application A might need version 1.0 of a library.
- Application B might need version 2.0 of the same library.

By creating separate virtual environments, Application A and B can use different versions without conflict. Upgrading one environment does not affect the other.

## Creating Virtual Environments

The `venv` module in Python is used to create and manage virtual environments. This module installs the version of Python that is currently being used to execute the command.

### Steps to create a virtual environment:
1. **Choose a directory** where you want the virtual environment to be created.
2. **Run the `venv` module** to create the virtual environment:
   ```bash
   python -m venv tutorial-env
   ```
   This will create the `tutorial-env` directory and place a copy of the Python interpreter along with supporting files inside it.

3. **Directory Naming Convention**: A common practice is to name the virtual environment `.venv`. This keeps the directory hidden in Unix-like systems and prevents it from interfering with environment variable definition files.

## Activating the Virtual Environment:

```bash
source tutorial-env/bin/activate
```

Activating the environment changes your shell prompt to indicate which virtual environment you are using and modifies the environment so that the `python` command uses the correct version from the virtual environment.

Example:
```bash
$ source ~/envs/tutorial-env/bin/activate
(tutorial-env) $ python
```

## Deactivating the Virtual Environment:
To deactivate a virtual environment and return to the system's Python installation, simply run:
```bash
deactivate
```

## Managing Packages with pip

`pip` is the Python package manager that allows you to install, upgrade, and remove packages from the virtual environment. By default, `pip` installs packages from the Python Package Index (PyPI).

### Basic `pip` Commands:
- **Install a package**:
   ```bash
   python -m pip install <package-name>
   ```

- **Install a specific version of a package**:
   ```bash
   python -m pip install <package-name>==<version>
   ```

- **Upgrade an existing package**:
   ```bash
   python -m pip install --upgrade <package-name>
   ```

- **Uninstall a package**:
   ```bash
   python -m pip uninstall <package-name>
   ```

### Viewing Package Information:
- **Show package details**:
   ```bash
   python -m pip show <package-name>
   ```
   This displays metadata about the package, such as its version, location, and dependencies.

- **List installed packages**:
   ```bash
   python -m pip list
   ```

- **Freeze installed packages**:
   ```bash
   python -m pip freeze
   ```
   This outputs a list of installed packages in a format suitable for use in a `requirements.txt` file.

### Using `requirements.txt`:
A `requirements.txt` file lists all the necessary packages and their versions for a Python application. This file can be committed to version control and shared with others. To install all the dependencies from a `requirements.txt` file:
```bash
python -m pip install -r requirements.txt
```

This allows other users to set up the same virtual environment with the same dependencies.

### Example of using `requirements.txt`:
```bash
$ python -m pip freeze > requirements.txt
$ cat requirements.txt
novas==3.1.1.3
numpy==1.9.2
requests==2.7.0
```
To install the dependencies:
```bash
$ python -m pip install -r requirements.txt
```

# Floating-Point Arithmetic: Issues and Limitations

Floating-point numbers in computers are represented using binary fractions (base 2), similar to how decimal numbers are represented in base 10. However, the issue arises because many decimal numbers cannot be exactly represented in binary. This leads to approximations when dealing with floating-point numbers in computers, often causing unexpected results.

## Representation of Fractions

Consider a decimal fraction like 0.625. In base 10, it is represented as:
\[ 0.625 = \frac{6}{10} + \frac{2}{100} + \frac{5}{1000} \]

In base 2 (binary), the number 0.625 is represented as:
\[ 0.625 = \frac{1}{2} + \frac{0}{4} + \frac{1}{8} \]
This is straightforward because it can be expressed precisely using powers of 2.

However, many decimal fractions cannot be exactly represented in binary. For example, 1/10 in decimal is:
\[ 0.1 \text{ (in base 10)} \]

In binary, this fraction is an infinitely repeating sequence:
\[ 0.1 = 0.00011001100110011001100110011\ldots \text{ (repeating)} \]

If we truncate this repeating sequence, we get an approximation. In most computers, binary floating-point numbers are approximated using 53 bits for precision (in double-precision format).

For instance, 0.1 in binary is approximated as:
\[ \frac{3602879701896397}{2^{55}} \]
This is a close approximation, but not exactly equal to 1/10. On most systems, this binary approximation is used to store 0.1.

## Floating-Point Approximation and Display

Even though the value stored for 0.1 is an approximation, Python (and many other programming languages) only displays a rounded version of this value. If Python were to display the exact internal binary representation of 0.1, it would be:
```
0.1000000000000000055511151231257827021181583404541015625
```
However, Python rounds this to the simpler:
```
0.1
```
This rounded representation gives the illusion of exactness, but the actual stored value is an approximation. Interestingly, many different decimal numbers (like 0.1, 0.10000000000000001, and others) share the same closest binary approximation.

## Examples of Floating-Point Errors

Floating-point arithmetic can lead to errors that are not immediately obvious. For instance, summing three values of 0.1:
```python
0.1 + 0.1 + 0.1 == 0.3
```
This results in:
```
False
```
This happens because 0.1 cannot be exactly represented, and summing multiple approximations introduces small errors. Even rounding the values using Python's `round()` function does not eliminate the error:
```python
round(0.1, 1) + round(0.1, 1) + round(0.1, 1) == round(0.3, 1)
```
This also results in:
```
False
```
However, the `math.isclose()` function can help compare inexact floating-point values within a tolerance:
```python
import math
math.isclose(0.1 + 0.1 + 0.1, 0.3)
```
This results in:
```
True
```

## Handling Floating-Point Precision

To mitigate the effects of floating-point errors, Python provides several methods:

- **String Formatting**: You can format floating-point numbers to display only a certain number of significant digits, avoiding confusion with excessive precision:
  ```python
  format(math.pi, '.12g')  # 12 significant digits
  format(math.pi, '.2f')   # 2 digits after the decimal point
  ```

- **`sum()` with Extended Precision**: The built-in `sum()` function uses extended precision for intermediate rounding steps, reducing errors when summing many values:
  ```python
  sum([0.1] * 10) == 1.0
  ```

- **`math.fsum()`**: This function is even more accurate, as it tracks all the intermediate digits to minimize rounding errors:
  ```python
  math.fsum(arr)
  ```

## When Exact Arithmetic is Needed

For applications that require exact decimal arithmetic (e.g., financial calculations), Python provides the **`decimal`** and **`fractions`** modules:
- **`decimal` module**: This implements decimal arithmetic and is useful for high-precision operations.
- **`fractions` module**: This works with rational numbers, so fractions like 1/3 can be represented exactly.

## Analyzing the `0.1` Example in Detail

The primary issue with floating-point representation is that certain decimal fractions (like 0.1) cannot be represented exactly in binary. In IEEE 754 double-precision format (binary64), 0.1 is represented as:
\[ \frac{7205759403792794}{2^{56}} \]
This is a good approximation of 1/10, but it is slightly larger. The value stored in memory for 0.1 is:
```
0.1000000000000000055511151231257827021181583404541015625
```
To analyze this more precisely, you can use the `as_integer_ratio()` method:
```python
(0.1).as_integer_ratio()
```
This returns:
```
(3602879701896397, 36028797018963968)
```
This exact ratio can be used to represent 0.1 precisely in rational form.
