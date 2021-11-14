
![Py-Imports](img/icon-py-import.png)
<p align="center">
    <em>Parse imports from .py file in a flexible way</em>
</p>
<p align="center">
<a href="https://github.com/andresbena19/py-imports/actions?query=workflow%3ATest+event%3Apush+branch%3Amaster" target="_blank">
    <img src="https://github.com/tiangolo/fastapi/workflows/Test/badge.svg?event=push&branch=master" alt="Test">
</a>
<a href="https://codecov.io/gh/andresbena19/py-imports" target="_blank">
    <img src="https://img.shields.io/codecov/c/github/andresbena19/py-imports" alt="Coverage">
</a>

</p>

---

**Source Code**: <a href="https://github.com/andresbena19/py-imports" target="_blank"> https://github.com/andresbena19/py-imports
</a>
## Requirements

Python 3.7+

py-imports stands on the shoulders of giants:

* <a href="https://docs.python.org/3/library/ast.html" class="external-link" target="_blank">ast — Abstract Syntax Trees</a> to traverse python code.

## Installation

<div class="termy">

```console
$ pip install py-imports

---> 100%

All it's ready to begin 
```

</div>

## Example

### Introspect it

* Create a file `main.py` with:

```Python
from py_imports.manager import PyImports

myself = "main.py"

# Let's introspect myself
with PyImports() as manager:
    manager.get_imports(myself)
    imports = manager.imports_resume()


# Now you have access to the imports used in each file 
print(imports)
{
 'main.py': <py_imports.base.models.ImportsCollectionFile object at 0x10b889220>
}

# Get details about the absolute, relative and standard imports in the file
collector_object = imports.get(myself)
absolute_imports = collector_object.absolute_imports
relative_imports = collector_object.relative_imports
imports = collector_object.imports

# It's obvious that in this file there are just one absolute import
#  --- from py_imports.manager import PyImports ---
# If we introspect the object, wi will get the next

first_import = absolute_imports[0]
first_import.childs -> ['PyImports']
first_import.parent -> 'py_imports.manager'
first_import.statement -> 'from py_imports.manager import PyImports'
first_import.level -> 0
first_import.line -> 1

# Now you know more about you...
```

## License

This project is licensed under the terms of the MIT license.
