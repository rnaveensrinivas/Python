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

## Statistics
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

## Turtle

The **turtle** module in Python is a beginner-friendly graphics library used to create simple drawings and animations. It introduces programming concepts visually, making it an excellent tool for learning programming and exploring recursion, geometry, and patterns.

### Key Features:
- **Turtle as a Cursor**: A "turtle" represents a cursor that moves on the screen to draw lines or shapes.
- **Drawing Commands**: Control the turtle to move forward, backward, turn, or lift its pen for movement without drawing.
- **Customization**: You can change the pen color, width, and speed of the turtle.
- **Shapes and Patterns**: Draw geometric shapes like circles, squares, and polygons or create complex patterns using loops and recursion.

### Basic Commands:
1. **Setup**: 
   - `import turtle`: Import the module.
   - `turtle.Turtle()`: Create a turtle object.

2. **Movement**:
   - `forward(distance)`: Move forward by a specified distance.
   - `backward(distance)`: Move backward.
   - `right(angle)` / `left(angle)`: Turn the turtle right or left by a given angle.

3. **Drawing**:
   - `penup()` / `pendown()`: Lift or place the pen to stop or start drawing.
   - `color(color_name)`: Set the pen color.
   - `width(width)`: Set the pen's thickness.

4. **Control**:
   - `speed(speed)`: Adjust drawing speed.
   - `exitonclick()`: Wait for a click to close the turtle window.

### Example:
```python
import turtle

# Create a turtle object
t = turtle.Turtle()

# Set turtle properties
t.color("blue")
t.width(2)

# Draw a square
for _ in range(4):
    t.forward(100)  # Move forward 100 units
    t.right(90)     # Turn right by 90 degrees

# Finish and close the window
turtle.done()
```

### Applications:
- Visualizing recursion (fractals, spirals)
- Drawing geometric shapes
- Animation and simple games


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
| `decimal` | For high precision computing | 
| `turtle` | For beginner friendly graphics | 

