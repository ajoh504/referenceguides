# Python 

A guide on built-in functions, built-in methods, the standard library, and custom class creation. Links to sources are provided where applicable. All examples were used on Python v. 3.10.2

# Built-In Functions

### range() function with for loops

The range() function returns a series of numbers. By default it starts at 0 and increments by 1. An integer argument is required to designate the stopping point, and the stopping point integer is not returned. The range() function can also be called directly inside a for loop.

```py
for i in range(3):
  print(i)
 
# Output: 0
# Output: 1
# Output: 2
```

Optionally, the range() function can receive two arguments: range(start, stop). It can also receive up to three arguments: range(start, stop, step). Start and stop refer to the beginning and ending integers, and step refers to the incrementation. 

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

range() function sources:

https://automatetheboringstuff.com/2e/chapter2/

# Built-In Methods

### upper() and lower() methods:

The upper() and lower() methods must be called on a string value. They return a new string either in all uppercase or all lowercase.

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

In Python, a custom class can be created to organize and store objects using the `class` keyword. If the class is empty, the print statement returns the memory address where the object is stored.

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

The `__init()__` function can receive arguments to assign new values to the class. 

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

    def display_menu(self):
        print(self.entree)
        print(self.dessert)

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

Sources for Python classes: 

https://learnpython.com/blog/custom-class-python/

https://www.w3schools.com/python/python_classes.asp

https://realpython.com/instance-class-and-static-methods-demystified/

https://docs.python.org/3/tutorial/classes.html


# Standard library

Python comes pre-built with a standard library, a collection of modules that can be imported into your code as needed. Import a new module using the `import` statement.

### import random

Standard library sources:

https://automatetheboringstuff.com/2e/chapter2/
