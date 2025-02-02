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


