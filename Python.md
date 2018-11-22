## Variables

Just use them, no scoping.

```python
a = 3
```

### Types

* `int`
* `str`
    * `.upper()`, `.lower()`, `.capitalize()`, `.title()`
    * `.isdigit()`, `isalpha()`
    * `.strip()`, `.lstrip()`, `.rstrip()` - Can be used for specific characters
    * `.count("word")`, `.find("word")`, `.replace("old", "new")`
    * `/n` and `/t`
    * Interpolate with "First: {first}, Second: {second}".format(first="first", second="second")
* `float`
* `bool`
    * `True` / `False`

### Collections

* `dict` - Key:Value
    * {a: 1, b: 2}
    * `.pop(key)` - Removes
    * `.has_key(key)`
    * `.keys(), .values()`
    * `==`
* `list` - A general collection
    * `[1, 2, 3,]`
    * `list[0]`
    * `del list`
    * `list[1:3]` - Second through 3rd elements
    * `.append(item)`, `.extend(list)`, `.remove(firstMatch)`, `.insert(position, element)`
    * `.sort()`, `.reverse()`
    * `==`, `!=`, `+` (concat), `*` (repeat)
* `tuple` - An immutable list
    * `(1, 2, 3,)`
* `set` - Unique, unordered
    * `{1, 2, 3}`

## Input

* `input("prompt")` - Get input from the console, try to match data type
* `raw_input("prompt")` - Get input from the console, as a string
* `open()` - Get a file pointer
    * `.readlines()`
    * `.close()` when done
* json.load(file_pointer)
* `getpass("prompt")` - Get hidden input, must be imported with `from getpass import getpass`

## Output

* `print()` - Output to the console
* `format()` - Apply variables to a string
* `open()` - Get a file pointer
    * `.writelines(content)`
    * `.write(content)` - One line
    * Open a file for writing with `open("filename", "w")`
    * Open a file for appending with `open("filename", "a")`
    * Create a file for writing with `open("filename", "w+")`
    * `.close()` when done
* `json.dump(dictionary, file_pointer)` - Print to file
* `json.dumps(dictionary, indent=4)` - Print to screen

## Loops

* `range(start, end, increment)`
* `continue`, `break`

### For

```python
for element in list:
    #
```

### While

```python
age = raw_input("Age?")
while not age.isdigit():
    print "Oops"
    age = raw_input("No, your age:")
```

## Functions

* Arguments must match number of paramenters
    * If variable args, use `**kwargs` (key:value) or `*args` (tuple)
* Optional parameters have to come last
* Can return `multiple, values` (will come back as a tuple)
* Can `destructure, returns`
* Simply pass by value/reference rules as JS

```python
def name(parameter1, parameter2=''):
    #
    return
```

## Conditionals

```python
if some_condition:
    #
elif other_condition:
    #
else:
    #
```

* Each type has their own falsy value
* `not` is the negation operator

## Errors

```python
try:
    #
except:
    #
```

## Math

* `+`/`-`/`*`/`/`/`%`/`**`
* `abs()`
* Negate with `-`
* If the result of a division should be a float, one of the numbers has to be a float (either literal or with `float()`

## Built-Ins

* `type()`
* `len()` - Arrays or Strings

## Classes & Objects

```python
class ClassName(ParentClass):
    def __init__(self, parameter, option=""):
        super(ClassName, self).__init__()
        self.parameter = parameter
    def some_method(self):
        return self.parameter
    def __eq__(self, other): // Allows == comparison
        return self.parameter == other.parameter
    // Also can do eq, ne, gt, lt, gte, lte, str

class_name = ClassName()
```

## Modules

* Include a file called `__init__.py` in any folder you want to add to the path
* Use underscores instead of dashes for names
* The `main()` function is the conventional point of entry for the app

```python
import module
from module import class_or_function
from directory.file_name import class_or_function
from module import *
```

Popular modules:

* `random` - `.randint()`, `.random()`, `.uniform()`. `.choice()`
* `os`
* `json`
* `sqlite3`
* `datetime`
* `getpass`
* `pprint`

### Resolution Order

1. Standard library
2. Current directory
3. External libraries

## Comments

* `#`
* Triple ticks define docstrings, which will show up when passed into `help()`

## OS

* `os.getcwd()` - Current runpath
* `os.listdir('/etc')` - List files in current directory or passed in dir
* `os.makedir('name')` / `os.makedirs('name/nested')`
* `os.stat()` - Get file info

## Debugging

Steps through a file line by line:

`python -n pdb filename.py`

### Commands

* `a` - What arguments are being passed to this function
* `b` - Adds a breakpoint
* `c` - Continues to next break point
* `cl` - Clear all breakpoints
* `l` - List the code around your position
* `n` - Execute the next line of code
* `s` - Step through this line, stopping if you enter a function
* `variable_name` - Current value of variable
