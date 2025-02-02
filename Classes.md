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

