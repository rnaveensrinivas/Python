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