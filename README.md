# Reproducer for namespace package issue in PyCharm

### Steps to reproduce
Once you have cloned the repository you can set up the environment as follows.

#### Initialise the virtual environment
```shell
# this ensures the virtual environment is created in the project directory
poetry config --local virtualenvs.in-project true
# this sets the environment up with all the required dependencies
poetry install
```

#### Open the `namespace` project in PyCharm
Once opened do the following.

1. Set the interpreter if not already detected (`namespace/.venv/bin/python`).
2. Mark `src` as source directory for the project.

### Expected behaviour
The file at [`namespace/src/namespace/hello.py`](namespace/src/namespace/hello.py) should not have any inspection errors.

### Actual behaviour
The file [`namespace/src/namespace/hello.py`](namespace/src/namespace/hello.py) has inspection errors, like shown here.

```
Cannot find reference 'core' in '__init__.py'
```

This is because PyCharm does not correctly detect `namespace-core` in the active environment when the `__init__.py` is 
omitted in the `namespace-core` and a source directory is marked in `namespace`.
