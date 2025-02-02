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

