# Virtual Environments and Packages

In Python, applications may require external packages and modules that are not part of the standard library. Sometimes, different applications require different versions of the same package, which could lead to version conflicts. To solve this problem, Python provides the concept of **virtual environments**. 

A virtual environment is a self-contained directory tree that contains a specific version of Python along with additional packages. This allows different applications to use different versions of Python and libraries without interfering with each other.

For example:
- Application A might need version 1.0 of a library.
- Application B might need version 2.0 of the same library.

By creating separate virtual environments, Application A and B can use different versions without conflict. Upgrading one environment does not affect the other.

## Creating Virtual Environments

The `venv` module in Python is used to create and manage virtual environments. This module installs the version of Python that is currently being used to execute the command.

### Steps to create a virtual environment:
1. **Choose a directory** where you want the virtual environment to be created.
2. **Run the `venv` module** to create the virtual environment:
   ```bash
   python -m venv tutorial-env
   ```
   This will create the `tutorial-env` directory and place a copy of the Python interpreter along with supporting files inside it.

3. **Directory Naming Convention**: A common practice is to name the virtual environment `.venv`. This keeps the directory hidden in Unix-like systems and prevents it from interfering with environment variable definition files.

## Activating the Virtual Environment:

```bash
source tutorial-env/bin/activate
```

Activating the environment changes your shell prompt to indicate which virtual environment you are using and modifies the environment so that the `python` command uses the correct version from the virtual environment.

Example:
```bash
$ source ~/envs/tutorial-env/bin/activate
(tutorial-env) $ python
```

## Deactivating the Virtual Environment:
To deactivate a virtual environment and return to the system's Python installation, simply run:
```bash
deactivate
```

## Managing Packages with pip

`pip` is the Python package manager that allows you to install, upgrade, and remove packages from the virtual environment. By default, `pip` installs packages from the Python Package Index (PyPI).

### Basic `pip` Commands:
- **Install a package**:
   ```bash
   python -m pip install <package-name>
   ```

- **Install a specific version of a package**:
   ```bash
   python -m pip install <package-name>==<version>
   ```

- **Upgrade an existing package**:
   ```bash
   python -m pip install --upgrade <package-name>
   ```

- **Uninstall a package**:
   ```bash
   python -m pip uninstall <package-name>
   ```

### Viewing Package Information:
- **Show package details**:
   ```bash
   python -m pip show <package-name>
   ```
   This displays metadata about the package, such as its version, location, and dependencies.

- **List installed packages**:
   ```bash
   python -m pip list
   ```

- **Freeze installed packages**:
   ```bash
   python -m pip freeze
   ```
   This outputs a list of installed packages in a format suitable for use in a `requirements.txt` file.

### Using `requirements.txt`:
A `requirements.txt` file lists all the necessary packages and their versions for a Python application. This file can be committed to version control and shared with others. To install all the dependencies from a `requirements.txt` file:
```bash
python -m pip install -r requirements.txt
```

This allows other users to set up the same virtual environment with the same dependencies.

### Example of using `requirements.txt`:
```bash
$ python -m pip freeze > requirements.txt
$ cat requirements.txt
novas==3.1.1.3
numpy==1.9.2
requests==2.7.0
```
To install the dependencies:
```bash
$ python -m pip install -r requirements.txt
```

