# Table of Contents
* [Introduction](#Introduction)
* [Whetting Your Appetite](#Whetting-Your-Appetite)
* [Using the Python Interpreter](#Using-the-Python-Interpreter)
* [An Informal Introduction to Python](#An-Informal-Introduction-to-Python)
* [More Control Flow Tools in Pyton](#more-control-flow-tools-in-python)
* [Data Structures](#data-structures)
* [Modules](#Modules)

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

## Lists

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

# More Control Flow Tools in Python

## `if` Statements

The `if` statement is used to execute code based on a condition. It can include optional `elif` and `else` parts:

```python
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

**Example Interaction:**
```
Please enter an integer: 42
More
```
- An `if … elif … elif …` sequence is a substitute for the switch or case
statements found in other languages.
- `elif` is short for "else if" and prevents **excessive indentation**.
- The `else` part is optional.
- Use the `match` statement for comparing same constant value to several constant.

---

## `for` Statements

The `for` statement iterates over items in a sequence (like a list or string) in order:

```python
words = ['cat', 'window', 'defenestrate']
for w in words:
    print(w, len(w))
```

**Output:**
```
cat 3Match
window 6
defenestrate 12
```

### Modifying Collections While Iterating

Avoid modifying a collection directly while iterating. Instead, use a copy or create a new collection:

**Using a Copy:**
```python
users = {'Hans': 'active', 'Éléonore': 'inactive', 'John': 'active'}
for user, status in users.copy().items():
    if status == 'inactive':
        del users[user]
```

**Creating a New Collection:**
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
##### What Happens?

* The iterator starts with the original list, [1, 2, 3, 4, 5].
* When it encounters 2, it appends 4 (twice its value) to the list.
* The modified list becomes [1, 2, 3, 4, 5, 4].
* The iterator does not track that the new elements have been added, and depending on how Python processes the list, this may cause repeated processing of some elements or even go back to earlier elements.

---

## The `range()` Function

Use the built-in `range(start, stop, step)` function to generate sequences of numbers:

```python
for i in range(5):
    print(i)
```

**Output:**
```
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

### Iterating Over Indices

Combine `range()` and `len()` to iterate over sequence indices:

```python
a = ['Mary', 'had', 'a', 'little', 'lamb']
for i in range(len(a)):
    print(i, a[i])
```

**Output:**
```
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

- `range()` returns an iterable, not a list, **saving memory**.
- Example of using `range()` with `sum()`:

```python
print(sum(range(4)))  # 0 + 1 + 2 + 3 = 6
```

---

## `break` and `continue` Statements

### `break`

The `break` statement exits the innermost loop:

```python
for n in range(2, 10):
    for x in range(2, n):
        if n % x == 0:
            print(f"{n} equals {x} * {n//x}")
            break
```

**Output:**
```
4 equals 2 * 2
6 equals 2 * 3
8 equals 2 * 4
9 equals 3 * 3
```

### `continue`

The `continue` statement skips to the next iteration of the loop:

```python
for num in range(2, 10):
    if num % 2 == 0:
        print(f"Found an even number {num}")
        continue
    print(f"Found an odd number {num}")
```

**Output:**
Found an even number 2
Found an odd number 3
Found an even number 4
Found an odd number 5
Found an even number 6
Found an odd number 7
Found an even number 8
Found an odd number 9


---

## `else` Clauses on Loops

An `else` clause can follow a `for` or `while` loop. The `else` block executes only if the loop completes without encountering a `break` statement.

### For Loops with `else`

In the following example, the `else` clause executes if no factors are found (i.e., the loop does not encounter a `break`):

```python
for n in range(2, 10):
    for x in range(2, n):
        if n % x == 0:
            print(f"{n} equals {x} * {n//x}")
            break
    else:
        # Loop fell through without finding a factor
        print(f"{n} is a prime number")
```

**Output:**
```
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
```

**Output:**
```
0
1
2
3
4
Loop completed without a break.
```

### Behavior of `else` Clause

The `else` block does not execute if the loop is terminated by a `break`. This behavior is similar to the `else` clause in a `try` statement, which executes only if no exception occurs.

Here's the syntax for a `try...except...else` block in Python:

```python
try:
    # Code that might raise an exception
    risky_code()
except SomeException as e:
    # Code to handle the exception
    print(f"An error occurred: {e}")
else:
    # Code that runs if no exceptions were raised in the try block
    print("No errors occurred!")
```

#### Key Points:
1. **`try` Block:** Contains the code that might raise an exception.
2. **`except` Block:** Handles exceptions that occur in the `try` block. You can specify the exception type(s) to catch.
3. **`else` Block:** Runs only if no exceptions occur in the `try` block.
4. **Optional:** You can use multiple `except` clauses for handling different exceptions.

#### Example:

```python
try:
    num = int(input("Enter a number: "))
    result = 10 / num
except ValueError:
    print("Invalid input! Please enter a valid integer.")
except ZeroDivisionError:
    print("Division by zero is not allowed.")
else:
    print(f"The result is {result}.")
```

**Interaction Example:**
```
Enter a number: 5
The result is 2.0
```

**If an exception occurs:**
```
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

The `match` statement in Python enables structured pattern matching, offering a powerful way to handle various data scenarios. This feature is inspired by languages like Rust and Haskell and is more versatile than traditional `switch` statements in languages like C, Java, or JavaScript.

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
Here, the `_` serves as a wildcard, matching any value not explicitly handled by other cases.

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
    case (0, y):
        print(f"Y={y}")
    case (x, 0):
        print(f"X={x}")
    case (x, y):
        print(f"X={x}, Y={y}")
    case _:
        raise ValueError("Not a point")
```

### Matching Objects with Attributes
Class instances can be matched using patterns resembling constructors, binding attributes to variables.

#### Example: Object Matching
```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

def where_is(point):
    match point:
        case Point(x=0, y=0):
            print("Origin")
        case Point(x=0, y=y):
            print(f"Y={y}")
        case Point(x=x, y=0):
            print(f"X={x}")
        case Point():
            print("Somewhere else")
        case _:
            print("Not a point")
```

### Using `__match_args__`
The `__match_args__` attribute specifies the order of attributes for positional matching.
```python
class Point:
    __match_args__ = ('x', 'y')
    def __init__(self, x, y):
        self.x = x
        self.y = y

match point:
    case Point(1, var):
        print(f"Y={var}")
    case Point(x=1, y=var):
        print(f"Y={var}")
```

### Nested Patterns
Patterns can be nested for complex matching scenarios.

#### Example: Matching Lists of Objects
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
Guards can add conditions to patterns, filtering matches further.

#### Example: Guard in Pattern
```python
match point:
    case Point(x, y) if x == y:
        print(f"Y=X at {x}")
    case Point(x, y):
        print(f"Not on the diagonal")
```

### Additional Features of `match`
1. **Sequence Patterns:**
   - Match arbitrary sequences like lists or tuples (not iterators or strings).
   - Support extended unpacking with `*`:
     ```python
     case [x, y, *rest]:
         print(f"First: {x}, Second: {y}, Rest: {rest}")
     ```

2. **Mapping Patterns:**
   - Match dictionaries by keys:
     ```python
     case {"bandwidth": b, "latency": l}:
         print(f"Bandwidth={b}, Latency={l}")
     ```

3. **Capturing Subpatterns with `as`:**
   - Capture parts of a pattern:
     ```python
     case (Point(x1, y1), Point(x2, y2) as p2):
         print(f"Second point: {p2}")
     ```

4. **Literal Comparison:**
   - Most literals are compared by equality.
   - `True`, `False`, and `None` are compared by identity.

5. **Named Constants:**
   - Prevent interpretation as capture variables using dotted names:
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

## Function

### Key Features of Defining Functions

1. **Basic Syntax**:  
   - The `def` keyword introduces a function definition.  
   - The function name is followed by parentheses containing a comma-separated list of parameters.  
   - The function body is indented and may include a **docstring** as its first statement to document the function.

   Example:
   ```python
   def fib(n):
       """Print Fibonacci series less than n."""
       a, b = 0, 1
       while a < n:
           print(a, end=' ')
           a, b = b, a + b
       print()
   ```

2. **Calling Functions**:  
   Functions are executed when called, e.g., `fib(2000)`.

3. **Docstrings**:  
   A function can have an optional docstring (enclosed in triple quotes) to describe its purpose. Docstrings are good practice and help in generating documentation or for interactive use.

---

### Variable Scope and Symbol Tables

1. **Local Symbol Table**:  
   - Each function call creates a new local symbol table for its variables.  
   - Variables are first looked up in the local table, then in enclosing functions' tables, global scope, and finally in built-in names.

2. **Global and Nonlocal Variables**:  
   - To assign to global variables, use the `global` statement.  
   - For variables in enclosing functions, use the `nonlocal` statement.

     * **Global Variables Example**

      The `global` keyword is used when you want to modify a variable defined at the global (module) level inside a function.

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
      ```

      **Output**:
      ```
      Counter inside function: 1
      Counter inside function: 2
      Counter outside function: 2
      ```

      Without the `global` statement, the function would create a new local variable `counter`, and the global `counter` would remain unchanged.

      ---

     * **Nonlocal Variables Example**

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
      ```

      **Output**:
      ```
      Count inside inner function: 1
      Count inside inner function: 2
      Count in outer function: 2
      ```

      Without the `nonlocal` statement, `count` inside `inner_function` would be treated as a local variable, and modifying it would result in an error since it's referenced before assignment.

      ---

     * **Combining Both**

      You can use both `global` and `nonlocal` in different parts of a nested function hierarchy.

      ```python
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
      ```

      **Output**:
      ```
      Global x modified: 11
      Enclosing x modified: 6
      Global x outside: 11
      ```


3. **Argument Passing**:  
   - Arguments are passed by **object reference** (commonly called "call by value" where the value is a reference to the object).  
   - Mutable objects can be modified within the function.

---

### Functions as Objects

1. **Function Objects**:  
   - Functions are objects and can be assigned to other names, enabling aliasing.  
   Example:
   ```python
   f = fib
   f(100)  # Calls the same function as fib(100)
   ```

2. **Return Values**:  
   - Functions without a `return` statement return `None`.  
   - Explicitly returning `None` or falling off the end of the function behaves the same.  

---

### Returning Values

1. **Returning a Value**:  
   Use the `return` statement to return a value from a function.
   ```python
   def fib2(n):
       """Return a list containing Fibonacci series up to n."""
       result = []
       a, b = 0, 1
       while a < n:
           result.append(a)
           a, b = b, a + b
       return result
   ```

2. **Calling and Using Return Values**:  
   The result of the function can be stored and manipulated.
   ```python
   f100 = fib2(100)
   print(f100)  # Output: [0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
   ```

---

### Notable Python Features Demonstrated

1. **Method Calls**:  
   - The `append()` method adds elements to a list efficiently.
   - Example:
     ```python
     result.append(a)
     ```
     This is equivalent to `result = result + [a]` but more efficient.

2. **Returning Multiple Values**:  
   - Python allows returning multiple values as a tuple.  
     ```python
     def example():
         return 1, 2, 3
     x, y, z = example()
     ```

3. **Call by Object Reference**:  
   - If a mutable object (e.g., a list) is passed as an argument, modifications inside the function are reflected outside.

---

### Default Argument Values

Default argument values in Python allow functions to be called with fewer arguments than they are defined to accept. This provides flexibility and avoids repetitive argument passing in common use cases.

1. **Basic Syntax**:
   - Default values are defined by assigning values to parameters in the function definition.
   - For example:
     ```python
     def ask_ok(prompt, retries=4, reminder='Please try again!'):
         ...
     ```

2. **Function Usage**:
   - You can call such functions in multiple ways:
     - **Only mandatory argument**: `ask_ok('Do you really want to quit?')`
     - **One optional argument**: `ask_ok('OK to overwrite the file?', 2)`
     - **All arguments**: `ask_ok('OK to overwrite the file?', 2, 'Come on, only yes or no!')`

3. **Evaluation of Default Values**:
   - Default values are evaluated **at the time of function definition**, not at runtime.
   - Example:
     ```python
     i = 5
     def f(arg=i):
         print(arg)
     i = 6
     f()  # Prints 5 because the value of `i` was captured when the function was defined.
     ```

4. **Using Mutable Default Arguments**:
   - Default values are evaluated **only once**, which can lead to unintended behavior if the default is a mutable object (like a list or dictionary).
   - Example of unintended behavior:
     ```python
     def f(a, L=[]):
         L.append(a)
         return L
     print(f(1))  # [1]
     print(f(2))  # [1, 2]
     print(f(3))  # [1, 2, 3]
     ```
     The list `L` persists across calls because it is shared between calls.

5. **Avoiding Mutable Defaults**:
   - To avoid this issue, use `None` as the default value and initialize the mutable object inside the function:
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

#### **Best Practices**
- Avoid using mutable objects as default values to prevent unexpected behavior.
- Use `None` as the default and explicitly initialize mutable objects inside the function body.
- Always consider how the default value's evaluation timing might affect function behavior.

### Keyword Arguments

Keyword arguments allow functions to be called with arguments explicitly named using the format `kwarg=value`. This enhances flexibility, clarity, and allows positional and optional arguments to be mixed effectively.

---

1. **Basic Usage**:
   - A function can have required positional arguments and optional keyword arguments:
     ```python
     def parrot(voltage, state='a stiff', action='voom', type='Norwegian Blue'):
         print("-- This parrot wouldn't", action, end=' ')
         print("if you put", voltage, "volts through it.")
         print("-- Lovely plumage, the", type)
         print("-- It's", state, "!")
     ```
   - Example calls:
     ```python
     parrot(1000)                                # 1 positional argument
     parrot(voltage=1000)                        # 1 keyword argument
     parrot(voltage=1000000, action='VOOOOOM')   # 2 keyword arguments
     parrot(action='VOOOOOM', voltage=1000000)   # Order doesn't matter for keyword arguments
     parrot('a million', 'bereft of life', 'jump')  # 3 positional arguments
     parrot('a thousand', state='pushing up the daisies')  # Mixed positional and keyword
     ```

2. **Invalid Calls**:
   - Missing required arguments: `parrot()` → Error.
   - Mixing positional arguments after keyword arguments: `parrot(voltage=5.0, 'dead')` → Error.
   - Providing multiple values for the same argument: `parrot(110, voltage=220)` → Error.
   - Using unknown arguments: `parrot(actor='John Cleese')` → Error.

3. **Rules for Keyword Arguments**:
   - Keyword arguments must **follow all positional arguments**.
   - Each argument can receive a value only once.
   - The order of keyword arguments in the function call does not matter.
   - All keyword arguments must match the parameter names in the function definition.

4. **Using `*args` and `**kwargs`**:
   - The `*args` parameter collects additional positional arguments into a tuple.
   - The `**kwargs` parameter collects additional keyword arguments into a dictionary.
   - Example:
     ```python
     def cheeseshop(kind, *arguments, **keywords):
         print("-- Do you have any", kind, "?")
         print("-- I'm sorry, we're all out of", kind)
         for arg in arguments:
             print(arg)
         print("-" * 40)
         for kw in keywords:
             print(kw, ":", keywords[kw])
     ```
   - Example call:
     ```python
     cheeseshop(
         "Limburger",
         "It's very runny, sir.",
         "It's really very, VERY runny, sir.",
         shopkeeper="Michael Palin",
         client="John Cleese",
         sketch="Cheese Shop Sketch"
     )
     ```
   - Output:
     ```
     -- Do you have any Limburger ?
     -- I'm sorry, we're all out of Limburger
     It's very runny, sir.
     It's really very, VERY runny, sir.
     ----------------------------------------
     shopkeeper : Michael Palin
     client : John Cleese
     sketch : Cheese Shop Sketch
     ```

5. **Order of Printing Keyword Arguments**:
   - The order in which keyword arguments are printed matches the order they are provided during the function call.

---

#### **Best Practices**
- Use keyword arguments to improve function call clarity and avoid mistakes in argument order.
- Use `*args` and `**kwargs` when creating flexible functions that can handle variable numbers of arguments.
- Ensure that all required arguments are provided, either positionally or by name.

---

### Special Parameters

Python allows arguments to be passed to functions by position or by keyword. For clarity and better control, the way arguments are passed can be restricted using special symbols (`/` and `*`) in function definitions. These symbols define **positional-only**, **positional-or-keyword**, and **keyword-only** arguments.

---

#### Key Types of Parameters

1. **Positional-or-Keyword Arguments**:
   - Default behavior when `/` and `*` are not used.
   - Arguments can be passed by position or keyword.
   - Example:
     ```python
     def standard_arg(arg):
         print(arg)
     standard_arg(2)         # Positional
     standard_arg(arg=2)     # Keyword
     ```

2. **Positional-Only Parameters**:
   - Defined by placing a `/` in the function definition.
   - Arguments must be passed by position; using keywords for these parameters raises an error.
   - Useful for enforcing strict argument order or preventing reliance on parameter names.
   - Example:
     ```python
     def pos_only_arg(arg, /):
         print(arg)
     pos_only_arg(1)         # Valid
     pos_only_arg(arg=1)     # TypeError: argument must be positional
     ```

3. **Keyword-Only Parameters**:
   - Defined by placing a `*` before the first keyword-only parameter.
   - These arguments must be passed by keyword, not position.
   - Useful for explicit function calls where argument names add clarity.
   - Example:
     ```python
     def kwd_only_arg(*, arg):
         print(arg)
     kwd_only_arg(arg=3)     # Valid
     kwd_only_arg(3)         # TypeError: argument must be a keyword
     ```

4. **Combined Use of `/` and `*`**:
   - A function can mix all three parameter types: positional-only, positional-or-keyword, and keyword-only.
   - Example:
     ```python
     def combined_example(pos_only, /, standard, *, kwd_only):
         print(pos_only, standard, kwd_only)

     combined_example(1, 2, kwd_only=3)          # Valid
     combined_example(1, standard=2, kwd_only=3) # Valid
     combined_example(pos_only=1, standard=2, kwd_only=3)  # TypeError
     ```

---

#### Special Cases

1. **Handling Name Collisions**:
   - Positional-only arguments can avoid conflicts with `**kwargs`.
   - Example:
     ```python
     def foo(name, /, **kwds):
         return 'name' in kwds

     foo(1, **{'name': 2})  # True
     ```
   - Here, `name` is treated as a positional argument, allowing `name` to also appear in the `**kwds` dictionary.

2. **Errors and Ambiguities**:
   - Using the same parameter as both positional and keyword:
     ```python
     def foo(name, **kwds):
         return 'name' in kwds
     foo(1, **{'name': 2})  # TypeError: multiple values for argument 'name'
     ```

---

#### Guidelines for Usage

1. **Positional-Only Parameters**:
   - Use when parameter names are irrelevant or could change without breaking the API.
   - Enforce strict argument order for readability and performance.

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

---

#### Advantages

- **Readability**: Restricting argument passing improves code clarity by showing intent directly in the function signature.
- **Robust APIs**: Helps prevent breaking changes in APIs when parameter names are modified.
- **Control**: Allows developers to enforce positional arguments or require explicit naming for clarity and maintainability.

### Arbitrary Argument Lists
- Functions can accept an arbitrary number of arguments, which are gathered into a tuple using the `*args` syntax. These variadic arguments must appear after any normal positional arguments.
- Example: `write_multiple_items(file, separator, *args)` where `args` is a tuple containing extra arguments.
- Keyword-only arguments must be placed after the `*args` parameter and can only be passed as keywords, not positional arguments.
- Example of a function with arbitrary arguments: 
  ```python
  def concat(*args, sep="/"):
      return sep.join(args)
  ```
  It can be called with or without specifying the separator:
  ```python
  concat("earth", "mars", "venus")  # 'earth/mars/venus'
  concat("earth", "mars", "venus", sep=".")  # 'earth.mars.venus'
  ```

### Unpacking Argument Lists
- When arguments are already stored in a list or tuple, they can be unpacked using the `*` operator in function calls that require separate positional arguments.
- Example of unpacking arguments for the `range()` function:
  ```python
  args = [3, 6]
  list(range(*args))  # [3, 4, 5]
  ```
- Similarly, dictionaries can be used to pass keyword arguments to functions using the `**` operator.
- Example of using a dictionary for keyword arguments:
  ```python
  def parrot(voltage, state='a stiff', action='voom'):
      print(f"-- This parrot wouldn't {action} if you put {voltage} volts through it. E's {state}!")
  d = {"voltage": "four million", "state": "bleedin' demised", "action": "VOOM"}
  parrot(**d)  # Output: -- This parrot wouldn't VOOM if you put four million volts through it. E's bleedin' demised!
  ```

---

### Function Annotations

**Function annotations** in Python provide a way to add metadata to the parameters and return values of functions. They are optional and serve as a way to document the types or other properties of function inputs and outputs. Function annotations have no impact on the execution of the function, but they can be accessed programmatically for purposes such as documentation or type checking.

1. **Syntax of Annotations:**
   - **Parameter Annotations**: A colon `:` is used after the parameter name, followed by an expression that evaluates to the annotation.
   - **Return Annotations**: A literal `->` is used before the return type annotation, placed between the parameter list and the colon that ends the `def` statement.

   Example:
   ```python
   def f(ham: str, eggs: str = 'eggs') -> str:
       return ham + ' and ' + eggs
   ```

2. **How Annotations are Stored:**
   - Annotations are stored in the `__annotations__` attribute of the function as a dictionary.
   - The dictionary keys are the parameter names (and 'return' for the return type), and the values are the corresponding annotations.

3. **Example:**
   In the following example, the function `f` has annotated parameters and a return type:
   ```python
   def f(ham: str, eggs: str = 'eggs') -> str:
       print("Annotations:", f.__annotations__)
       print("Arguments:", ham, eggs)
       return ham + ' and ' + eggs
   ```
   Output:
   ```
   Annotations: {'ham': <class 'str'>, 'eggs': <class 'str'>, 'return': <class 'str'>}
   Arguments: spam eggs
   'spam and eggs'
   ```
   - **Annotations**: The `__annotations__` attribute shows that both `ham` and `eggs` are of type `str`, and the return value is also a `str`.

4. **No Effect on Function Behavior:**
   - Function annotations are purely for documentation and do not affect how the function operates. They don't enforce type checking at runtime.

5. **Use Cases:**
   - Annotations are useful for tools that perform type checking, static analysis, or for generating documentation automatically.
   
Function annotations in Python allow developers to add metadata to function parameters and return values. While they do not affect execution, they provide valuable information for tools and documentation. They are stored in the `__annotations__` attribute as a dictionary, and their syntax follows a simple pattern of `parameter_name: annotation` for parameters and `-> return_annotation` for the return type.

---

## Lambda Expressions

Lambda expressions provide a concise way to define **small, anonymous** functions. These functions are syntactically limited to a single expression, but they can be used wherever a function object is required. Although lambda functions are often viewed as a more compact alternative to traditional function definitions, they are semantically equivalent to standard functions.

### Syntax and Structure:
A lambda expression follows this syntax:
```python
lambda arguments: expression
```
- **Arguments**: The input parameters to the function (can be zero or more).
- **Expression**: A single expression that gets evaluated and returned when the function is called.

#### Example:
A simple lambda function that adds two arguments:
```python
lambda a, b: a + b
```

### Key Characteristics:
1. **Single Expression**: Lambda functions can only contain one expression. Unlike regular functions, which can have multiple statements, lambda functions are limited to a single expression that is evaluated and returned.
2. **Syntactic Sugar**: Lambda expressions are a more concise way to define functions but are functionally equivalent to a normal function definition.
3. **Can Reference Outer Variables**: Like nested functions, lambda functions can access variables from the enclosing scope.

### Example of Lambda in Practice:
A function `make_incrementor` returns a lambda function that increments its argument by a given value:
```python
def make_incrementor(n):
    return lambda x: x + n
```
Usage:
```python
f = make_incrementor(42)
print(f(0))  # Output: 42
print(f(1))  # Output: 43
```
Here, the lambda function adds `n` (in this case, 42) to its argument `x`. The lambda expression is returned and stored in `f`.

### Lambda Functions as Arguments:
Lambda expressions are often used as arguments in functions that require a function object. This allows for passing small, one-off functions without having to define a full function.

#### Example of Using Lambda in Sorting:
In this example, we use a lambda function to specify the key by which a list of tuples should be sorted:
```python
pairs = [(1, 'one'), (2, 'two'), (3, 'three'), (4, 'four')]
pairs.sort(key=lambda pair: pair[1])
print(pairs)  # Output: [(4, 'four'), (1, 'one'), (3, 'three'), (2, 'two')]
```
Here, the lambda function `lambda pair: pair[1]` tells the `sort()` method to sort the tuples based on the second element (the string) of each pair.

### Use Cases:
- **Short, anonymous functions**: Lambda expressions are useful for defining small, throwaway functions that don't need to be reused elsewhere.
- **Functional arguments**: Lambda functions are often passed as arguments to higher-order functions, such as `sort()`, `map()`, `filter()`, and `reduce()`.

## Documentation Strings

Documentation strings (also known as docstrings) in Python provide a way to document the purpose, behavior, and usage of functions, classes, and modules. Python has a specific convention for formatting these docstrings to ensure consistency and clarity. 

### Key Conventions for Writing Documentation Strings:

### Concise Summary in the First Line
   - The first line of a docstring should offer a short and clear summary of the object's purpose or behavior. 
   - **Do not include the object's name or type** in this summary unless the name is a verb describing the function's operation (e.g., `fetch_data()` might be summarized as "Fetches data from the server").
   - The first line should begin with a capital letter and end with a period.

   Example:
   ```python
   def fetch_data():
       """Fetches data from the server."""
       pass
   ```

### Blank Line Separating Summary from Further Details
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

### Multi-line Docstrings and Indentation
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
       
       No, really, it doesn't do anything.
       """
       pass
   ```

   When printed, this would display as:
   ```python
   print(my_function.__doc__)
   ```
   Output:
   ```
   Do nothing, but document it.
   
   No, really, it doesn't do anything.
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

Let's look at coding style guidelines that promote readability and maintainability in Python code. By adhering to these conventions, developers can write code that is easier for others to read, understand, and maintain. The guidelines are based on **[PEP 8](https://peps.python.org/pep-0008/)**, which is the official style guide for Python.

### Key Guidelines from PEP 8:

1. **Indentation**:
   - Use **4 spaces** for indentation, not tabs.
   - **Why?**: 4 spaces provide a good balance between readability and compactness, while tabs can cause confusion due to potential tab width differences across environments.

2. **Line Length**:
   - Wrap lines so that they **don’t exceed 79 characters**.
   - **Why?**: This makes it easier to read code on smaller displays and allows multiple files to be viewed side-by-side on larger screens.

3. **Blank Lines**:
   - Use **blank lines** to separate functions, classes, and larger code blocks inside functions.
   - **Why?**: Blank lines improve readability and help separate logical sections of the code.

4. **Comments**:
   - When possible, place comments **on their own line**.
   - Use **docstrings** for documenting functions, classes, and methods.
   - **Why?**: Clear and concise comments help explain the code's logic, making it easier for others to understand.

5. **Spacing Around Operators**:
   - Use **spaces around operators** and **after commas**, but **not inside brackets** (e.g., `a = f(1, 2) + g(3, 4)`).
   - **Why?**: Consistent spacing makes the code more visually appealing and easier to read.

6. **Naming Conventions**:
   - **Classes** should be named using **UpperCamelCase**.
   - **Functions and methods** should be named using **lowercase_with_underscores**.
   - Always use `self` as the first argument for methods in classes.
   - **Why?**: Consistent naming makes it easier to recognize different types of code elements (classes vs. functions).

7. **Character Encoding**:
   - **Avoid using fancy encodings**. Stick to **UTF-8** or **plain ASCII**.
   - **Why?**: Using a standard encoding ensures compatibility across various environments and platforms.

8. **Non-ASCII Characters**:
   - Avoid **non-ASCII characters in identifiers** if the code is likely to be used or maintained by people who may not speak the same language.
   - **Why?**: Using non-ASCII characters can cause issues in international environments and may be confusing to non-native speakers.

---

# Data Structures

## List 

Python lists are versatile, mutable sequences that can hold an ordered collection of items. 

---

### **List Methods Overview**

The following table summarizes the key methods available for Python lists:

| **Method**            | **Description**                                                                                       | **Return Type**  | **Example Usage**                                    |
|------------------------|-------------------------------------------------------------------------------------------------------|-------------------|-----------------------------------------------------|
| `list.append(x)`      | Adds `x` to the end of the list.                                                                      | `None`           | `a.append(10)`                                      |
| `list.extend(iterable)` | Appends all elements from `iterable` to the list.                                                   | `None`           | `a.extend([4, 5, 6])`                              |
| `list.insert(i, x)`   | Inserts `x` at position `i`.                                                                          | `None`           | `a.insert(1, "item")`                              |
| `list.remove(x)`      | Removes the first occurrence of `x`. Raises `ValueError` if `x` is not found.                         | `None`           | `a.remove("item")`                                 |
| `list.pop(i)`         | Removes and returns the element at position `i` (last item if `i` is omitted). Raises `IndexError`.   | `Element`        | `a.pop(2)`                                         |
| `list.clear()`        | Removes all elements from the list.                                                                   | `None`           | `a.clear()`                                        |
| `list.index(x, start, end)` | Returns the index of the first occurrence of `x` in the list. Searches within `[start:end]`.      | `int`            | `a.index("item", 1, 5)`                            |
| `list.count(x)`       | Counts the number of occurrences of `x` in the list.                                                  | `int`            | `a.count(10)`                                      |
| `list.sort(*, key=None, reverse=False)` | Sorts the list in-place. Accepts optional `key` for custom sorting and `reverse`.      | `None`           | `a.sort(reverse=True)`                             |
| `list.reverse()`      | Reverses the list in-place.                                                                           | `None`           | `a.reverse()`                                      |
| `list.copy()`         | Returns a shallow copy of the list.                                                                   | `list`           | `b = a.copy()`                                     |

---

### **Detailed Examples**

Here’s how some of the methods work with examples:

#### **Counting Elements**
```python
fruits = ['orange', 'apple', 'pear', 'banana', 'kiwi', 'apple', 'banana']
print(fruits.count('apple'))  # Output: 2
print(fruits.count('tangerine'))  # Output: 0
```

#### **Finding Indices**
```python
print(fruits.index('banana'))  # Output: 3
print(fruits.index('banana', 4))  # Search starting at position 4. Output: 6
```

#### **Reversing and Sorting**
```python
fruits.reverse()
print(fruits)  # Output: ['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange']

fruits.sort()
print(fruits)  # Output: ['apple', 'apple', 'banana', 'banana', 'grape', 'kiwi', 'orange', 'pear']
```

#### **Popping and Appending**
```python
fruits.append('grape')
print(fruits)  # Adds 'grape' to the list.

last_item = fruits.pop()
print(last_item)  # Removes and returns 'pear'.
```

---

### **Important Notes**

1. **Methods Without Return Values:**
   - Methods like `insert`, `remove`, `sort`, `reverse`, and `append` modify the list in place and return `None`. This design ensures clarity when dealing with mutable structures.

2. **Type Restrictions in Sorting:**
   - Sorting is not defined for all data types.
     - Example: `[None, 'hello', 10]` will raise an error because integers cannot be compared with strings, nor can `None` be compared to other types.
     - Similarly, complex numbers do not have a defined ordering: `3+4j < 5+7j` is invalid.

3. **Mutability:**
   - Lists are mutable, meaning their contents can be changed after creation.

---

### **Sample Code to Explore List Methods**
The following code demonstrates the usage of most list methods:

```python
# Example List
fruits = ['orange', 'apple', 'pear', 'banana', 'kiwi', 'apple', 'banana']

# Count occurrences
print(fruits.count('apple'))  # Output: 2

# Index search
print(fruits.index('banana'))  # Output: 3

# Reverse the list
fruits.reverse()
print(fruits)

# Append and Pop
fruits.append('grape')
print(fruits)
print(fruits.pop())  # Removes 'grape'

# Sort the list
fruits.sort()
print(fruits)

# Clear the list
fruits.clear()
print(fruits)  # Output: []
```

---

### **Using Lists as Stacks**

A **stack** operates on a Last-In, First-Out (LIFO) principle. Python lists support stack operations with the following methods:
- **`append()`**: Adds an item to the top of the stack.
- **`pop()`**: Removes and returns the item from the top of the stack.

#### **Example**
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

#### **Key Characteristics**
- Operations (`append` and `pop`) are efficient since they occur at the end of the list.
- Suitable for use cases where LIFO order is needed.

---

### **Using Lists as Queues**

A **queue** operates on a First-In, First-Out (FIFO) principle. While Python lists can be used as queues:
- **`pop(0)`**: Removes and returns the first element.
- **`append()`**: Adds an item to the end of the list.

However, **lists are not ideal for queues** due to inefficiency:
- **Removing from the beginning (`pop(0)`)** requires shifting all subsequent elements, which is slow for large lists.

#### **Recommended Alternative: `collections.deque`**
- Designed for fast appends and pops at both ends.
- Efficient for queue implementations.

#### **Example with `deque`**
```python
from collections import deque

queue = deque(["Eric", "John", "Michael"])
queue.append("Terry")  # Add Terry to the queue
queue.append("Graham")  # Add Graham to the queue

queue.popleft()  # Removes and returns 'Eric'
queue.popleft()  # Removes and returns 'John'
print(queue)     # Output: deque(['Michael', 'Terry', 'Graham'])
```

#### **Key Characteristics**
- Efficient for FIFO operations.
- Supports both appends and pops from either end of the queue.

---

### **Comparison of Stack and Queue**

| **Feature**         | **Stack**                     | **Queue (List)**                | **Queue (`deque`)**             |
|----------------------|-------------------------------|----------------------------------|----------------------------------|
| **Order**           | Last-In, First-Out (LIFO)    | First-In, First-Out (FIFO)      | First-In, First-Out (FIFO)      |
| **Primary Methods** | `append()`, `pop()`           | `append()`, `pop(0)`            | `append()`, `popleft()`         |
| **Performance**     | Fast for `append` and `pop`   | Slow for `pop(0)`               | Fast for both ends              |
| **Ideal Use Case**  | Stacks or LIFO structures     | Small, occasional FIFO queues   | Large, frequent FIFO queues     |

---

### **Detailed Summary: List Comprehensions and Nested List Comprehensions**

---

### **List Comprehensions**
List comprehensions offer a concise, readable way to construct lists, applying operations or filters to elements from other sequences or iterables.

#### **Syntax**
```python
[expression for item in iterable if condition]
```
- **`expression`**: Defines how each element is processed.
- **`for item in iterable`**: Iterates over the sequence.
- **`if condition`** *(optional)*: Filters elements based on a condition.

---

#### **Examples and Use Cases**

##### **Basic Examples**
1. **Creating a List of Squares:**
   ```python
   squares = [x**2 for x in range(10)]
   print(squares)  # Output: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
   ```

2. **Combining Elements from Two Lists (With a Condition):**
   ```python
   combs = [(x, y) for x in [1, 2, 3] for y in [3, 1, 4] if x != y]
   print(combs)  
   # Output: [(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
   ```

##### **Operations on List Elements**
1. **Doubling Elements:**
   ```python
   vec = [-4, -2, 0, 2, 4]
   doubled = [x * 2 for x in vec]
   print(doubled)  # Output: [-8, -4, 0, 4, 8]
   ```

2. **Filtering Negative Numbers:**
   ```python
   filtered = [x for x in vec if x >= 0]
   print(filtered)  # Output: [0, 2, 4]
   ```

3. **Applying a Function:**
   ```python
   abs_values = [abs(x) for x in vec]
   print(abs_values)  # Output: [4, 2, 0, 2, 4]
   ```

4. **Calling Methods:**
   ```python
   freshfruit = [' banana', ' loganberry ', 'passion fruit ']
   stripped = [fruit.strip() for fruit in freshfruit]
   print(stripped)  # Output: ['banana', 'loganberry', 'passion fruit']
   ```

##### **Complex Examples**
1. **Creating Tuples:**
   ```python
   squares_tuples = [(x, x**2) for x in range(6)]
   print(squares_tuples)  
   # Output: [(0, 0), (1, 1), (2, 4), (3, 9), (4, 16), (5, 25)]
   ```

2. **Flattening Nested Lists:**
   ```python
   vec = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
   flattened = [num for sublist in vec for num in sublist]
   print(flattened)  # Output: [1, 2, 3, 4, 5, 6, 7, 8, 9]
   ```

3. **Using Mathematical Functions:**
   ```python
   from math import pi
   rounded_pi = [str(round(pi, i)) for i in range(1, 6)]
   print(rounded_pi)  # Output: ['3.1', '3.14', '3.142', '3.1416', '3.14159']
   ```

---

### **Nested List Comprehensions**
Nested list comprehensions allow processing nested structures, such as lists of lists.

#### **Example: Matrix Transposition**
##### **Matrix Representation:**
```python
matrix = [
    [1, 2, 3, 4],
    [5, 6, 7, 8],
    [9, 10, 11, 12]
]
```

##### **Using Nested List Comprehension:**
```python
transposed = [[row[i] for row in matrix] for i in range(4)]
print(transposed)
# Output: [[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```

##### **Equivalent Code Without List Comprehension:**
```python
transposed = []
for i in range(4):
    transposed_row = []
    for row in matrix:
        transposed_row.append(row[i])
    transposed.append(transposed_row)
print(transposed)
```

##### **Using Built-In Functions:**
The `zip()` function simplifies matrix transposition:
```python
transposed = list(zip(*matrix))
print(transposed)
# Output: [(1, 5, 9), (2, 6, 10), (3, 7, 11), (4, 8, 12)]
```

---

#### **Key Considerations**
1. **Parentheses for Tuples:**
   When creating tuples in a comprehension, enclose them in parentheses to avoid syntax errors:
   ```python
   [(x, x**2) for x in range(6)]
   ```

2. **Performance:**
   - List comprehensions are faster and more readable than loops.
   - Avoid excessive nesting for maintainability; use built-ins like `zip()` when possible.

3. **Readability:**
   - Complex comprehensions may reduce clarity. Favor simplicity or explanatory comments for nested structures.

---

#### **Comparison Table: List Comprehensions and Nested Loops**

| **Feature**                     | **List Comprehension**                      | **Nested Loops**                               |
|----------------------------------|---------------------------------------------|-----------------------------------------------|
| **Syntax**                      | `[expression for x in iterable if cond]`    | Explicit loops and conditions                 |
| **Readability**                 | Concise, more readable for simple cases     | Clear for complex or multi-step processes     |
| **Performance**                 | Faster in most cases                        | Slightly slower for large datasets            |
| **Use Cases**                   | Quick data transformation or filtering      | Complex workflows or multi-step logic         |

---

## The `del` Statement**

---

The `del` statement in Python provides a flexible way to remove elements from lists, slices of lists, or even entire variables. Unlike the `pop()` method, which removes an element and returns its value, `del` removes elements without returning anything. This makes it ideal for scenarios where returning a value is unnecessary.

---

### **Key Features and Use Cases**

#### 1. **Removing an Item by Index**
- The `del` statement removes an element from a list based on its **index**.
- Example:
  ```python
  a = [-1, 1, 66.25, 333, 333, 1234.5]
  del a[0]  # Removes the first element
  print(a)  # Output: [1, 66.25, 333, 333, 1234.5]
  ```

---

#### 2. **Removing Slices**
- It can also delete multiple elements by specifying a **slice**.
- Example:
  ```python
  a = [1, 66.25, 333, 333, 1234.5]
  del a[2:4]  # Removes elements from index 2 to 3
  print(a)  # Output: [1, 66.25, 1234.5]
  ```

- Slices provide a powerful way to handle contiguous ranges of elements without using loops.

---

#### 3. **Clearing the Entire List**
- Assigning an empty slice effectively clears all elements of the list.
- Example:
  ```python
  a = [1, 66.25, 1234.5]
  del a[:]  # Removes all elements
  print(a)  # Output: []
  ```

---

#### 4. **Deleting Entire Variables**
- The `del` statement can delete an entire variable, making it unavailable for further use.
- Example:
  ```python
  del a  # Deletes the variable `a`
  # Accessing `a` now would raise a NameError
  ```

---

### **Key Differences Between `del` and Other Methods**

| **Feature**            | **`del` Statement**                              | **`pop()` Method**                       | **Assignment (`a[:] = []`)**            |
|-------------------------|-------------------------------------------------|------------------------------------------|------------------------------------------|
| **Purpose**             | Remove items or slices; delete variables.       | Remove an item and return its value.     | Clear all elements of a list.           |
| **Returns a Value?**    | No                                              | Yes                                      | No                                       |
| **Scope**               | Can delete entire variables.                    | Limited to removing specific elements.   | Limited to list clearing.               |

---

### **Advantages of Using `del`**
1. **Flexibility**: 
   - Can handle individual elements, slices, or the entire list.
   - Works on non-list objects, such as deleting variables.

2. **Efficiency**: 
   - Eliminates the need for iterative loops when removing multiple elements or slices.

3. **Clear Intent**: 
   - Explicitly communicates the intention to delete an item, slice, or variable.

---

### **Practical Considerations**
- **Safety**: Use `del` cautiously when deleting slices or variables, as unintended deletions may lead to runtime errors.
- **Readability**: In cases where the list must be cleared, `a[:] = []` is a more explicit alternative than `del a[:]`.

---

### **Examples for Context**
1. **Use in a Function:**
   ```python
   def remove_middle(lst):
       del lst[len(lst) // 2]
   numbers = [10, 20, 30, 40, 50]
   remove_middle(numbers)
   print(numbers)  # Output: [10, 20, 40, 50]
   ```

2. **Efficient List Management:**
   ```python
   a = [1, 2, 3, 4, 5]
   del a[1:4]  # Remove a slice
   print(a)  # Output: [1, 5]
   ```

3. **Variable Deletion:**
   ```python
   x = 100
   del x
   # Trying to print `x` now will raise NameError
   ```

---

## Tuples and Sequences

Tuples are one of Python's sequence data types, alongside lists and strings. While they share certain properties with other sequences, like indexing and slicing, they have distinct features and use cases.

---

### **Key Features of Tuples**

1. **Definition and Syntax:**
   - A tuple is a collection of values separated by commas.
   - Example:
     ```python
     t = 12345, 54321, 'hello!'
     print(t[0])  # Output: 12345
     print(t)     # Output: (12345, 54321, 'hello!')
     ```
   - Parentheses are optional when defining tuples, but they are often required for clarity or in larger expressions.

2. **Immutability:**
   - Tuples are immutable, meaning their elements cannot be modified after creation.
   - Example:
     ```python
     t[0] = 88888  # Raises TypeError
     ```

3. **Heterogeneous and Nested Elements:**
   - Tuples often hold heterogeneous data (elements of different types).
   - They support nesting:
     ```python
     u = t, (1, 2, 3, 4, 5)
     print(u)  # Output: ((12345, 54321, 'hello!'), (1, 2, 3, 4, 5))
     ```

4. **Mutable Objects in Tuples:**
   - Tuples can contain mutable objects, such as lists:
     ```python
     v = ([1, 2, 3], [3, 2, 1])
     print(v)  # Output: ([1, 2, 3], [3, 2, 1])
     ```

---

### **Differences Between Tuples and Lists**

| **Aspect**            | **Tuples**                               | **Lists**                          |
|-----------------------|------------------------------------------|------------------------------------|
| **Mutability**        | Immutable                                | Mutable                           |
| **Purpose**           | Heterogeneous data; fixed structure      | Homogeneous data; dynamic changes |
| **Access**            | By unpacking or indexing                | By iteration or indexing          |

---

### **Special Cases**

1. **Empty Tuples:**
   - Defined using an empty pair of parentheses:
     ```python
     empty = ()
     print(len(empty))  # Output: 0
     ```

2. **Singleton Tuples (Tuples with One Element):**
   - Require a trailing comma:
     ```python
     singleton = 'hello',
     print(singleton)  # Output: ('hello',)
     ```

---

### **Tuple Packing and Unpacking**

1. **Tuple Packing:**
   - Packing multiple values into a tuple:
     ```python
     t = 12345, 54321, 'hello!'
     ```

2. **Sequence Unpacking:**
   - Extracting elements from a sequence into variables:
     ```python
     x, y, z = t
     print(x, y, z)  # Output: 12345 54321 hello!
     ```
   - Requires the number of variables on the left to match the number of elements in the sequence.

3. **Multiple Assignment:**
   - Combines packing and unpacking:
     ```python
     x, y, z = 12345, 54321, 'hello!'
     ```

---

## Sets

---

**Sets** in Python are an **unordered collection of unique elements**. They are particularly useful for:
- Membership testing.
- Removing duplicate entries.
- Performing mathematical set operations like union, intersection, difference, and symmetric difference.

---

### **Key Features**

1. **Creation:**
   - **Using curly braces:** `{}` for non-empty sets.
   - **Using `set()` function:** For empty sets or dynamic construction.
     ```python
     basket = {'apple', 'orange', 'banana'}
     empty_set = set()
     ```

2. **Properties:**
   - **Unordered:** The order of elements is not guaranteed.
   - **Unique elements:** Automatically removes duplicates.
     ```python
     basket = {'apple', 'orange', 'apple'}
     print(basket)  # Output: {'apple', 'orange'}
     ```

3. **Membership Testing:**
   - Fast testing using `in` or `not in`:
     ```python
     'orange' in basket  # True
     'grape' in basket   # False
     ```

4. **Mathematical Operations:**
   - **Union (`|`):** Combines all unique elements from both sets.
   - **Intersection (`&`):** Common elements in both sets.
   - **Difference (`-`):** Elements in the first set but not the second.
   - **Symmetric Difference (`^`):** Elements in either set but not both.

5. **Set Comprehensions:**
   - Similar to list comprehensions, but for sets.
     ```python
     a = {x for x in 'abracadabra' if x not in 'abc'}
     print(a)  # Output: {'r', 'd'}
     ```

---

### **Set Methods Table**

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

### **Examples of Mathematical Operations**

1. **Union:**
   ```python
   a = {1, 2, 3}
   b = {3, 4, 5}
   print(a | b)  # Output: {1, 2, 3, 4, 5}
   ```

2. **Intersection:**
   ```python
   print(a & b)  # Output: {3}
   ```

3. **Difference:**
   ```python
   print(a - b)  # Output: {1, 2}
   ```

4. **Symmetric Difference:**
   ```python
   print(a ^ b)  # Output: {1, 2, 4, 5}
   ```

## Dictionaries

---

**Dictionaries** in Python are **mutable, unordered collections** of key-value pairs where:
- **Keys**: Must be unique and immutable (e.g., strings, numbers, tuples with immutable elements).
- **Values**: Can be of any data type and do not need to be unique.

Dictionaries are often referred to as "associative arrays" or "hash maps" in other programming contexts.

---

### **Key Features**

1. **Creation:**
   - Using `{}`: To create an empty dictionary or initialize key-value pairs.
   - Using `dict()`: To construct a dictionary dynamically.
     ```python
     tel = {'jack': 4098, 'sape': 4139}
     empty_dict = {}
     dynamic_dict = dict(sape=4139, guido=4127, jack=4098)
     ```

2. **Basic Operations:**
   - Adding/Updating: `d[key] = value` assigns a value to a key. Overwrites if the key exists.
   - Deleting: `del d[key]` removes a key-value pair.
   - Checking Existence: `key in d` checks if a key exists.

3. **Key Constraints:**
   - Keys must be immutable (e.g., strings, numbers, tuples with immutable elements).
   - Lists and other mutable types cannot be used as keys.

4. **Accessing Data:**
   - Retrieve value by key: `d[key]`.
   - Get all keys: `list(d)`.
   - Get sorted keys: `sorted(d)`.

5. **Dictionary Comprehensions:**
   - Use expressions to create dictionaries dynamically:
     ```python
     {x: x**2 for x in (2, 4, 6)}
     # Output: {2: 4, 4: 16, 6: 36}
     ```

---

### **Table: Dictionary Methods**

| **Method**                          | **Description**                                                                 | **Return Type**       |
|-------------------------------------|---------------------------------------------------------------------------------|-----------------------|
| `clear()`                           | Removes all key-value pairs from the dictionary.                                | `None`                |
| `copy()`                            | Returns a shallow copy of the dictionary.                                      | `dict`                |
| `fromkeys(iterable, value=None)`    | Creates a new dictionary with keys from the iterable and values set to `value`. | `dict`                |
| `get(key, default=None)`            | Returns the value for `key` if it exists; otherwise, returns `default`.         | Value Type or Default |
| `items()`                           | Returns a view object of key-value pairs.                                       | `dict_items`          |
| `keys()`                            | Returns a view object of all keys.                                              | `dict_keys`           |
| `pop(key, default=None)`            | Removes the specified key and returns the corresponding value.                 | Value Type or Default |
| `popitem()`                         | Removes and returns the last inserted key-value pair as a tuple.               | `(key, value)` tuple  |
| `setdefault(key, default=None)`     | Returns the value for `key` if it exists; otherwise, inserts `key` with `default`. | Value Type           |
| `update([other])`                   | Updates the dictionary with key-value pairs from another dictionary or iterable. | `None`                |
| `values()`                          | Returns a view object of all values.                                            | `dict_values`         |

---

### **Examples**

1. **Creating and Accessing:**
   ```python
   tel = {'jack': 4098, 'sape': 4139}
   tel['guido'] = 4127  # Add key-value pair
   print(tel['jack'])   # Access value
   ```

2. **Deleting:**
   ```python
   del tel['sape']
   ```

3. **Checking Existence:**
   ```python
   'guido' in tel  # True
   'jack' not in tel  # False
   ```

4. **Using Comprehensions:**
   ```python
   squares = {x: x**2 for x in (2, 4, 6)}
   print(squares)  # {2: 4, 4: 16, 6: 36}
   ```

## Looping Techniques

Python provides versatile tools for iterating over collections, enabling clear and concise iteration patterns for different use cases.

---

### **1. Looping Through Dictionaries**
- **Retrieve keys and values simultaneously**:
  Use the `.items()` method to loop through key-value pairs of a dictionary.
  ```python
  knights = {'gallahad': 'the pure', 'robin': 'the brave'}
  for k, v in knights.items():
      print(k, v)
  ```
  **Output**:
  ```
  gallahad the pure
  robin the brave
  ```

---

### **2. Looping Through Sequences with Index**
- **Retrieve index and value**:
  Use the `enumerate()` function to get the index and corresponding value in a sequence.
  ```python
  for i, v in enumerate(['tic', 'tac', 'toe']):
      print(i, v)
  ```
  **Output**:
  ```
  0 tic
  1 tac
  2 toe
  ```

---

### **3. Looping Over Multiple Sequences Simultaneously**
- **Pair elements from two or more sequences**:
  Use the `zip()` function to combine sequences element-wise and iterate over the paired results.
  ```python
  questions = ['name', 'quest', 'favorite color']
  answers = ['lancelot', 'the holy grail', 'blue']
  for q, a in zip(questions, answers):
      print(f'What is your {q}? It is {a}.')
  ```
  **Output**:
  ```
  What is your name? It is lancelot.
  What is your quest? It is the holy grail.
  What is your favorite color? It is blue.
  ```

---

### **4. Looping in Reverse**
- **Iterate in reverse order**:
  Use the `reversed()` function to loop over a sequence from the end to the beginning.
  ```python
  for i in reversed(range(1, 10, 2)):
      print(i)
  ```
  **Output**:
  ```
  9
  7
  5
  3
  1
  ```

---

### **5. Looping in Sorted Order**
- **Iterate over a sequence in sorted order**:
  Use the `sorted()` function to loop through elements in ascending order without altering the original sequence.
  ```python
  basket = ['apple', 'orange', 'apple', 'pear', 'orange', 'banana']
  for i in sorted(basket):
      print(i)
  ```
  **Output**:
  ```
  apple
  apple
  banana
  orange
  orange
  pear
  ```

- **Loop over unique, sorted elements**:
  Combine `sorted()` with `set()` to remove duplicates and iterate in sorted order.
  ```python
  for f in sorted(set(basket)):
      print(f)
  ```
  **Output**:
  ```
  apple
  banana
  orange
  pear
  ```

---

### **6. Safely Modifying a List While Looping**
- **Avoid modifying a list during iteration**:
  Instead, create a new list for filtered or modified elements.
  ```python
  import math
  raw_data = [56.2, float('NaN'), 51.7, 55.3, 52.5, float('NaN'), 47.8]
  filtered_data = []
  for value in raw_data:
      if not math.isnan(value):
          filtered_data.append(value)
  print(filtered_data)
  ```
  **Output**:
  ```
  [56.2, 51.7, 55.3, 52.5, 47.8]
  ```

---

### **Key Techniques**

| **Technique**                     | **Function/Method Used** | **Purpose**                                               | **Example Output**                                     |
|------------------------------------|---------------------------|-----------------------------------------------------------|-------------------------------------------------------|
| Looping through dictionary items  | `.items()`                | Retrieve key-value pairs.                                 | `gallahad the pure`                                   |
| Looping with index in a sequence  | `enumerate()`             | Get index and value simultaneously.                      | `0 tic`                                              |
| Pairing multiple sequences         | `zip()`                   | Iterate over two or more sequences in parallel.          | `What is your name? It is lancelot.`                 |
| Reversing a sequence               | `reversed()`              | Loop over a sequence in reverse order.                   | `9, 7, 5, 3, 1`                                      |
| Sorting elements                   | `sorted()`                | Iterate in sorted order without altering the original.   | `apple, apple, banana, orange, orange, pear`         |
| Removing duplicates and sorting    | `set()` + `sorted()`      | Loop over unique elements in sorted order.               | `apple, banana, orange, pear`                        |
| Filtering a list                   | Manual filtering          | Safely create a new list by filtering elements.           | `[56.2, 51.7, 55.3, 52.5, 47.8]`                    |

## More on Conditions

In Python, conditions used in `while` and `if` statements can involve various operators beyond just comparisons.

---

### **1. Membership Operators: `in` and `not in`**
- The `in` and `not in` operators are used to test whether a value exists (or does not exist) in a container (like a list, string, or set). 

---

### **2. Identity Operators: `is` and `is not`**
- The `is` and `is not` operators are used to check if two variables refer to the same object in memory, not just if their values are equal.

---

### **3. Chained Comparisons**
- Comparisons can be chained together. For example:
  ```python
  a < b == c
  ```
  This checks if `a` is less than `b` **and** `b` equals `c`.

---

### **4. Combining Comparisons with Boolean Operators: `and`, `or`, and `not`**
- **Logical Operators**: 
  - `and`, `or`, and `not` combine comparisons.
  - `and` requires all conditions to be true.
  - `or` requires at least one condition to be true.
  - `not` negates a Boolean value.
  - **Operator Precedence**: 
    - `not` has higher precedence than `and`, which has higher precedence than `or`.
    - Parentheses can be used to control the evaluation order.
  - **Short-Circuiting**: 
    - The evaluation stops as soon as the result is determined (left to right).
    - For example, in `A and B and C`, if `B` is false, `C` isn't evaluated because the result is already false.
  - **Return Value**: The last evaluated argument is returned by `and` and `or` when they are used as general values (not just Booleans).
  
---

### **5. Assigning Results of Comparisons**
- You can assign the result of a Boolean expression to a variable.
  ```python
  string1, string2, string3 = '', 'Trondheim', 'Hammer Dance'
  non_null = string1 or string2 or string3
  print(non_null)  # 'Trondheim'
  ```
  - The expression returns the first non-empty value from the sequence.
  
---

### **6. The Walrus Operator (`:=`)**
- In Python, assignment inside expressions must use the **walrus operator (`:=`)**. This helps avoid mistakes like using `=` (assignment) when `==` (comparison) was intended.

---

## Comparing Sequences and Other Types

Python allows comparing sequences (like lists, tuples, and strings) with each other. The comparison follows **lexicographical order**.

---

### **1. Lexicographical Ordering**
- Sequences are compared item by item. The first pair of unequal items determines the comparison outcome. If items are equal, the next items are compared, and so on.
- If one sequence is a prefix of the other (e.g., `[1, 2]` vs `[1, 2, 3]`), the shorter sequence is considered smaller.

Examples of comparisons:
- `(1, 2, 3) < (1, 2, 4)` (True)
- `('ABC' < 'C' < 'Pascal' < 'Python')` (True)
- `(1, 2, 3) == (1.0, 2.0, 3.0)` (True)

---

### **2. Comparing Sequences with Different Types**
- Sequences of different types can be compared if they have appropriate comparison methods (e.g., numbers). For example, `0 == 0.0`.
- If comparisons between unrelated types are attempted, Python raises a `TypeError`.

--- 


# Modules


### What are Modules?
- A **module** is a file containing Python definitions (functions, variables, etc.) and statements.
- The file name of the module ends with `.py`. For example, a file named `fibo.py` is a module.
- Modules enable:
  - **Code reuse**: Functions or variables in a module can be used across multiple scripts or programs.
  - **Organization**: Large programs can be split into smaller, manageable files.
  - **Improved maintenance**: Changes in a single module reflect across all scripts importing it.

---

### Benefits of Using Modules
- Avoids losing definitions (functions, variables) when exiting the Python interpreter.
- Facilitates the reuse of code without duplicating definitions in multiple programs.

---

### Importing Modules
- To use a module in Python, it needs to be **imported** using the `import` statement:
  ```python
  import module_name
  ```
- When a module is imported:
  - The module name is added to the current namespace.
  - The functions and variables within the module are accessed using the **dot notation**:
    ```python
    module_name.function_name(arguments)
    ```
- Example:
  ```python
  import fibo
  fibo.fib(1000)  # Calls the `fib` function from the `fibo` module
  ```

---

### Creating a Module
- A module is created by saving a Python script (`.py` file) with the desired functions and variables.
- Example module (`fibo.py`):
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

---

### Accessing Module Functions
- After importing a module, its functions and variables can be accessed:
  ```python
  >>> import fibo
  >>> fibo.fib(100)   # Prints Fibonacci numbers up to 100
  0 1 1 2 3 5 8 13 21 34 55 89
  >>> fibo.fib2(50)   # Returns a list of Fibonacci numbers up to 50
  [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
  ```
- The module name can be checked using the `__name__` attribute:
  ```python
  >>> fibo.__name__
  'fibo'
  ```

---

### Assigning Module Functions to Local Names
- A function from a module can be assigned to a local variable to simplify access:
  ```python
  >>> fib = fibo.fib
  >>> fib(200)  # Calls the `fib` function without using `fibo.`
  0 1 1 2 3 5 8 13 21 34 55 89 144
  ```

---


### **What a Module Contains**
A Python module can include:
- **Executable Statements**: These run when the module is first imported or executed as a standalone script. These statements help initialize the module.
- **Function and Variable Definitions**: These are reusable components that other scripts can import and use.

Each module has its **own private namespace**, meaning the global variables within a module are not accessible directly by other scripts unless explicitly referenced.

---

### **Importing Modules**

When a module is imported for the first time:
- Python executes its initialization statements.
- The module’s namespace becomes available.

Subsequent imports of the same module within the same session do not reinitialize it. For example:
```python
import fibo
fibo.fib(500)  # Calls the 'fib' function defined in the module
```

---

### **Importing Specific Components**
To reduce namespace clutter, specific items can be imported from a module:
```python
from fibo import fib, fib2
fib(500)  # Directly calls the 'fib' function
```
Here, only `fib` and `fib2` are imported, and the module name `fibo` is not added to the local namespace.

---

### **Importing All Names**
Using `from module import *` imports all items from a module except those starting with an underscore (`_`):
```python
from fibo import *
fib(500)
```
**Drawback**: This practice can lead to namespace conflicts and less readable code. For example, it may unintentionally overwrite existing variables or functions.

---

### **Using Aliases for Modules and Components**
Modules and their components can be given alternative names using the `as` keyword. This is useful for simplifying long or frequently used names:
```python
import fibo as fib
fib.fib(500)  # Calls 'fib' from the module 'fibo'

from fibo import fib as fibonacci
fibonacci(500)  # Calls 'fib' with the alias 'fibonacci'
```

---

### **Efficiency of Importing**
A module is imported only **once per interpreter session** for efficiency. If the module code changes during the session, the interpreter must be restarted or the module reloaded interactively:
```python
import importlib
importlib.reload(fibo)
```

---

### **Best Practices**
- Use explicit imports (`from module import name`) to maintain clarity in your code.
- Avoid `from module import *` in production code to prevent namespace conflicts.
- Use aliases for long or frequently referenced module names to improve code readability.


---

### **Executing Modules as Scripts**
Python modules can act as both reusable components and standalone scripts. When executed as a script, the `__name__` variable of the module is set to `"__main__"`. This allows developers to add code specifically designed to run only when the module is executed directly, not when imported.

**Example 1: Basic Module Execution**
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
```

- Running `python fibo.py 50`:
  ```
  0 1 1 2 3 5 8 13 21 34
  ```
  The `fib` function executes using the command-line argument `50`.

- Importing `fibo` in another script:
  ```python
  import fibo
  fibo.fib(30)
  ```
  The `if __name__ == "__main__":` block is **not executed**. Only the `fib` function is available.

---

**Example 2: Testing Code**
Modules often include test cases or examples under the `__main__` block. For instance:
```python
if __name__ == "__main__":
    print("Testing fib(10):")
    fib(10)
```
Output:
```
Testing fib(10):
0 1 1 2 3 5 8
```
This makes it easy to validate functionality without affecting the module's behavior when imported.

---

### **The Module Search Path**

When importing a module, Python follows a specific search path to locate it. The interpreter searches:
1. **Built-in Modules**: These are checked first. Names like `os` or `sys` are built-in.
   ```python
   import sys
   print(sys.builtin_module_names)
   ```
   Output:
   ```
   ('_ast', '_io', '_thread', ..., 'sys', ...)
   ```

2. **Current Directory**: If the module is not built-in, Python looks in the directory of the script being executed (or the current working directory in interactive sessions).

**Example: Local Module Precedence**
Suppose the directory contains `math.py` with the following:
```python
def my_func():
    print("This is a custom math module!")
```
Running:
```python
import math
math.my_func()
```
The local `math.py` will be imported instead of Python's standard library `math`.

---

3. **Environment Variable `PYTHONPATH`**: You can define additional directories to include in the search path using `PYTHONPATH`.
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

4. **Installation-Dependent Defaults**: These include standard library paths and the `site-packages` directory for third-party modules.

---

### **Modifying the Module Search Path**
The search path is stored in `sys.path`, a list of directories. You can inspect and modify it:
```python
import sys
print(sys.path)
```
Adding a directory:
```python
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
```
Output:
```
Hello from extra!
```

---

### **Important Considerations**

1. **Symlink Behavior**: On systems supporting symlinks, the directory of the resolved target is used for the search path, not the directory containing the symlink.

2. **Precedence**: The current directory takes precedence over standard libraries. Be cautious when naming local scripts, as they may shadow standard modules.

**Example: Shadowing Issue**
A local file named `random.py` could interfere with importing the standard library module:
```python
import random
```
Instead of Python's `random`, the local file will be used, possibly leading to errors.

---

### “Compiled” Python Files

Python employs a caching mechanism to speed up module loading by storing compiled versions of Python files (`.py`) in a special directory named `__pycache__`. These compiled files are identified by the `.pyc` extension and include metadata, such as the Python version used to compile them, ensuring compatibility across different versions and platforms.

---

#### **How Compiled Python Files Work**

1. **Compilation and Caching**:
   - When a module is imported, Python compiles the `.py` file into bytecode and saves it as a `.pyc` file in the `__pycache__` directory.
   - The compiled file is named using the format:  
     `module.version.pyc`  
     Example:
     - `spam.py` in Python 3.11 would be compiled and saved as:
       ```
       __pycache__/spam.cpython-311.pyc
       ```

2. **Automatic Recompilation**:
   - Python automatically checks the modification date of the `.py` file against its cached `.pyc` counterpart.
   - If the source file has been updated, Python recompiles it, replacing the cached version.

3. **Platform Independence**:
   - Compiled files are architecture-independent, allowing them to be used across different systems as long as the Python versions match.

---

#### **Scenarios Where Python Does Not Use the Cache**

1. **Direct Execution**:
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

2. **Missing Source File**:
   - If the `.py` file is not present and only the `.pyc` file exists, Python does not check the cache.

   **Example: Distribution Without Source**:
   - For deploying without source files:
     - Place the `.pyc` file in the same directory as the module.
     - Ensure the `.py` file is removed to prevent recompilation.

---

#### **Optimizations with `.pyc` Files**

1. **Using `-O` and `-OO` Flags**:
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

---

#### **Performance Insights**

- **Loading Speed**:
  - Using `.pyc` files improves load time but does not enhance runtime performance.
  - Programs read from `.py` files and `.pyc` files execute at the same speed because the execution is bytecode-based in both cases.

---

#### **Advanced Tools and Techniques**

1. **Creating `.pyc` Files Manually**:
   - Use the `compileall` module to precompile all modules in a directory.

   **Example**:
   ```bash
   python -m compileall /path/to/modules
   ```
   - This generates `.pyc` files for all `.py` files in the specified directory.

2. **Exploring Details in PEP 3147**:
   - Python's `.pyc` file caching mechanism is detailed in [PEP 3147](https://peps.python.org/pep-3147/), which includes a flowchart of how Python decides to recompile or use cached files.

---

#### **Practical Example: Using `__pycache__`**

1. **Create a module**:
   ```python
   # demo.py
   def greet():
       print("Hello, world!")
   ```

2. **Import it in a script**:
   ```python
   import demo
   demo.greet()
   ```
   Output:
   ```
   Hello, world!
   ```

3. **Inspect the cache**:
   - After importing, the directory structure will look like this:
     ```
     demo.py
     __pycache__/
         demo.cpython-311.pyc
     ```

4. **Recompile after modification**:
   - Update `demo.py`:
     ```python
     def greet():
         print("Hello, Python!")
     ```

   - On the next import, Python automatically recompiles `demo.cpython-311.pyc`.

---

### **In-depth Summary: Standard Modules**

Python's standard library is an extensive collection of modules that come bundled with the Python interpreter. These modules provide a wide range of functionality, from system-level access to high-level utilities, making Python a versatile language for diverse use cases. Below is an exploration of key aspects of standard modules using examples.

---

### **Built-in Standard Modules**

1. **Definition and Scope**:
   - Some modules are built into the Python interpreter for efficiency or to provide low-level access to operating system features.
   - The availability of certain modules depends on the platform.  
     Example:
     - The `winreg` module is exclusive to Windows.

2. **Key Built-in Module: `sys`**:
   - The `sys` module provides access to system-specific parameters and functions.

   **Example 1: Prompt Customization**:
   - The `sys.ps1` and `sys.ps2` variables define the primary (`>>>`) and secondary (`...`) prompts in interactive mode.
     ```python
     import sys
     print(sys.ps1)  # Output: '>>>'
     print(sys.ps2)  # Output: '...'

     # Customizing the prompt
     sys.ps1 = 'C> '
     print(sys.ps1)  # Output: 'C> '
     ```

     Interaction after setting `sys.ps1`:
     ```
     C> print('Hello, World!')
     Hello, World!
     C>
     ```

   **Example 2: Managing the Module Search Path**:
   - The `sys.path` variable is a list of strings indicating the directories searched for modules.
   - It can be modified to include custom paths dynamically.
     ```python
     import sys
     print(sys.path)  # Displays the default search paths
     sys.path.append('/custom/path/to/modules')
     ```

---

### **The `dir()` Function**

The `dir()` function is a powerful tool for introspection, allowing users to list the names defined within a module, variable, or current namespace.

1. **Usage with Modules**:
   - Lists all names (functions, variables, etc.) defined in a module.
     ```python
     import fibo, sys
     print(dir(fibo))  # Output: ['__name__', 'fib', 'fib2']
     print(dir(sys))   # Outputs names defined in the `sys` module
     ```

2. **Usage Without Arguments**:
   - Displays names defined in the current namespace.
     ```python
     a = [1, 2, 3, 4, 5]
     import fibo
     fib = fibo.fib

     print(dir())  
     # Output: ['__builtins__', '__name__', 'a', 'fib', 'fibo', 'sys']
     ```

3. **Discovering Built-in Functions**:
   - The `dir()` function does not display built-in functions or variables by default.
   - Use the `builtins` module to access this list:
     ```python
     import builtins
     print(dir(builtins))
     # Output includes names like 'abs', 'all', 'any', 'bin', 'bool', etc.
     ```

---

### **Customization and Practical Scenarios**

1. **Interactive Debugging**:
   - Use `sys.ps1` and `sys.ps2` to create custom prompts in interactive Python sessions, aiding in debugging and testing.

2. **Custom Module Paths**:
   - Dynamically add paths to `sys.path` to organize large projects or load modules from non-standard locations.
     ```python
     import sys
     sys.path.append('/my_project/lib')
     ```

3. **Exploring Modules**:
   - Use `dir()` to explore the contents of unfamiliar modules interactively.
     ```python
     import random
     print(dir(random))  
     # Explore the functions like 'choice', 'randint', 'shuffle', etc.
     ```

4. **Checking Current Namespace**:
   - View all currently defined names, useful for managing the workspace in interactive sessions.
     ```python
     x = 42
     print(dir())  
     # Output: ['__builtins__', '__name__', 'x']
     ```

---

## Python Packages

Python packages provide a way to organize and structure code into logical modules using "dotted module names." This organization helps developers manage larger projects, avoid name conflicts, and reuse code effectively. Here's an exhaustive explanation with practical examples.

---

### **What Are Packages?**

- **Definition**: A package is a collection of modules organized in directories that use a special `__init__.py` file to indicate they are Python packages.
- **Dotted Names**: Packages allow hierarchical access to modules via dotted module names, e.g., `package.submodule`.

**Example**:  
In the package `A`, a submodule `B` can be accessed as `A.B`. This system is especially useful for large projects like `NumPy` or `Pillow`, where it prevents naming collisions across modules.

---

### **Example: Sound Package**

Let’s consider a package for handling sound files and operations. Sound files come in various formats (`.wav`, `.aiff`, `.au`), and you might need functionalities like conversion, equalizing, or applying effects.

**File Structure**:  
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

---

### **How Packages Work**

1. **The `__init__.py` File**:
   - Every package directory must contain an `__init__.py` file.
   - **Purpose**:
     - Signals Python that the directory is a package.
     - Prevents accidental shadowing of modules with common directory names (e.g., `string`).

   - **Examples**:
     - Empty file:
       ```plaintext
       __init__.py
       ```
       This marks the directory as a package.
     - Initialization code:
       ```python
       # sound/__init__.py
       print("Initializing the sound package")
       ```
     - Setting `__all__`:
       ```python
       # sound/effects/__init__.py
       __all__ = ["echo", "surround"]
       ```

2. **Importing Modules**:
   - To use submodules, import them explicitly:
     ```python
     import sound.effects.echo
     sound.effects.echo.echofilter(input, output, delay=0.7, atten=4)
     ```
   - Use `from` for convenience:
     ```python
     from sound.effects import echo
     echo.echofilter(input, output, delay=0.7, atten=4)
     ```
   - Import specific functions or classes directly:
     ```python
     from sound.effects.echo import echofilter
     echofilter(input, output, delay=0.7, atten=4)
     ```

---

### **Key Concepts**

#### **1. Using `from package import item`**

- `item` can be:
  - A submodule (e.g., `echo`).
  - A function, class, or variable defined in the package.

**Example**:  
```python
# sound/effects/__init__.py
def initialize_effects():
    print("Effects initialized")
```

```python
from sound.effects import initialize_effects
initialize_effects()
```

- Python first looks for `initialize_effects` in the package. If not found, it checks for a module with that name.

---

#### **2. Using `import item.subitem.subsubitem`**

- Each `item` except the last must be a package.
- The last can be:
  - A package.
  - A module.

**Invalid Example**:  
```python
import sound.effects.echo.some_function  # Error: `some_function` is not a module or package
```

---

### **Advantages of Using Packages**

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

---

### **Examples in Action**

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

---

### **Import Best Practices**

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

---

### **Summary**

- **Packages**:
  - Organize modules into logical namespaces.
  - Enable modular development for large projects.

- **Dotted Module Names**:
  - Allow hierarchical organization and access.

- **`__init__.py`**:
  - Defines package behavior.
  - Can contain initialization code or the `__all__` variable.

- **Importing**:
  - Use specific imports for clarity.
  - Avoid wildcard imports in production.

By using packages, Python enables developers to manage complexity and create clean, reusable, and scalable codebases.

### **In-Depth Summary: Importing `*` From a Package**

The `from package import *` statement allows importing multiple submodules or names from a package into the current namespace. However, its behavior is nuanced, with potential caveats, limitations, and best practices. Here's a comprehensive breakdown with examples.

---

### **How Does `from package import *` Work?**

1. **Default Behavior**:
   - By default, `from package import *` does **not** automatically import all submodules from the package.
   - Instead, it:
     - Imports the package itself.
     - Executes any initialization code in the package’s `__init__.py`.
     - Imports all names explicitly defined in the package’s `__init__.py`.

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

### **Why Avoid Automatically Importing All Submodules?**

1. **Performance Concerns**:
   - Automatically searching the filesystem for submodules and importing them can be time-consuming.
   - This approach might also trigger unwanted side effects from the initialization code of submodules.

2. **Control and Intent**:
   - Importing all submodules might lead to namespace pollution and unintended behavior.
   - Explicit imports are preferable because they make the code more readable and predictable.

---

### **Examples of Importing `*`**

#### **Example 1: Using `__all__`**

**Structure**:  
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

---

#### **Example 2: Shadowing Submodules**

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

#### **Example 3: Without `__all__`**

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

### **Best Practices**

1. **Avoid `import *` in Production**:
   - It’s considered bad practice due to potential namespace conflicts and reduced code readability.
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

---

### **Key Takeaways**

- **Control With `__all__`**:
  - Define `__all__` in `__init__.py` to specify the submodules or names imported via `import *`.
  - Example:
    ```python
    __all__ = ["module1", "module2"]
    ```

- **Shadowing Issues**:
  - Local names in `__init__.py` can shadow submodules, causing unexpected behavior.

- **Explicit Imports Are Safer**:
  - Always prefer explicit imports for clarity and maintainability.

**Recommended**:
```python
from sound.effects import echo
```

**Avoid in Production**:
```python
from sound.effects import *
```

By adhering to these principles, you can write cleaner, more maintainable Python code and avoid pitfalls associated with `import *`.


### Intra-package References

When working with Python packages, you may often need to reference submodules within the same package or sibling subpackages. Python offers two main types of imports for this purpose: **absolute imports** and **relative imports**.

---

#### **Absolute Imports**:
- Absolute imports refer to modules or submodules by their full path, starting from the root package.
- For example, in the package `sound`, if the module `sound.filters.vocoder` needs to use the `echo` module from `sound.effects`, it can use an absolute import like this:
  ```python
  from sound.effects import echo
  ```
  - **Explanation**: This line imports the `echo` submodule from the `effects` subpackage, starting from the root `sound` package.

---

#### **Relative Imports**:
- Relative imports allow you to refer to other modules or submodules within the same package or its parent packages. These are useful when you're working within a nested package structure, as they allow for more concise and flexible imports.
- Relative imports use **leading dots** to refer to the current and parent packages. The number of dots indicates the level of the package structure to move up:
  - A single dot (`.`) refers to the **current package**.
  - Two dots (`..`) refer to the **parent package**.
  - Three dots (`...`) would refer to the **grandparent package**, and so on.

##### **Examples**:

1. **Import from the Current Package**:
   - If you're in the `surround` module within `sound.effects` and want to import the `echo` module from the same `effects` package, you can use:
     ```python
     from . import echo
     ```
     - The single dot (`.`) indicates that `echo` is a sibling submodule in the same package (`sound.effects`).

2. **Import from the Parent Package**:
   - If you're in the `surround` module and want to access something from the `formats` subpackage (which is at the same level as `effects`), you would use:
     ```python
     from .. import formats
     ```
     - The two dots (`..`) indicate that `formats` is a sibling subpackage to `effects` and `surround`, but one level up in the package hierarchy.

3. **Import from a Sibling Subpackage's Submodule**:
   - To access `equalizer` from the `filters` subpackage, you can write:
     ```python
     from ..filters import equalizer
     ```
     - The two dots (`..`) indicate moving one level up to `sound` and then into the `filters` subpackage to import `equalizer`.

---

#### **Important Note on Relative Imports**:
- **Relative imports are based on the module's name** in the package structure. This means that they are typically used within modules that are part of a larger package or subpackage. 
- **Special Case for the Main Module**:
  - The main module, usually identified as `"__main__"`, cannot use relative imports because it's not part of any package. When running a script directly (e.g., `python myscript.py`), Python considers it the top-level module, and relative imports would not work.
  - In such cases, only **absolute imports** should be used to ensure proper module resolution.

**Example**:
- Suppose you have the following package structure:
  ```plaintext
  sound/
    __init__.py
    effects/
      __init__.py
      echo.py
      surround.py
    filters/
      __init__.py
      equalizer.py
  ```
  - In `echo.py`, if you want to use the `surround` module within the same `effects` package, you can write:
    ```python
    from . import surround
    ```
  - In `surround.py`, if you want to use the `equalizer` module from the `filters` subpackage, you would write:
    ```python
    from ..filters import equalizer
    ```

---

### Multiple Directories

In some cases, a package may be distributed across **multiple directories**. Python supports this scenario using the special `__path__` attribute.

1. **The `__path__` Attribute**:
   - The `__path__` attribute is a list initialized with the directory containing the package's `__init__.py` file.
   - This attribute is important because it defines where Python looks for submodules and subpackages when importing a package.
   - It can be modified to include additional directories, allowing you to extend the search path for modules within a package.

2. **Extending the Package Search Path**:
   - By modifying `__path__`, you can make Python search for modules in multiple locations.
   - For example, if a package is split across two directories, you can modify `__path__` to include both directories. This is useful for large projects where the package’s components may reside in different locations but still need to be considered part of the same logical package.

**Example**:
```python
# sound/__init__.py
__path__.append('/path/to/other/directory')
```
- This adds `/path/to/other/directory` to the package search path for the `sound` package, allowing Python to find and import submodules from that directory.

---

### **Key Takeaways**:

1. **Absolute Imports**:
   - Always refer to modules and submodules from the root package, using the full path.
   - Useful when referencing sibling or other submodules from a different part of the package hierarchy.

2. **Relative Imports**:
   - Use leading dots to refer to modules within the same package or parent packages.
   - Flexible and concise, but **not suitable for the main module** (`__main__`).

3. **Managing Packages Across Multiple Directories**:
   - Python allows you to extend the package search path using the `__path__` attribute.
   - This is useful for large packages distributed across multiple directories, though it’s not commonly needed.

4. **Relative vs Absolute Imports**:
   - Relative imports are best used within packages, while absolute imports should be used in the main module (`__main__`).

By understanding and applying absolute and relative imports effectively, you can structure your Python code more cleanly and maintainably, particularly in larger projects with complex package hierarchies.


# Input and Output

## Fancier Output Formatting

### Formatted String Literals (f-strings):
- Introduced with `f` or `F` before the string's opening quotes, f-strings allow embedding Python expressions directly within curly braces `{}`. 
- These expressions can refer to variables or literal values.

**Example**:
```python
year = 2016
event = 'Referendum'
f'Results of the {year} {event}'
# Output: 'Results of the 2016 Referendum'
```
- **Use Case**: Concise and readable syntax for including variables and expressions in strings.

---

### The `str.format()` Method:
- This method uses `{}` as placeholders and requires the explicit provision of values to be formatted. You can also include detailed formatting instructions.

**Example**:
```python
yes_votes = 42_572_654
total_votes = 85_705_149
percentage = yes_votes / total_votes
'{:-9} YES votes {:2.2%}'.format(yes_votes, percentage)
# Output: ' 42572654 YES votes 49.67%'
```
- **Details**:
  - `-9`: Pads `yes_votes` with spaces, handling negative numbers properly.
  - `2.2%`: Displays the percentage with 2 decimal places and a `%` sign.

---

### Manual String Handling:
- By combining string slicing and concatenation, you can construct custom layouts without relying on built-in formatting tools.

**Example**:
```python
x = 10 * 3.25
y = 200 * 200
s = 'The value of x is ' + repr(x) + ', and y is ' + repr(y) + '...'
print(s)
# Output: 'The value of x is 32.5, and y is 40000...'
```

---

### `str()` vs. `repr()` Functions:
- These functions convert objects to strings but are intended for different purposes:
  - **`str()`**: Produces human-readable representations.
  - **`repr()`**: Produces interpreter-readable representations, often suitable for debugging or recreating the object.

**Examples**:
```python
s = 'Hello, world.'
str(s)  # Output: 'Hello, world.'
repr(s) # Output: "'Hello, world.'"

# `repr()` adds string quotes and backslashes for clarity:
hello = 'hello, world\n'
repr(hello)  # Output: "'hello, world\\n'"
```

---

### Using the `Template` Class from the `string` Module**:
- Templates offer basic string substitution using placeholders like `$x`. Substitutions are made from a dictionary.

**Example**:
```python
from string import Template
t = Template('Total: $total, Discount: $discount')
t.substitute(total=100, discount=10)
# Output: 'Total: 100, Discount: 10'
```
- **Limitations**: Provides less control over formatting compared to f-strings or `str.format()`.

---

### **Additional Notes**:
1. **Percentage Formatting**:
   - Format values as percentages with precision using `{:n.m%}` where `n` is width and `m` is precision.
2. **For Quick Debugging**:
   - Use `repr()` or `str()` to quickly convert variables to strings.
   - Objects like tuples or lists maintain their structure in `repr()`.

---

### Formatted String Literals (f-strings)

Formatted string literals, or **f-strings**, are a powerful Python feature that enables embedding expressions within strings by prefixing the string with `f` or `F`. These expressions, enclosed in curly braces `{}`, are evaluated at runtime and inserted directly into the string. This method is concise, efficient, and offers advanced formatting capabilities.

---

#### **1. Embedding Expressions in Strings**
- Any Python expression can be placed inside `{}` within an f-string.
- The expression is evaluated, and its result is included in the string.

**Example**:
```python
name = "Alice"
age = 30
f"My name is {name} and I am {age} years old."
# Output: 'My name is Alice and I am 30 years old.'
```

---

#### **2. Using Format Specifiers**
- **Format specifiers** control the presentation of values, such as the number of decimal places, width, or type of alignment.
- To use a format specifier, include a colon (`:`) after the expression, followed by the desired specification.

**Example**: Rounding values
```python
import math
f"The value of pi is approximately {math.pi:.3f}."
# Output: 'The value of pi is approximately 3.142.'
```

- **Example**: Aligning columns with minimum width
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

#### **3. Value Conversion Modifiers**
F-strings allow modifying values before formatting:
- **`!a`**: Applies `ascii()` (produces ASCII-safe representations).
- **`!s`**: Applies `str()` (converts to a string).
- **`!r`**: Applies `repr()` (produces interpreter-readable representation).

**Examples**:
```python
animals = 'eels'
f"My hovercraft is full of {animals}."
# Output: 'My hovercraft is full of eels.'

f"My hovercraft is full of {animals!r}."
# Output: "My hovercraft is full of 'eels'."
```

---

#### **4. Self-Documenting Expressions with `=`**
- The `=` specifier automatically expands expressions to include the expression itself, followed by its evaluated result. This is useful for debugging or self-documenting code.

**Example**:
```python
bugs = 'roaches'
count = 13
area = 'living room'
f"Debugging {bugs=} {count=} {area=}"
# Output: "Debugging bugs='roaches' count=13 area='living room'"
```

---

#### **5. Advanced Format Specifiers**
- F-strings use the same format specifications as the `str.format()` method. For a full reference, consult the `formatspec` documentation.

**Examples**:
- Fixed-point formatting:
  ```python
  value = 123.45678
  f"{value:.2f}"  # Output: '123.46'
  ```
- Zero-padding:
  ```python
  number = 42
  f"{number:05d}"  # Output: '00042'
  ```
- Hexadecimal or binary:
  ```python
  num = 255
  f"{num:#x}"  # Output: '0xff'
  f"{num:#b}"  # Output: '0b11111111'
  ```

---

#### **Advantages of F-strings**
1. **Concise and Readable**:
   - Embed variables and expressions directly into strings without additional function calls.
2. **Powerful Formatting**:
   - Provides granular control over presentation using format specifiers.
3. **Debugging Aid**:
   - The `=` specifier helps self-document code and debug variable values easily.
4. **Performance**:
   - Faster than alternatives like `str.format()` or string concatenation due to direct evaluation.

---

#### **Comparison with Other Methods**
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

---

#### **1. Basic Usage**

The placeholders `{}` in a string are replaced by the arguments passed to the `format()` method.

**Example:**
```python
print('We are the {} who say "{}!"'.format('knights', 'Ni'))
# Output: We are the knights who say "Ni!"
```

---

#### **2. Positional Arguments**

You can specify the order of substitution using numbers inside the curly braces.

**Examples:**
- Default order:
  ```python
  print('{0} and {1}'.format('spam', 'eggs'))
  # Output: spam and eggs
  ```
- Reversed order:
  ```python
  print('{1} and {0}'.format('spam', 'eggs'))
  # Output: eggs and spam
  ```

---

#### **3. Keyword Arguments**

Keyword arguments are referenced by their names within the placeholders.

**Example:**
```python
print('This {food} is {adjective}.'.format(food='spam', adjective='absolutely horrible'))
# Output: This spam is absolutely horrible.
```

---

#### **4. Mixing Positional and Keyword Arguments**

You can combine positional and keyword arguments arbitrarily.

**Example:**
```python
print('The story of {0}, {1}, and {other}.'.format('Bill', 'Manfred', other='Georg'))
# Output: The story of Bill, Manfred, and Georg.
```

---

#### **5. Accessing Values in Dictionaries**

You can use dictionary keys as references within the placeholders:
- **Using direct dictionary access:**
  ```python
  table = {'Sjoerd': 4127, 'Jack': 4098, 'Dcab': 8637678}
  print('Jack: {0[Jack]:d}; Sjoerd: {0[Sjoerd]:d}; Dcab: {0[Dcab]:d}'.format(table))
  # Output: Jack: 4098; Sjoerd: 4127; Dcab: 8637678
  ```

- **Using `**` to unpack the dictionary:**
  ```python
  print('Jack: {Jack:d}; Sjoerd: {Sjoerd:d}; Dcab: {Dcab:d}'.format(**table))
  # Output: Jack: 4098; Sjoerd: 4127; Dcab: 8637678
  ```

---

#### **6. Formatting with Width and Alignment**

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

---

#### **7. Using `vars()` for Local Variables**

The `vars()` function returns a dictionary of all local variables, which can be used with `**` to dynamically format strings.

**Example:**
```python
x = 42
y = 'example'
table = vars()
print('x: {x}, y: {y}'.format(**table))
# Output: x: 42, y: example
```

---

##E# **Advantages of `str.format()`**
1. **Flexibility**: Combine positional and keyword arguments.
2. **Readability**: Reference variables by name or position for clarity.
3. **Customizability**: Control width, alignment, and type-specific formatting (e.g., integers, floats).
4. **Dictionary Access**: Format strings using values from dictionaries, including dynamically generated ones.

---

#### **Comparison with f-strings**

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

Manual string formatting involves directly manipulating strings using methods like `rjust()`, `ljust()`, `center()`, and `zfill()` for precise control over layout and alignment. This approach does not involve placeholders like `str.format()` or f-strings but instead relies on string methods to create properly formatted output.

---

#### **1. Right-Justifying with `str.rjust()`**

The `rjust()` method aligns text to the right within a specified width by padding it with spaces on the left. 

**Example: Table of Squares and Cubes**
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

---

#### **2. Left-Justifying with `str.ljust()`**

The `ljust()` method aligns text to the left within a specified width by padding it with spaces on the right.

**Example:**
```python
print('Hello'.ljust(10) + 'World')
# Output: Hello     World
```

---

#### **3. Centering with `str.center()`**

The `center()` method centers text within a specified width, padding both sides with spaces.

**Example:**
```python
print('Python'.center(10))
# Output:   Python  
```

---

#### **4. Zero-Padding with `str.zfill()`**

The `zfill()` method pads a string on the left with zeros, and it recognizes signs (`+` or `-`) for numeric strings.

**Examples:**
```python
print('12'.zfill(5))          # Output: 00012
print('-3.14'.zfill(7))       # Output: -003.14
print('3.14159265359'.zfill(5))  # Output: 3.14159265359 (unchanged because it's longer than 5)
```

---

#### **5. Truncating Strings**

If you need a fixed width and truncation, you can use slicing in combination with `ljust()` or `rjust()`.

**Example:**
```python
print('Hello, world!'.ljust(10)[:10])
# Output: Hello, wo
```

---

#### **6. Spaces Between Arguments in `print()`**

The `print()` function automatically adds a space between arguments. To avoid extra spaces, use string concatenation or formatting.

**Example:**
```python
print('Hello', 'World')  # Output: Hello World
print('Hello' + 'World')  # Output: HelloWorld
```

---

#### **Advantages of Manual Formatting**
1. **Control**: Offers precise control over padding, alignment, and layout.
2. **Simplicity**: Useful for straightforward tasks without requiring placeholders.

---

### Old String Formatting with the `%` Operator

Old-style string formatting in Python uses the `%` operator, also known as the modulo operator, to substitute values into a format string. This approach was prevalent before `str.format()` and f-strings were introduced. The `%` operator offers several format specifiers to control how values are inserted into a string.

---

#### **Basic Syntax**

```python
format % values
```
- **`format`**: A string containing placeholders.
- **`values`**: A single value or a tuple of values to replace the placeholders.

---

#### **1. Placeholders and Specifiers**

Placeholders are introduced with `%` followed by format specifiers that define how the value will be formatted.

##### **Common Format Specifiers**
| Specifier | Meaning                         | Example Input | Example Output      |
|-----------|---------------------------------|---------------|---------------------|
| `%s`      | String                          | `'Python'`    | `Python`            |
| `%d`      | Integer                         | `42`          | `42`                |
| `%f`      | Floating-point number           | `3.14159`     | `3.141590`          |
| `%x`      | Hexadecimal (lowercase)         | `255`         | `ff`                |
| `%X`      | Hexadecimal (uppercase)         | `255`         | `FF`                |
| `%e`      | Scientific notation (lowercase) | `12345.67`    | `1.234567e+04`      |
| `%E`      | Scientific notation (uppercase) | `12345.67`    | `1.234567E+04`      |
| `%c`      | Single character                | `65`          | `A` (ASCII 65)      |

---

#### **2. Examples of Basic Usage**

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

---

#### **3. Formatting with Width and Precision**

The `%` operator allows specifying the width (minimum number of characters) and precision for numeric values.

**Syntax:**
```
%[flags][width][.precision]specifier
```

##### **Examples**
- **Width and Right-Justification**:
  ```python
  print('Value: %5d' % 42)
  # Output: Value:    42
  ```

- **Width with Zero-Padding**:
  ```python
  print('Value: %05d' % 42)
  # Output: Value: 00042
  ```

- **Floating-Point Precision**:
  ```python
  print('Value: %.3f' % 3.14159)
  # Output: Value: 3.142
  ```

- **Combining Width and Precision**:
  ```python
  print('Value: %8.2f' % 3.14159)
  # Output: Value:     3.14
  ```

---

#### **4. Using `%s` for Strings**

The `%s` specifier converts any value into a string.

**Examples**:
```python
print('Name: %s' % 'Bob')
# Output: Name: Bob

print('List: %s' % [1, 2, 3])
# Output: List: [1, 2, 3]
```

---

#### **5. Escape Characters**

To include a literal `%` in the string, use `%%`:
```python
print('Discount: %d%%' % 20)
# Output: Discount: 20%
```

---

#### **6. Limitations of `%` Formatting**

- **Readability**: Formatting with `%` can become hard to read, especially with multiple placeholders.
  ```python
  print('Coordinates: (%d, %d)' % (10, 20))
  # Output: Coordinates: (10, 20)
  ```
- **Flexibility**: It lacks features like alignment and nested formatting available in `str.format()` and f-strings.

---

## Reading and Writing Files

Python provides a straightforward way to handle file operations through the `open()` function. File handling is a critical feature for reading data from files and writing data to them. This section delves into the various modes, practices, and precautions when working with files in Python.

---

### **1. `open()` Function**

The `open()` function is the entry point for file operations. It returns a file object used to read, write, or manipulate the file.

**Syntax:**
```python
open(filename, mode, encoding=None)
```

- **`filename`**: Name of the file to open (string).
- **`mode`**: Describes the purpose of file access.
- **`encoding`**: Specifies the text encoding; recommended to use `"utf-8"` unless otherwise required.

---

### **2. File Modes**

The `mode` parameter determines how the file is opened. Below are the common modes:

| Mode | Description                                                                                   |
|------|-----------------------------------------------------------------------------------------------|
| `r`  | Read-only mode (default). The file must exist.                                                |
| `w`  | Write mode. Creates a new file or truncates an existing file.                                 |
| `a`  | Append mode. Writes data to the end of the file, creating it if it doesn’t exist.             |
| `r+` | Read and write mode. The file must exist.                                                     |
| `b`  | Binary mode. Appends to `r`, `w`, or `a` to handle files as bytes objects (e.g., `rb`, `wb`). |

---

### **3. Text Mode vs Binary Mode**

#### **Text Mode** (Default)
- Reads and writes strings.
- Converts platform-specific line endings to `\n` (reading) and back to platform-specific endings (writing).
- Suitable for text files like `.txt` or `.csv`.

#### **Binary Mode**
- Reads and writes data as bytes objects.
- Does not modify line endings.
- Essential for handling binary data like images (`.jpeg`), executables (`.exe`), or audio files.

**Example: Text vs Binary Mode**
```python
# Text mode
with open('example.txt', 'w', encoding='utf-8') as f:
    f.write('Hello, World!\n')

# Binary mode
with open('example.bin', 'wb') as f:
    f.write(b'Binary data')
```

---

### **4. Using the `with` Keyword**

The `with` statement is the preferred way to handle file objects. It ensures the file is automatically closed after its block is executed, even if an exception occurs.

**Example: Using `with`**
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

---

### **5. Writing to Files**

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

---

### **6. Reading from Files**

Use methods like `read()`, `readline()`, or `readlines()` to read data from a file.

- **`read(size)`**: Reads the specified number of characters (or bytes in binary mode).
- **`readline()`**: Reads a single line.
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

### **7. Handling Closed Files**

Once a file is closed (either manually or automatically with `with`), any operations on it will raise an error.

**Example:**
```python
f = open('example.txt', 'r')
f.close()
print(f.read())  # Raises ValueError: I/O operation on closed file
```

---

### **8. Error Handling**

Be cautious when handling files:
1. Use `with` to ensure proper cleanup.
2. Avoid hardcoding paths; use libraries like `os` or `pathlib` for path manipulations.
3. Handle exceptions using `try-except` blocks when necessary.

**Example: Handling Errors**
```python
try:
    with open('nonexistent.txt', 'r') as f:
        content = f.read()
except FileNotFoundError:
    print('File does not exist!')
```

---

### **9. Summary of Good Practices**

1. Always use the `with` statement for file operations.
2. Specify `encoding="utf-8"` for text files unless another encoding is required.
3. Use binary mode for non-text files.
4. Avoid performing operations on closed files.
5. Handle exceptions gracefully to avoid crashes.

### Methods of File Objects**

File objects in Python provide numerous methods to interact with files effectively, whether reading, writing, or manipulating file positions. Below is an in-depth explanation of the most commonly used methods, along with examples for better understanding.

---

### **1. Reading File Contents**

#### **`f.read(size)`**
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

---

#### **`f.readline()`**
- Reads one line from the file.
- Keeps the newline character (`\n`) at the end of the string unless the file doesn’t end with one.
- Returns an empty string (`''`) if the end of the file is reached.

**Examples:**
```python
with open('example.txt', 'r') as f:
    print(f.readline())  # First line
    print(f.readline())  # Second line
    print(f.readline())  # Returns '' if no more lines exist
```

**Handling Blank Lines:**
- A blank line is represented as `'\n'`.

---

#### **Reading Lines Efficiently**
- Iterating over a file object is an efficient and straightforward way to read lines.

**Example:**
```python
with open('example.txt', 'r') as f:
    for line in f:
        print(line.strip())  # Removes trailing newline
```

---

#### **`f.readlines()` or `list(f)`**
- Reads all lines from a file and returns them as a list of strings.

**Example:**
```python
with open('example.txt', 'r') as f:
    lines = f.readlines()
print(lines)
```

---

### **2. Writing to Files**

#### **`f.write(string)`**
- Writes the given string to the file.
- Returns the number of characters written.

**Examples:**
```python
with open('example.txt', 'w') as f:
    num_chars = f.write('This is a test\n')
print(num_chars)  # Output: 15
```

#### Writing Non-String Objects
- Non-string objects must be converted to strings or bytes before writing.

**Example:**
```python
value = ('the answer', 42)
with open('example.txt', 'w') as f:
    f.write(str(value))  # Converts tuple to string
```

---

### **3. File Positioning**

#### **`f.tell()`**
- Returns the current position in the file.
- In binary mode: Number of bytes from the start.
- In text mode: An opaque value that represents the position.

**Example:**
```python
with open('example.txt', 'r') as f:
    print(f.read(10))  # Reads first 10 characters
    print(f.tell())    # Shows the position after 10 characters
```

---

#### **`f.seek(offset, whence)`**
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
- Seeks relative to the beginning (`0`) are allowed.
- Seeking beyond valid offsets produces undefined behavior.

---

### **4. Miscellaneous Methods**

#### **`isatty()`**
- Checks if the file object is connected to a terminal.
- Rarely used in general file handling.

#### **`truncate(size)`**
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

### **Good Practices and Tips**

1. **Iterating Over Files**: Use `for line in f` for efficient line-by-line reading.
2. **Avoid Reading Large Files Fully**: Use `f.read(size)` to limit memory usage.
3. **Always Close Files**:
   - Use the `with` keyword to handle files automatically.
4. **Binary Data**: Use binary mode (`'rb'` or `'wb'`) for non-text files.
5. **Position Handling**: Use `tell()` and `seek()` for precise control over file navigation.

### Saving Structured Data with JSON

Python's `json` module provides an efficient way to serialize and deserialize data for saving and sharing structured data like lists, dictionaries, and nested objects. JSON (JavaScript Object Notation) is a widely used data interchange format, making it a great choice for interoperability.

---

### **Understanding JSON Serialization and Deserialization**

1. **Serialization (Converting Python Objects to JSON)**
   - Serializing is the process of converting Python objects (like lists, dictionaries, or other data hierarchies) into a JSON string representation.
   - This is helpful for saving data to files or transferring it over a network.

2. **Deserialization (Converting JSON to Python Objects)**
   - Deserializing is the process of reconstructing Python objects from a JSON string.
   - Useful for reading structured data stored in JSON format.

---

### **Why Use JSON?**
- Simplifies saving and retrieving complex data types like nested lists and dictionaries.
- Eliminates the need to manually parse and serialize data.
- JSON is widely supported, making it a great format for data exchange across applications and languages.

---

### **Key Functions in the `json` Module**

#### **`json.dumps(obj)`**
- Serializes a Python object into a JSON string.
- **Example:**
```python
import json

data = [1, 'simple', 'list']
json_string = json.dumps(data)
print(json_string)  # Output: '[1, "simple", "list"]'
```

---

#### **`json.dump(obj, file)`**
- Serializes a Python object and writes it directly to a file.
- **Example:**
```python
data = {'name': 'Alice', 'age': 30, 'is_member': True}

with open('data.json', 'w', encoding='utf-8') as f:
    json.dump(data, f)
```

---

#### **`json.loads(json_string)`**
- Deserializes a JSON string into a Python object.
- **Example:**
```python
json_string = '{"name": "Alice", "age": 30, "is_member": true}'
data = json.loads(json_string)
print(data)  # Output: {'name': 'Alice', 'age': 30, 'is_member': True}
```

---

#### **`json.load(file)`**
- Deserializes JSON content from a file and reconstructs it into a Python object.
- **Example:**
```python
with open('data.json', 'r', encoding='utf-8') as f:
    data = json.load(f)
print(data)  # Output: {'name': 'Alice', 'age': 30, 'is_member': True}
```

---

### **Examples of Using JSON**

#### **Saving a Nested Dictionary**
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

---

#### **Reading and Modifying JSON Data**
```python
with open('user_data.json', 'r', encoding='utf-8') as f:
    data = json.load(f)

# Modify the data
data['user']['preferences']['language'] = 'French'

# Save changes back to the file
with open('user_data.json', 'w', encoding='utf-8') as f:
    json.dump(data, f, indent=4)
```

---

### **Important Notes**
1. **UTF-8 Encoding**:
   - JSON files must use UTF-8 encoding. Always specify `encoding="utf-8"` when opening files for reading or writing.

2. **Handling Arbitrary Python Objects**:
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

3. **Comparison with `pickle`**:
   - **Advantages of JSON**:
     - Language-independent: JSON can be used across different programming languages.
     - Safer: JSON doesn’t execute arbitrary code during deserialization.
   - **Advantages of `pickle`**:
     - Can serialize arbitrary Python objects, but it’s Python-specific.
     - Less secure: Deserializing untrusted `pickle` data can execute malicious code.

   **When to Use**:
   - Use JSON for interoperability and when sharing data between different systems.
   - Use `pickle` for Python-specific projects requiring more complex object serialization.

---

### **Best Practices**
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
   - JSON serialization doesn’t support circular references in data structures.

---

### **Advanced Example: Logging JSON Data**
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
