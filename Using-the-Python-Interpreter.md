# Using the Python Interpreter

The Python interpreter is a powerful tool that can be used interactively or for executing scripts. 

## Installing Python
To install Python interpreter follow the below commands: 
```bash
$ sudo apt update
$ sudo apt install python3 -y
$ python3 --version
```

### Optional: Adding an alias
You can also add an alias for `python3` so that you don't have to type the full command. For example, `py` or `python`.  To add alias, 

```bash
$ echo "alias python=python3" >> ~/.bashrc
```

## Locating Python
To find Python on your system, use the `whereis` command in Linux-based environments:
```bash
$ whereis python3
python3: /usr/bin/python3 /usr/lib/python3 /etc/python3 /usr/share/python3 /usr/share/man/man1/python3.1.gz
```
The above command lists the paths where Python is installed, including binaries, libraries, configuration files, and documentation.

---

## Invoking the Interpreter interactively

### Standard Invocation of Interactive Interpreter

The interpreter is typically installed at `/usr/bin/python3`. Add `/usr/bin` to your shell's search path (already added if you installed via command line) to invoke it use:
```bash
$ python3
Python 3.12.3 (main, Nov  6 2024, 18:32:19) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```
When invoked interactively, Python reads and executes commands interactively, similar to a Unix shell. This acts as a handy calculator. 

#### Quitting the Interactive Interpreter
You can exit the Python interpreter using one of the following methods:
- **Control Commands**:
  - `CTRL-Z` Suspends the program. 
    - To get back to the interpreter, `fg job_id_of_python_program`.
  - `CTRL-D` Pressing the shortcut on an **empty command** quits the program. 
    - For example, `>>> var=10 CTRL-D` just beeps and does nothing. 
- **Commands**:
  - `exit()`
  - `quit()`

### Command Line Options
#### Execute Commands Directly:
Use `-c` to execute Python commands inline and qutoe the entire command to avoid shell issues with special characters.
```bash
# Syntax
$ python -c "commands"

# Example
$ python -c "print('Hello, World')"
Hello, World
```

#### Execute Modules: 
Use `-m` to run Python modules as scripts:
```bash
# Syntax
$ python -m module_name [arguments]

# Example
$ cat script.py 
import sys
print(sys.argv)
$ python -m script passing arguments
['/home/usr/Desktop/script.py', '-m', 'script.py', 'passing', 'arguments']
```
**Note**: Don't use the extension `.py` in the module name. 

#### Interactive Mode After Script: 
Use `-i` to enter interactive mode after running a script. 

```bash
# Syntax
$ python -i file

# Example
$ cat script.py
print("Hello, World!")

$ python -i script.py
Hello, World!
>>> # we have enetered interactive mode after executing the script.py
>>>
```
## Running a Script
To run a Python script follow the below syntax: 
```bash
# Syntax
$ python script_name.py

# Example
$ python script.py
print("Hello, World!")
```

## Interactive Mode
When commands are read from ???tty, the interpreter is said to be in interactive mode. 
```bash
$ python3
Python 3.12.3 (main, Nov  6 2024, 18:32:19) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> for i in range(10):
...     print(i, end=" ")
... print()
... 
0 1 2 3 4 5 6 7 8 9 
>>> 
```
* `>>>` is called **primary command**
* `...` is called **secondary command**, they are used 
  * to create multiline code
  * to quit a secondary prompt type in a blank line (leave the secondary prompt all by itself). 
  
**Tip**: To clear the interactive session screen use `CTRL+L`.

## Interactive Editing and History Features in Python
The interpreter's line-editing features include interactive editing, history substitution and code completion **on systems that support the GNU Readline library**.

### Key Features:

#### Line Editing & History Substitution: 
Some Python interpreters support editing of the current input line and history substitution using the GNU Readline library, similar to Korn and Bash shells.

#### Tab Completion: 
- Automatically enabled at interpreter startup.
- Supports variable, module, and attribute name completion.
- Works for dotted expressions (e.g., `string.a`) by evaluating up to the last `.` and suggesting attributes of the resulting object.

???Note that this may execute application-defined code if an object with a __getattr__() method is part of the expression.

#### History Management: 
- Input history is saved to `.python_history` in the user directory.
  - Run the command `less ~/.pythong_history` to view history of Python commands you have executed in the interpreter. 
- History persists across interactive interpreter sessions. But each time you close the interactive sessions all the Python environment information is cleared. 

### Limitations:
- No suggestions for proper indentation on continuation lines.
- Limited use of the interpreter's symbol table for completion.
- No built-in tools for checking or matching parentheses, quotes, etc.

### Enhanced Alternatives:
#### IPython:
- Advanced tab completion, object exploration, and history management.
- Highly customizable and embeddable.
#### bpython:
- Similar features with an enhanced interactive experience.

---

## Argument Passing

Python provides a flexible way to handle command-line arguments passed to a script. These arguments are stored in the `sys.argv` list, which resides in the `sys` module.

---

### Accessing Arguments
The command-line arguments are automatically converted into a list of strings and assigned to the `sys.argv` variable. To access this list, import the `sys` module:
```python
import sys
print(sys.argv)
```

#### Understanding the Arguments 
Let's try to understand the arguments that can be passed to Python.
```bash
$ python --help
usage: python3 [option] ... [-c cmd | -m mod | file | -] [arg] ...
Options (and corresponding environment variables):
-b     : issue warnings about converting bytes/bytearray to str and comparing
         bytes/bytearray with str or bytes with int. (-bb: issue errors)
...
Arguments:
file   : program read from script file
-      : program read from stdin (default; interactive mode if a tty)
arg ...: arguments passed to program in sys.argv[1:]
```

From the above, we understand that in ordered to pass argument, we need to have any one of these (**indicators of input source**) `[-c cmd | -m mod | file | -]` to prefix it. We notice that `-` is the default when just `python` is given to command line. But since it is not passed via command line, it will be accounted as an argument. 

```bash
$ python
Python 3.12.3 (main, Nov  6 2024, 18:32:19) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> sys.argv
['']
>>> 
```

```bash
# not passing any of [-c cmd | -m mod | file | -] leads to error. 
$ python trying to pass command line arguments
python3: can't open file '/home/sri/Documents/Python/trying': [Errno 2] No such file or directory

sri@envy:~/Documents/Python
$ python - trying to pass command line arguments
Python 3.12.3 (main, Nov  6 2024, 18:32:19) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> sys.argv
['-', 'trying', 'to', 'pass', 'command', 'line', 'arguments']
>>> 
```
---

### Structure of `sys.argv`
`sys.argv` will always have a valid length (>=1). `sys.argv[0]` always contains the name of the script or the indicator of the input source.
#### Passing no script or argumetns
If no script or arguments are provided: `sys.argv[0]` is an empty string (`''`).
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
#### Passing just the arguments 
If the script is run with `-` (indicating standard input): `sys.argv[0]` is set to `'-'`.
```bash
$ python - trying to pass command line arguments
Python 3.12.3 (main, Nov  6 2024, 18:32:19) [GCC 13.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> len(sys.argv)
7
>>> for arg in sys.argv:
...     print(arg)
... 
-
trying
to
pass
command
line
arguments
>>> 
```
#### Passing Program as String
If using `-c` to execute a command: `sys.argv[0]` is set to `'-c'`.
```bash
$ python -c "import sys; print(sys.argv)"
['-c']
$ python -c "import sys; print(sys.argv)" hello
['-c', 'hello']
$
```
#### Passing a Module
If using `-m` to run a module: `sys.argv[0]` is set to the full name (**absolute path**) of the located module.

```bash
$ cat random_module.py 
import sys
print(f"Arguments are: {sys.argv}")

$ python3 -m random_module
Arguments are: ['/home/sri/Desktop/random_module.py']

$ python -m random_module passing some arguments
Arguments are: ['/home/sri/Desktop/random_module.py', 'passing', 'some', 'arguments']
$ 

```

#### Note
Arguments following `-c` or `-m` are **not consumed** by the Python interpreter itself. These arguments remain in `sys.argv` for the command or module to process directly. This ensures flexibility when passing options to user-defined scripts or modules.

---

## Source Code Encoding

### Default Encoding
Python source files are treated as **UTF-8** by default. This allows characters from most languages to be used in string literals, identifiers, and comments. However, the **standard library uses only ASCII for identifiers** to maintain portability.

### Editor Requirements
**Your editor must**:
1. Recognize the file as UTF-8.
2. Use a font that supports the characters present in the file.

### Declaring a Custom Encoding
To use an encoding other than UTF-8, add a special comment at the beginning of the file:
```python
# -*- coding: encoding -*-
```
- Example for Windows-1252 encoding:
```python
# -*- coding: cp1252 -*-
```

### Custom Encoding and Shebang
If the file starts with a UNIX shebang line (e.g., `#!/usr/bin/env python3`), the encoding declaration should be the **second line**:
```python
#!/usr/bin/python3
# -*- coding: cp1252 -*-
```

---

## Shebang (`#!`) Explained
The shebang line specifies where the interpreter is located inorderd to execute the script. 

### Syntax: 
```
#!/path/to/interpreter

code...
```
### Example - script.py:
```python
#!/usr/bin/python3

print("Hello World")
```
### Purpose:
Enables the script to run directly from the command line without explicitly invoking the interpreter.
```bash
$ ./script.py
```
instead of:
```bash
$ python3 script.py
```
**Note!** You need to have execute permission to run the file. Else you will get error `bash: ./script.py: Permission denied`, when you try to run `./script.py`
```bash
$ cat script.py
#!/usr/bin/python3
print("Hello, World!")
$ chmod +x script.py
$ ./script.py
Hello, World!
```
    
### Shebang Portablility:
The `env` utility (`/usr/bin/env`) is often used for portability. It searches for the interpreter in the system's `PATH`, making the script adaptable across environments.AN INFORMAL INTRODUCTION TO PYTHON


## Summary of Python Interpreter
```
$ sudo apt update
$ sudo apt install python3 -y
$ python3 --version
$ echo "alias python=python3" >> ~/.bashrc
$ whereis python
$ python --help
$ python
^z
^d
exit()
quit()
$ python -c "commands"
$ python -m module_name [arguments]
$ python -i file
$ python - [arguments]
import sys; sys.argv
# -*- coding: encoding -*-
#!/usr/bin/python3
#!/usr/bin/env
```
---
