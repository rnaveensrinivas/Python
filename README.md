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
  * `>>>` is called primary command
  * `...` is called secondary command
  
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
  - The `env` utility (`/usr/bin/env`) is often used for portability. It searches for the interpreter in the system's `PATH`, making the script adaptable across environments.