# Python 

A guide on built-in functions, built-in methods, classes, and the standard library. All examples were used on Python v. 3.10.2

### try and except statements

For error handling, use the `try` and `except` statements. 

```py
try:
    print(var)
except:
    print('Variable not defined')

# Output: Variable not defined
```

Use the `except` statement multiple times if desired. Point the `except` statement to specific error messages.

```py
var = 'text'

try:
    print(var+1)
except NameError:
    print('Variable not defined')
except TypeError:
    print('Check for int and str')

# Output: Check for int and str
```

Use `else` or `finally` as optional statements. The `else` block executes if no errors occured. The `finally` block executes whether or not errors occured.

```py
try:
    print(var)
except:
    print('Variable not defined')
else:
    print('No errors found')
finally:
    print('Error handling complete')
    
# Output: Variable not defined
# Output: Error handling complete
```
### indexing and slicing

Use indexing notation to slice items from a list or string. Syntax: `list[i:j]` where i is the starting index and j is the stopping index. 

```py
test = [1, 2, 3, 4, 5, 6]
test = test[0:2]
print(test)

# Output: [1, 2]
```

Use slicing in a `for` loop by adding a numeric value to i. This designates the stopping point as (x) amount + i.

```py
var = 'abcd'
for i in range(len(var)):
    print(var[i:i+3])
    
# Output: abc
# Output: bcd
# Output: cd
# Output: d
```

### Change or delete list items with indexes

Use a list index to change the item in a list. A negative index number begins at the end of the list. 


```py
test = [1, 2, 3, 4, 5, 6]
test[0] = 'A'
test[-1] = 'F'
print(test)

# Output: ['A', 2, 3, 4, 5, 'F']
```
Use the `del` keyword to delete a list item. 

```py
test = [1, 2, 3, 4, 5, 6]
del test[0]
del test[-1]
print(test)

# Output: [2, 3, 4, 5]
```
### tuple unpacking 

Tuple unpacking is a shortcut for assigning each item in a list to their own variable. The variable names must equal the number of items in the list or else an error will occur.

```py
character_list = ['Aragorn', 'Legolas', 'Bilbo']
human, elf, hobbit = character_list
print(human, elf)

# Output: Aragorn Legolas
```

# Built-In Functions

### range() function with for loops

The `range()` function returns a series of numbers. By default it starts at 0 and increments by 1. An integer argument is required to designate the stopping point, and the item at the stopping point index is not returned. The `range()` function can also be called directly inside a `for` loop.

```py
for i in range(3):
  print(i)
 
# Output: 0
# Output: 1
# Output: 2
```

Optionally, the `range()` function can receive two arguments: `range(start, stop)`, or three arguments: `range(start, stop, step)`. Start and stop refer to the beginning and ending integers, and step refers to the incrementation. 

```py
x = range(7, 10)
for i in x:
  print(i)
 
# Output: 7
# Output: 8
# Output: 9
```
The step argument can be used in a variety of scenarios. For example, printing only even or odd numbers, or every (x) number. 

```py
for i in range(0, 10, 2):
  print(i)
  
# Output: 0
# Output: 2
# Output: 4
# Output: 6
# Output: 8

for i in range(10, 60, 10):
  print(i)
  
# Output: 10
# Output: 20
# Output: 30
# Output: 40
# Output: 50
```

range() sources: [ATBS](https://automatetheboringstuff.com/2e/chapter2/)

### range() and len() functions in for loops

Call `len()` inside of `range()` when accessing multiple items in a single list, or when accessing both the index and the item at that index.


```py
character_list = ['Aragorn', 'Legolas', 'Bilbo']
for i in range(len(character_list)):
    if character_list[i] == 'Bilbo':
        print('Hobbit found')

# Output: Hobbit found
```
Run the above code without the `len()` function and you'll receive the error: `TypeError: 'list' object cannot be interpreted as an integer` because the `range()` function expects to receive an integer. Run the above code without the `len()` and `range()` functions and you'll receive the error: `TypeError: list indices must be integers or slices, not str` because 

Sources: [SO len() range()](https://stackoverflow.com/questions/19184335/is-there-a-need-for-rangelena), [SO TypeError](https://stackoverflow.com/questions/28036309/typeerror-list-object-cannot-be-interpreted-as-an-integer), [SO TypeError](https://stackoverflow.com/questions/32554527/typeerror-list-indices-must-be-integers-or-slices-not-str)

### enumerate() function with for loops

The `enumerate()` function can also be used in a `for` loop instead of `range(len(list))`. The for loop can receive two variables, one for list indices and one for list items.
```py
character_list = ['Aragorn', 'Legolas', 'Bilbo']
for index, item in enumerate(character_list):
    if character_list[index] == 'Bilbo':
        print(item, 'found at index', index)

# Output: Bilbo found at index 2

```
### print() function keyword arguments

The `print()` function always adds a newline character to the end of the printed output. Use `end=''` as an optional parameter with to eliminate the newline character. Any text entered inside the emptry string will also print.

```py
print('test1 ', end='')
print('test2 ', end='test3 ')

# Output: test1 test2 test3
```
Use the `sep=''` keyword to separate multiple strings with whatever you choose to place inside the empty string.

```py
print('1','2','3',sep=', ')

# Output: 1, 2, 3
```

# Built-In Methods

### upper() and lower() methods on strings:

Use the `upper()` or `lower()` methods on a string value. This returns a new string in all uppercase or all lowercase.

```py
x = 'Abc'
x = x.upper()
print(x)

x = x.lower()
print(x)

# Output: 'ABC'
# Output: 'abc'
```

# Classes

In Python, a custom class can be created to organize and store objects using the `class` keyword. The print statement returns the name of the class and the memory address where the object is stored.

```py
class test_class:
  pass

test = test_class()
print(test)

# Output: <__main__.testClass object at 0x7fd88c5c6520>
```

An object is created when a class is assigned to a variable. The variable can be used to invoke values stored inside the class.

```py
class test_class:
  x = 5
  y = 6

test = test_class()
print(test.x)
print(test.y)

# Output: 5
# Output: 6
```
### __init__() and self

The `self` keyword is a parameter that refers to the current instance of the class. It is passed to the `__init__()` function, which is used to create new instances of that class. In this next example, we'll create a new instance called `number` and assign it a value of `5`.

```py
class test_class:
    def __init__(self):
        self.number = 5

test = test_class()
print(test.number)

# Output: 5
```

The `__init()__` function can receive arguments to assign new values to the class. Those values are known as instance attributes, as they are only accesible by that instance of the class. 

```py
class menu:
    def __init__(self, entree, dessert):
        self.entree = entree
        self.dessert = dessert

test = menu("Salmon", "Ice cream")
print(test.entree)
print(test.dessert)

# Output: Salmon
# Output: Ice cream
```

### Class attributes vs. instance attributes

Class attributes refer to variables defined within the class, and are shared by all instances of that class. To update the "menu" class, we can add an attribute that describes what type of menu it is. The instance attributes are already definied within the __init__() function as `self.entree = entree` and `self.dessert = dessert`

```py
class menu:
    # Add class attribute:
    attr = "Dinner menu"
    def __init__(self, entree, dessert):
        self.entree = entree
        self.dessert = dessert

    def display_menu(self):
        print(self.entree)
        print(self.dessert)

test = menu("Salmon", "Ice cream")
print(test.attr)

# Output: Dinner menu
```

### Editing or deleting class attributes

Class attributes can be edited just like the key/value pairs of an object. The `del` keyword can be used to delete an attribute or an entire object.

```py
class menu:
    # Add class attribute:
    attr = "Dinner menu"
    def __init__(self, entree, dessert):
        self.entree = entree
        self.dessert = dessert

test = menu("Salmon", "Ice cream")
test.dessert = "Pie"
del test.entree
print(test.dessert)
print(test.entree)

# Output: Pie
# Output: AttributeError: 'menu' object has no attribute 'entree'
```

### Instance methods

Classes can also contain methods, which are functions that can be called when invoking the class name. The following instance method is called `display_menu()` and it prints all the contents of the menu class. 

```py
class menu:
    def __init__(self, entree, dessert):
        self.entree = entree
        self.dessert = dessert

    def display_menu(self):
        print(self.entree)
        print(self.dessert)

test = menu("Salmon", "Ice cream")
test.display_menu()

# Output: Salmon
# Output: Ice cream
```
### Class methods

In Python 3.x, class methods are denoted with `@classmethod` decorator and take the `cls` parameter. Unlike instance methods, class methods cannot access the attributes of an object. However, a class method can change properties of the class that are accessible to the entire class. The following class method when called allows you to pass an argument that changes the class attribute.

```py
class menu:
    # Add class attribute:
    attr = "Dinner menu"
    def __init__(self, entree, dessert):
        self.entree = entree
        self.dessert = dessert
        
    # Instance method
    def display_menu(self):
        print(self.entree)
        print(self.dessert)

    @classmethod
    # Method to change the class attribute
    def attr_change(cls, new_attr):
        attr = new_attr
        return attr

test = menu("Salmon", "Ice cream")

# Invoke attr_change() method to change the class attribute
menu.attr = menu.attr_change("Lunch menu")
print(menu.attr)

# Output: Lunch menu
```
### Static methods

In Python 3.x, static methods are denoted with the `@staticmethod` decorator and do not take the `cls` or `self` parameters. Static methods are standard functions that can be accessed by calling the object instance followed by the function name, such as `obj.static_method()`. They can also be called as standalone functions without an object instance, such as `static_method()`. A static method cannot modify the class state or instance state. 

```py
class menu:
    # Add class attribute:
    attr = "Dinner menu"
    def __init__(self, entree, dessert):
        self.entree = entree
        self.dessert = dessert
        
    # Instance method
    def display_menu(self):
        print(self.entree)
        print(self.dessert)

    @classmethod
    # Method to change the class attribute
    def attr_change(cls, new_attr):
        attr = new_attr
        return attr
        
    @staticmethod
    def is_class_defined():
      return True

#test = menu("Salmon", "Ice cream")
print(menu.is_class_defined())

# Output: True
```

Sources: [Learn Python](https://learnpython.com/blog/custom-class-python/), [W3](https://www.w3schools.com/python/python_classes.asp), [Learn Python](https://realpython.com/instance-class-and-static-methods-demystified/), [Python Docs](https://docs.python.org/3/tutorial/classes.html)


# Standard library

Python comes pre-built with a standard library, a collection of modules that can be imported into your code as needed. Import a new module using the `import` statement.

### import random

Sources [ATBS CH2](https://automatetheboringstuff.com/2e/chapter2/). [ATBS CH4](https://automatetheboringstuff.com/2e/chapter4/)
