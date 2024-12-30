# Table of Contents
* [Introduction](#Introduction)
* [Whetting Your Appetite](#Whetting-Your-Appetite)
* [Using the Python Interpreter](#Using-the-Python-Interpreter)
* [An Informal Introduction to Python](#An-Informal-Introduction-to-Python)

# Introduction

Python is an easy-to-learn, powerful programming language known for its efficient data structures, simple object-oriented approach, elegant syntax, dynamic typing, and interpreted nature, making it ideal for scripting and rapid development across platforms.

## Key Features:
- **High-level Data Structures**: Powerful and easy-to-use data structures.
- **Object-Oriented**: Supports simple object-oriented programming.
- **Elegant Syntax**: Clean and easy-to-understand syntax.
- **Dynamic Typing**: Dynamically assigns types to variables.
- **Interpreted**: Executes code line-by-line for quick development.

## Extensibility:
Python can be extended with functions and data types in C, C++, or other languages callable from C, and is suitable for customizable applications.

## Tutorial Overview:
This tutorial introduces Python’s basic concepts and features.

# Whetting Your Appetite

Python is a versatile, easy-to-learn programming language that caters to a wide range of tasks, from scripting to GUI applications and game development. Its simplicity, power, and wide applicability make it an excellent choice for programmers of all levels.

---

## Why Python?

### Flexibility Across Use Cases
- Python bridges the gap between scripting and full-fledged programming:
  - **Shell Scripts**: Limited to file manipulation and text data processing.
  - **C/C++/Java**: Time-consuming for initial development.
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
  - Application in a broader range of problems compared to Awk or Perl.

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
- Python can be extended using **C**:
  - Add new built-in functions or modules for:
    - Performance-critical operations.
    - Access to binary-only libraries (e.g., vendor-specific graphics libraries).
- Embed the Python interpreter into C applications:
  - Use Python as an extension or command language within custom applications.

---

## Fun Fact
- Python is named after the BBC show *"Monty Python’s Flying Circus"* and has no connection to reptiles.
- References to Monty Python skits in documentation are encouraged, adding a touch of humor and creativity.

---

Python is more than just a language; it’s a tool that simplifies programming, reduces development time, and empowers you to solve complex problems effectively. Whether you're a beginner or a seasoned programmer, Python can help you achieve your goals with ease.

Here's an in-depth Markdown summary of the provided content:

# Using the Python Interpreter

The Python interpreter is a powerful tool that can be used interactively or for executing scripts. 

---

## Installing Python
To install Python interpreter follow the below commands: 
```bash
sudo apt update && apt upgrade -y
sudo apt install python3 -y
python --version
```

## Locating Python
To find Python on your system, use the `whereis` command in Unix-based environments:
```bash
$ whereis python3
python3: /usr/bin/python3 /usr/lib/python3 /etc/python3 /usr/share/python3 /usr/share/man/man1/python3.1.gz
```

This command lists the paths where Python is installed, including binaries, libraries, configuration files, and documentation.

---

## Quitting the Interpreter
You can exit the Python interpreter using one of the following methods:
- **Control Commands**:
  - `CTRL-Z` (Windows)
  - `CTRL-D` (Unix)
- **Commands**:
  - `exit()`
  - `quit()`

---

## Invoking the Interpreter

### Standard Invocation
- **Unix/Linux**: The interpreter is typically installed at `/usr/bin/python3.13`.
  - Add `/usr/bin` to your shell’s search path (already added if you installed via command line) to invoke it using:
    ```bash
    python3.13
    ```

### Command Line Options
- **Execute Commands Directly**: Use `-c` to execute Python commands inline:
  ```bash
  $ python -c "print('Hello, World')"
  Hello, World
  ```
  - Quote the entire command to avoid shell issues with special characters.
- **Execute Modules**: Use `-m` to run Python modules as scripts:
  ```bash
  python -m module_name [arguments]
  ```
- **Interactive Mode After Script**: Use `-i` to enter interactive mode after running a script:
- Consider a script `script.py`:
  ```python
  print("Hello, World!")
  ```
- When the below command is run
  ```bash
  $ python -i script.py
  Hello, World!
  >>> 
  ```
---

## Interactive Features

- When invoked interactively (e.g., without a script), Python reads and executes commands interactively, similar to a Unix shell.
- When given a script file or standard input, Python reads and executes the content of the file.

### Interactive Mode
* When commands are read from tty, the interpreter is said to be in interactive mode. 
* To start interactive mode execute
  ```bash
  $ python3
  Python 3.12.3 (main, Nov  6 2024, 18:32:19) [GCC 13.2.0] on linux
  Type "help", "copyright", "credits" or "license" for more information.
  >>> for i in range(10):
  ...     print(i, end=" ")
  ... 
  0 1 2 3 4 5 6 7 8 9 >>> 
  ```
  * `>>>` is called **primary command**
  * `...` is called **secondary command**
    * Used to to create multiline comment
    * To quit a secondary prompt type in a blank line. 
  
### Interactive Editing and History Features in Python

#### Key Features:
- **Line Editing & History Substitution**: Some Python interpreters support editing of the current input line and history substitution using the GNU Readline library, similar to Korn and Bash shells.
- **Tab Completion**: 
  - Automatically enabled at interpreter startup.
  - Supports variable, module, and attribute name completion.
  - Works for dotted expressions (e.g., `string.a`) by evaluating up to the last `.` and suggesting attributes of the resulting object.
- **History Management**:
  - Input history is saved to `.python_history` in the user directory.
  - History persists across interactive interpreter sessions.

#### Limitations:
- No suggestions for proper indentation on continuation lines.
- Limited use of the interpreter's symbol table for completion.
- No built-in tools for checking or matching parentheses, quotes, etc.

#### Enhanced Alternatives:
- **IPython**:
  - Advanced tab completion, object exploration, and history management.
  - Highly customizable and embeddable.
- **bpython**:
  - Similar features with an enhanced interactive experience.

---

## Argument Passing

Python provides a flexible way to handle command-line arguments passed to a script. These arguments are stored in the `sys.argv` list, which resides in the `sys` module.

---

### Accessing Arguments
- The command-line arguments are automatically converted into a list of strings and assigned to the `sys.argv` variable.
- To access this list, import the `sys` module:
  ```python
  import sys
  print(sys.argv)
  ```
---

### Structure of `sys.argv`
- **`sys.argv[0]`**: Always contains the name of the script or the indicator of the input source.
  - If no script or arguments are provided: `sys.argv[0]` is an empty string (`''`).
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
  - If the script is run with `-` (indicating standard input): `sys.argv[0]` is set to `'-'`.
    ```bash
    $ python - script.py 
    Python 3.12.3 (main, Nov  6 2024, 18:32:19) [GCC 13.2.0] on linux
    Type "help", "copyright", "credits" or "license" for more information.
    >>> import sys
    >>> len(sys.argv)
    2
    >>> for arg in sys.argv:
    ...     print(arg)
    ... 
    -
    script.py
    >>> 
    ```
  - If using `-c` to execute a command: `sys.argv[0]` is set to `'-c'`.
    ```bash
    $ python -c "import sys; print(sys.argv[0])"
    -c
    ```
  - If using `-m` to run a module: `sys.argv[0]` is set to the full name of the located module.

- Additional arguments provided after the script name or command are added sequentially to the `sys.argv` list as strings.
  ```bash
  $ python script.py Hi hello little boy
  Length of sys.arv: 5
  script.py
  Hi
  hello
  little
  boy
  ```
---

### Behavior with Command-Line Options
#### Using `-c` for Commands
- When running Python with `-c` to execute a command:
  ```bash
  python -c "print('Hello, World!')" arg1 arg2
  ```
  - `sys.argv[0]`: `'-c'`
  - `sys.argv[1:]`: Contains `['arg1', 'arg2']`

#### Using `-m` for Modules
- When running a Python module with `-m`:
  ```bash
  python -m module_name arg1 arg2
  ```
  - `sys.argv[0]`: The full name of the module.
  - `sys.argv[1:]`: Contains `['arg1', 'arg2']`

---

### Handling Remaining Options
- Arguments following `-c` or `-m` are **not consumed** by the Python interpreter itself.
  - These arguments remain in `sys.argv` for the command or module to process directly.
  - This ensures flexibility when passing options to user-defined scripts or modules.

---

## Source Code Encoding

### Default Encoding
- Python source files are treated as **UTF-8** by default.
  - This allows characters from most languages to be used in string literals, identifiers, and comments.
  - However, the standard library uses only ASCII for identifiers to maintain portability.

### Editor Requirements
- Your editor must:
  1. Recognize the file as UTF-8.
  2. Use a font that supports the characters present in the file.

### Declaring a Custom Encoding
- To use an encoding other than UTF-8, add a special comment at the beginning of the file:
  ```python
  # -*- coding: encoding -*-
  ```
- Example for Windows-1252 encoding:
  ```python
  # -*- coding: cp1252 -*-
  ```

### Exception: When Using a Shebang
- If the file starts with a UNIX shebang line (e.g., `#!/usr/bin/env python3`), the encoding declaration should be the **second line**:
  ```python
  #!/usr/bin/python3
  # -*- coding: cp1252 -*-
  ```

---

## Shebang (`#!`) Explained
- The shebang line specifies the interpreter to execute the script.
  - Syntax: `#!/path/to/interpreter`
  - Example:
    ```python
    #!/usr/bin/python3
    ```
- **Purpose**:
  - Enables the script to run directly from the command line without explicitly invoking the interpreter.
  - For example:
    ```bash
    $ ./script.py
    ```
    instead of:
    ```bash
    $ python3 script.py
    ```
  * **Note!** You need to have execute permission to run the file. Else you will get error `bash: ./script.py: Permission denied`, when you try to run `./script.py`
  ```bash
  $ cat script.py
  #!/usr/bin/python3
  print("Hello, World!")
  $ chmod +x script.py
  $ ./script.py
  Hello, World!
  ```
    
- **Usage Notes**:
  - The `env` utility (`/usr/bin/env`) is often used for portability. It searches for the interpreter in the system's `PATH`, making the script adaptable across environments.AN INFORMAL INTRODUCTION TO PYTHON
In the following examples, input and output are distinguished by the presence or absence of prompts (»> and …):
to repeat the example, you must type everything after the prompt, when the prompt appears; lines that do not begin
with a prompt are output from the interpreter. Note that a secondary prompt on a line by itself in an example means
you must type a blank line; this is used to end a multi-line command.
Many of the examples in this manual, even those entered at the interactive prompt, include comments. Comments
in Python start with the hash character, #, and extend to the end of the physical line. A comment may appear at the
start of a line or following whitespace or code, but not within a string literal. A hash character within a string literal
is just a hash character. Since comments are to clarify code and are not interpreted by Python, they may be omitted
when typing in examples.
Some examples:
# this is the first comment
spam = 1 # and this is the second comment
# ... and now a third!
text = "# This is not a comment because it's inside quotes."
3.1 Using Python as a Calculator
Let’s try some simple Python commands. Start the interpreter and wait for the primary prompt, >>>. (It shouldn’t
take long.)
3.1.1 Numbers
The interpreter acts as a simple calculator: you can type an expression at it and it will write the value. Expression
syntax is straightforward: the operators +, -, * and / can be used to perform arithmetic; parentheses (()) can be
used for grouping. For example:
>>> 2 + 2
4
>>> 50 - 5*6
20
>>> (50 - 5*6) / 4
5.0
>>> 8 / 5 # division always returns a floating-point number
1.6
The integer numbers (e.g. 2, 4, 20) have type int, the ones with a fractional part (e.g. 5.0, 1.6) have type float.
We will see more about numeric types later in the tutorial.
Division (/) always returns a float. To do floor division and get an integer result you can use the // operator; to
calculate the remainder you can use %:
7Python Tutorial, Release 3.13.0
>>> 17 / 3 # classic division returns a float
5.666666666666667
>>>
>>> 17 // 3 # floor division discards the fractional part
5
>>> 17 % 3 # the % operator returns the remainder of the division
2
>>> 5 * 3 + 2 # floored quotient * divisor + remainder
17
With Python, it is possible to use the ** operator to calculate powers1 :
>>> 5 ** 2
25
>>> 2 ** 7
128
# 5 squared
# 2 to the power of 7
The equal sign (=) is used to assign a value to a variable. Afterwards, no result is displayed before the next interactive
prompt:
>>> width = 20
>>> height = 5 * 9
>>> width * height
900
If a variable is not “defined” (assigned a value), trying to use it will give you an error:
>>> n # try to access an undefined variable
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
NameError: name 'n' is not defined
There is full support for floating point; operators with mixed type operands convert the integer operand to floating
point:
>>> 4 * 3.75 - 1
14.0
In interactive mode, the last printed expression is assigned to the variable _. This means that when you are using
Python as a desk calculator, it is somewhat easier to continue calculations, for example:
>>> tax = 12.5 / 100
>>> price = 100.50
>>> price * tax
12.5625
>>> price + _
113.0625
>>> round(_, 2)
113.06
This variable should be treated as read-only by the user. Don’t explicitly assign a value to it — you would create an
independent local variable with the same name masking the built-in variable with its magic behavior.
In addition to int and float, Python supports other types of numbers, such as Decimal and Fraction. Python
also has built-in support for complex numbers, and uses the j or J suffix to indicate the imaginary part (e.g. 3+5j).
1 Since ** has higher precedence than -, -3**2 will be interpreted as -(3**2) and thus result in -9. To avoid this and get 9, you can use
(-3)**2.

Here's an in-depth summary of the content in Markdown format:

# An Informal Introduction to Python

Python allows for interactive experimentation and scripting with ease. Below is a breakdown of its features, usage examples, and notable syntax.

## Comments in Python

Comments start with `#` and extend to the end of the line. They can appear at the beginning or after code, but not within string literals. Examples:

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

Attempting to use an undefined variable results in an error:

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

_Important:_ Avoid explicitly assigning a value to `_`, as it is meant for temporary results.

### Other Number Types

Python supports additional numeric types:
- **`Decimal`**: For fixed-point arithmetic with precise control over rounding and significant digits.
- **`Fraction`**: For exact rational number representation.
- **Complex Numbers**: Use `j` or `J` to indicate the imaginary part.

#### Examples

**`Decimal`**:  
The `Decimal` class from the `decimal` module provides precise decimal arithmetic, which is useful for financial and scientific applications.

```python
>>> from decimal import Decimal
>>> Decimal('0.1') + Decimal('0.2')  # Avoids floating-point precision errors
Decimal('0.3')

>>> Decimal('1.23456789').quantize(Decimal('0.01'))  # Rounds to two decimal places
Decimal('1.23')
```

**`Fraction`**:  
Use the `Fraction` class from the `fractions` module for exact arithmetic with rational numbers.

```python
>>> from fractions import Fraction
>>> Fraction(1, 3) + Fraction(2, 3)
Fraction(1, 1)
```

**Complex Numbers**:  
Python supports complex numbers natively, with `j` or `J` indicating the imaginary part.

```python
>>> 3 + 5j  # Complex number
(3+5j)

>>> (2 + 3j) * (1 - 4j)
(14-5j)
```

## Strings
Python allows for manipulation of text, represented by the `str` type. This includes words, sentences, special characters, or even numerals enclosed in quotes.
Strings in Python can be enclosed in **single quotes** (`'...'`) or **double quotes** (`"..."`) with the same result. Special characters (like `\n`) work the same in both.

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

>>> '"Yes," they said.'
'"Yes," they said.'

>>> "\"Yes,\" they said."
'"Yes," they said.'
```

### `print()` method
line
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

#### Examples
```python
>>> print(r'C:\some\name')
C:\some\name
```

#### A Subtle Limitation
Raw strings **cannot end with an odd number of backslashes** because the final backslash escapes the closing quote.

#### Example
```python
# This will cause an error
>>> r"C:\some\path\"
SyntaxError: EOL while scanning string literal

# Workaround: Use normal strings with escaping
>>> "C:\\some\\path\\"
'C:\\some\\path\\'
```

### Multi-line Strings
* Use triple quotes (`"""..."""` or `'''...'''`) for strings spanning multiple lines.
* End of lines are automatically included in the string, but it's possible to prevent this by adding a \ at the end of the line. 

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

#### Automatic Concatenation
* Adjacent strings separated by a space are automatically concatenated. 
* Very useful when we want to break long strings. You can also use `\` backslash. 

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

#### Indexing and Slicing
* Strings are indexed starting at `0`. Negative indices count from the end.
* In negative indexing, `-0` is same as `0`, hence they start from `-1`.
* Indexing allows you to get a **character**, slicing allows you to get a **substring**.

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

* Attempting to use an index that is too large will result in an error:
```python
>>> word[42] # the word only has 6 characters
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
IndexError: string index out of range
```

#### Slicing Behavior
- Start is **inclusive**, and end is **exclusive**.
  - It's doen done so that `s[:i] + s[i:] = s`
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
- Out-of-range slices are handled gracefully:
```python
>>> word[4:42]
'on'

>>> word[42:]
''
```

### Immutable Strings
Strings in Python cannot be modified. To change a string, create a new one.

```python
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

#### Examples

- **Indexing and Slicing**:
  ```python
  word = "Python"
  print(word[0])    # 'P' (first character)
  print(word[-1])   # 'n' (last character)
  print(word[0:3])  # 'Pyt' (substring from position 0 to 3, exclusive)
  ```

- **Concatenation and Repetition**:
  ```python
  greeting = "Hello, " + "World!"
  print(greeting)   # 'Hello, World!'
  print("Hi! " * 3) # 'Hi! Hi! Hi!'
  ```

- **Membership Testing**:
  ```python
  print('H' in "Hello")  # True
  print('z' not in "Hello")  # True
  ```

---

###  String Methods (`string-methods`)

Python strings come with a rich set of methods for common tasks like case conversion, splitting, joining, and searching.

#### Common String Methods

- **Transformation**:
  ```python
  print("hello".upper())       # 'HELLO'
  print("WORLD".lower())       # 'world'
  print("python".capitalize()) # 'Python'
  print("tItLe".title())       # 'Title'
  ```

- **Searching and Replacing**:
  ```python
  text = "hello world"
  print(text.find("world"))    # 6 (index where "world" starts)
  print(text.replace("world", "Python"))  # 'hello Python'
  ```

- **Splitting and Joining**:
  ```python
  data = "apple,orange,banana"
  print(data.split(","))       # ['apple', 'orange', 'banana']
  print(", ".join(['apple', 'orange', 'banana']))  # 'apple, orange, banana'
  ```

---

### Formatted String Literals (`f-strings`)

Introduced in Python 3.6, **f-strings** allow you to embed expressions directly in string literals for easy and efficient formatting.

#### Examples

- **Basic Usage**:
  ```python
  name = "Alice"
  age = 25
  print(f"My name is {name} and I am {age} years old.") 
  # Output: 'My name is Alice and I am 25 years old.'
  ```

- **Evaluating Expressions**:
  ```python
  print(f"The sum of 5 + 3 is {5 + 3}.") 
  # Output: 'The sum of 5 + 3 is 8.'
  ```

- **Formatting Values**:
  ```python
  pi = 3.14159
  print(f"Pi rounded to 2 decimals: {pi:.2f}") 
  # Output: 'Pi rounded to 2 decimals: 3.14'
  ```

---

### String Formatting with `str.format()` (`formatstrings`)

The `str.format()` method provides a more powerful way to format strings.

#### Examples

- **Positional and Keyword Arguments**:
  ```python
  print("Hello, {}!".format("World")) 
  # Output: 'Hello, World!'
  print("Name: {name}, Age: {age}".format(name="Alice", age=25)) 
  # Output: 'Name: Alice, Age: 25'
  ```

- **Formatting Numbers**:
  ```python
  print("Pi: {:.2f}".format(3.14159))  # Output: 'Pi: 3.14'
  print("{:d}".format(42))            # Output: '42'
  ```

- **Padding and Alignment**:
  ```python
  print("{:<10}".format("left"))   # 'left      '
  print("{:>10}".format("right"))  # '     right'
  print("{:^10}".format("center")) # '  center  '
  ```

---

### Old String Formatting (`old-string-formatting`)

Before `str.format()` and f-strings, Python used the `%` operator for string formatting.

#### Examples

- **Basic Substitution**:
  ```python
  print("Hello, %s!" % "World") 
  # Output: 'Hello, World!'
  ```

- **Formatting Numbers**:
  ```python
  print("Pi: %.2f" % 3.14159)  # Output: 'Pi: 3.14'
  print("%d items" % 42)       # Output: '42 items'
  ```

- **Multiple Substitutions**:
  ```python
  print("Name: %s, Age: %d" % ("Alice", 25)) 
  # Output: 'Name: Alice, Age: 25'
  ```

---

### Key Takeaways

- The `str.format()` method and f-strings are preferred for modern string formatting due to their flexibility and clarity.
- The older `%` formatting style is still functional but less versatile compared to newer methods.




Here's an in-depth Markdown summary of Python's list features based on the provided details:

## Python Lists: A Comprehensive Guide

Lists are compound data types that group together values in a specific order. 

### Introduction to Lists

- Lists are defined using square brackets `[]`, with items separated by commas.
- They can contain items of **different types**, though typically, items are of the same type.

#### Example:
```python
squares = [1, 4, 9, 16, 25]
print(squares)  # Output: [1, 4, 9, 16, 25]
```

---

### Indexing and Slicing

Lists, like strings, support **indexing** and **slicing**.

- **Indexing**:
  - Access individual items using their index.
  - Negative indices start counting from the end.

- **Slicing**:
  - Returns a new list containing the requested slice.

#### Examples:
```python
# Indexing
print(squares[0])   # Output: 1
print(squares[-1])  # Output: 25

# Slicing
print(squares[-3:]) # Output: [9, 16, 25]
```

---

### List Operations

- **Concatenation**:
  Combine lists using the `+` operator.
  
- **Repetition**:
  Repeat lists using the `*` operator.

#### Example:
```python
print(squares + [36, 49, 64, 81, 100]) 
# Output: [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
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

- Assigning a list to a new variable creates a **reference**, not a copy.
- Changes made to one variable affect the other.
- `id()` gives the memory location referred by the variable. 

#### Example:
```python
rgb = ["Red", "Green", "Blue"]
rgba = rgb
>>> id(rgb) == id(rgba) # they reference the same object
True
rgba.append("Alpha")
print(rgb)  # Output: ["Red", "Green", "Blue", "Alpha"]
```

To create a copy, use slicing:
```python
correct_rgba = rgba[:]
correct_rgba[-1] = "Alpha"
print(correct_rgba)  # Output: ["Red", "Green", "Blue", "Alpha"]
print(rgba)          # Output: ["Red", "Green", "Blue", "Alpha"]
```

---

### Assignment to Slices

Lists allow replacing, removing, or clearing elements using slice assignments.

#### Examples:
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

### List Functions

- **`len()`**:
  Returns the number of items in a list.

#### Example:
```python
letters = ['a', 'b', 'c', 'd']
print(len(letters))  # Output: 4
```

---

### Nesting Lists

Lists can contain other lists, creating a nested structure.

### Examples:
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

## Other Programming features

### Fibonacci Series Example

The Fibonacci sequence can be generated using the following code:
```python
# Fibonacci series:
# The sum of two elements defines the next
a, b = 0, 1
while a < 10:
    print(a)
    a, b = b, a + b
```

**Output**:
```
0
1
1
2
3
5
8
```

---

### Key Features and Concepts

#### Multiple Assignment
- Python allows simultaneous assignment of multiple variables:
  ```python
  a, b = 0, 1
  ```
- During assignment, expressions on the right-hand side are evaluated **left to right** before the values are assigned.

#### `while` Loop
- The `while` loop runs as long as the condition evaluates to `True`.
- Conditions can include:
  - **Numbers**: Non-zero integers are `True`; zero is `False`.
  - **Sequences** (strings, lists, etc.): Non-empty sequences are `True`; empty sequences are `False`.

#### Indentation
- Python uses **indentation** to group statements.
- Every line in the block must be indented by the same amount.
- At the interactive prompt:
  - Type spaces or tabs for indentation.
  - Follow compound statements with a blank line to indicate completion.

####  `print()` Function
- The `print()` function writes output to the screen.
- Differences from writing expressions:
  - Handles multiple arguments, floating-point numbers, and strings differently.
  - Automatically inserts spaces between arguments.
  - Prints strings without quotes.
  - Can customize Output with `end` keyword argument
    - Avoid the default newline after output.
    - Specify a different ending string.
    - **Example**:
    ```python
    a, b = 0, 1
    while a < 1000:
        print(a, end=',')
        a, b = b, a + b
    0,1,1,2,3,5,8,13,21,34,55,89,144,233,377,610,987,
    ```

#### Comparison Operators
   - `<` (less than), `>` (greater than)
   - `==` (equal to), `!=` (not equal to)
   - `<=` (less than or equal to), `>=` (greater than or equal to)

---