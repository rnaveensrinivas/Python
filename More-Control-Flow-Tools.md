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

