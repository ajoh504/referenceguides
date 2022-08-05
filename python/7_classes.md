# 7. Classes

In Python, a custom class can be created using the `class` keyword. The print statement returns the name of the class and the memory address where the object is stored.

```py
class test_class:
  pass

test = test_class()
print(test)

# Output: <__main__.testClass object at 0x7fd88c5c6520>
```

An object is created when a class is assigned to a variable (or when a class is called directly). The variable can be used to invoke values stored inside the class.

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
### 7.1 __init__() and self

The `self` keyword is a parameter that refers to the current instance of the class. It is passed to the `__init__()` function, which is used to create new instances of that class. In this next example, we'll create a new instance called `number` and assign it a value of `5`.

```py
class test_class:
    def __init__(self):
        self.number = 5

test = test_class()
print(test.number)

# Output: 5
```

The `__init()__` function can receive arguments to assign new values to the class. Those values are known as instance attributes because they are only accessible by an instance of the class. 

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

### 7.2 Class attributes vs. instance attributes

Class attributes refer to variables defined within the class, and are shared by all instances of that class. To update the "menu" class, we can add an attribute that describes what type of menu it is. The instance attributes are already defined within the `__init__()` function as `self.entree = entree` and `self.dessert = dessert`

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

### 7.3 Editing or deleting class attributes

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

### 7.4 Instance methods

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
### 7.5 Class methods

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
### 7.6 Static methods

In Python 3.x, static methods are denoted with the `@staticmethod` decorator and do not take the `cls` or `self` parameters. Static methods are standard functions that can be accessed by calling the object instance followed by the function name, such as `obj.static_method()`. A static method cannot modify the class state or instance state. 

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

Sources: [Learn Python - custom class](https://learnpython.com/blog/custom-class-python/), [W3 - classes](https://www.w3schools.com/python/python_classes.asp), [Learn Python - class and static methods](https://realpython.com/instance-class-and-static-methods-demystified/), [Python Docs - classes tutorial](https://docs.python.org/3/tutorial/classes.html)

