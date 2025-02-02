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

