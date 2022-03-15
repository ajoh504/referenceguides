# Python 
A guide on built-in functions, built-in methods, the standard library, third-party modules, and classes. All examples were used on Python v. 3.10.2

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

Use negative numbers to begin at the ending index: `test[-1]`

Leave the starting or ending index empty to designate as either the first or last index: `test[:5]` or `test[5:]` 

### Change or delete list items with indices

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
### Escape characters

Single quote: `\'`

Double quote: `\"`

Tab: `\t`

Newline: `\n`

Backslash: `\\`

Raw string (use to ignore escape characters: `r`

### String interpolation and f-strings 

Using the `%s` operator within a string to designate where to add new strings. 

```py
var1 = 'bow'
var2 = 'axe'
string1 = 'Legolas used a %s, but Gimli preferred an %s.' % (var1, var2)
print(string1)

# Output: Legolas used a bow, but Gimli preferred an axe.

```
f-strings are similar, except the expression is placed inside of the string. Place `f` in front of the string to edit, and place the variables between `{}`.

```py
var1 = 'bow'
var2 = 'axe'
string1 = f'Legolas used a {var1}, but Gimli preferred an {var2}." 
print(string1)

# Output: Legolas used a bow, but Gimli preferred an axe.
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
### list() and tuple() 

Convert a list to a tuple, or vice versa, using either the `list()` or `tuple()` function. Both functions work with strings. 
```py
character_list = ['Aragorn', 'Legolas', 'Bilbo']
character_tuple = tuple(character_list)
print(character_tuple)

# Output: ('Aragorn', 'Legolas', 'Bilbo')
```
```
character = 'Aragorn'
character = list(character)
print(character)

# Output: ['A', 'r', 'a', 'g', 'o', 'r', 'n']
```

### id() function returns the memory address where the object is stored. 
```py
character = 'Aragorn'
print(id(character))

# Output: Memory address location

```

# Built-In Methods

### keys(), values(), and items() on dictionaries

The `keys()`, `values`, and `items()` methods can be used to loop through the contents of a dictionary. 

```py
Legolas = {'Race': "Elf", 'Weapon': "Bow"}
for k in Legolas.keys():
    print(k)
        
# Output: Race
# Output: Weapon

Legolas = {'Race': "Elf", 'Weapon': "Bow"}
for v in Legolas.values():
    print(v)
    
# Output: Elf
# Output: Bow

Legolas = {'Race': "Elf", 'Weapon': "Bow"}
for k, v in Legolas.items():
    print(k + ': ' + v)
    
# Output: Race: Elf
# Output: Weapon: Bow
```
Combine these methods with the `list()` or `tuple()` functions to receive a new list or tuple with a dictionary's keys, values, or both.
```py
Legolas = {'Race': "Elf", 'Weapon': "Bow"}
print(list(Legolas.keys()))

# Output: ['Race', 'Weapon']
```

Combine with the `in` or `not in` operators to see if the key or value is inside the dictionary. 
```py
Legolas = {'Race': "Elf", 'Weapon': "Bow"}
print('Sword' in Legolas.keys())

# Output: False
```
The `get()` method searches a dictionary for a given key, and takes an optional argument to return if the key is not found.
```py
Gimli = {'Race': "Dwarf", 'Weapon': "Axe"}
print(Gimli.get('Home', 'No home found'))

# Output: No home found
```
### setdefault() with dictionaries

The `setdefault()` method adds a key and sets its default value. If the key is already stored in the dictionary, it returns the value.
```py
Shire = {
  'Location': "Middle Earth",
  'Inhabitants': "Hobbits",
}
test = Shire.setdefault('Location', "")
print(test)

# Output: Middle Earth

Shire = {
  'Location': "Middle Earth",
  'Inhabitants': "Hobbits",
}
test = Shire.setdefault('Farmland', True)
print(Shire)

# Output: {'Location': 'Middle Earth', 'Inhabitants': 'Hobbits', 'Farmland': True}
```

### upper() and lower() on strings

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

Use `isupper()` or `islower()` to return a Boolean value, i.e. `True` or `False` if the string is all upper or lowercase. 

```py
x = 'ABC'
print(x.isupper())

# Output: True
```

### startswith() and endswith()

Use `startswith()` or `endswith()` to return a Boolean value, i.e. `True` or `False` if the string is all upper or lowercase. 

```py
x = 'ABC'
print(x.startswith('a'))

# Output: False
```
### join() and split() 

Pass a list of strings to the `join()` method to return a new string value, with all items in the list concatenated. Preface `join()` with a required string value. Both `join()` and `split()` can act upon the escape characters.  
```py
x = ['abc', 'def']
x = ', '.join(x)
print(x)

# Output: abc, def

```
Use `split()` to break apart a string value into list. 
```py
x = 'abc, def'
x = x.split(', ')
print(x)

# Output: ['abc', 'def']

```
### rjust(), ljust(), and center()

Use `rjust()`, `ljust()`, or `center()` to justify text. A numeric argument is required to specify the number of spaces to justify. The character count of the string is included in this number.
```py
x = 'Flesh wound'
x = x.rjust(13)
print(x)

# Output:   Flesh wound
```
### strip(), rstrip(), and lstrip()

Use `strip()`, `rstrip()`, and `lstrip()` to remove whitespace characters (space, tab, and newline). `rstrip()` and `lstrip()` remove spaces from those sides respectively, and `strip()` removes spaces from both sides. 

```py
x = '          Flesh wound'
x = x.lstrip()
print(x)

# Output: Flesh wound
```
Add an optional string value to be removed instead of the whitespace. 

```py
x = 'Flesh wound'
x = x.lstrip('Flesh')
print(x)

# Output: wound
```

From [ATBS Ch 6:](https://automatetheboringstuff.com/2e/chapter6/)

> isalpha() Returns True if the string consists only of letters and isn’t blank
> 
> isalnum() Returns True if the string consists only of letters and numbers and is not blank
> 
> isdecimal() Returns True if the string consists only of numeric characters and is not blank
> 
> isspace() Returns True if the string consists only of spaces, tabs, and newlines and is not blank
> 
> istitle() Returns True if the string consists only of words that begin with an uppercase letter followed by only lowercase letters


### index() method on iterable data types

Use the `index()` method on lists, tuples, or strings to return the index value of the given item. 

```py
list1 = ['test1', 'test2', 'test3']
print(list1.index('test1'))

# Output: 0
```

### append(), insert(), remove(), sort(), and reverse()  

Use `append()` on a list to append an item to the end of the list. Both methods modify the list in place, so the return value is `None`.

```py
test = [1,2,3,4,5]
print(test.append(6))
print(test)

# Output: None
# Output: [1, 2, 3, 4, 5, 6]
```
Use `insert()` with two required arguments to insert an item at any index. The first argument is the index, the second argument is the item to be added.
```py
test = [1,2,3,4,5]
test.insert(5, 6)
print(test)

# Output: [1, 2, 3, 4, 5, 6]
```
Use `remove()` two remove an item from a list. Useful if you do not know the index of the item to be removed. Otherwise, simply use `del`.
```py
test = [1,2,3,4,5]
test.remove(5)
print(test)

# Output: [1, 2, 3, 4]
```

Use `sort()` to sort items in a list. `sort()` takes an optional keyword: `reverse=True` to sort the items in reverse order.
```py
test = [1,4,5,2,3]
test.sort(reverse=True)
print(test)

# Output: [5, 4, 3, 2, 1]
```
If using `sort` on text, uppercase is sorted first and grouped together, followed by lowercase. Use the optional keyword `key=str.lower` to treat the text as all lowercase. The text is not changed to lowercase, but only treated as such for sorting purposes. 

```py
list1 = ['mordor', 'The Shire', 'gondor']
list1.sort(key=str.lower, reverse=True)
print(list1)

# Output: ['The Shire', 'mordor', 'gondor']
```

Use the `reverse()` method to reverse the items in a list.
```py
test = [1,4,5,2,3]
test.reverse()
print(test)

# Output: [1, 2, 3, 4, 5]
```

# Standard library

Python comes pre-built with a standard library, a collection of modules that can be imported into your code as needed. Import a new module using the `import` statement.

### import random

Use `random.randint()` on a range of numbers to return a random number. 
```py
import random
print(random.randint(1,100))

# Output: a random integer between 1 and 100
```

Use `random.choice()` on a list to return a random item from that list. 

```py
import random
list1 = ['Mordor', 'The Shire', 'Gondor']
print(random.choice(list1))

# Output: a random item from list1
```

Use `random.shuffle()` on a list to shuffle the contents of a list. The list is modified in place. 
```py
import random
list1 = ['Mordor', 'The Shire', 'Gondor']
print(random.shuffle(list1))

# Output: list1 but rearranged randomly
```

Sources [ATBS CH2](https://automatetheboringstuff.com/2e/chapter2/). [ATBS CH4](https://automatetheboringstuff.com/2e/chapter4/)

### import copy

Use `copy.copy()` to copy the contents of one variable to another. Use `copy.deepcopy()` if the contents contain lists within lists. 

### import re / regex

The `re` module allows you to find patterns of text with regular expressionss, or regexes. Use `\d` to denote a digit, and add string values wherever necessary. Use a backslash in front of the string values, such as `\(` for parentheses. 

To search for a US phone number, use the pattern `\(\d\d\d\) \d\d\d-\d\d\d\d` or `(\d{3}) \d{3}-\d{4}` where `{3}` denotes how many `\d`'s to search for. Pass the regex pattern as a string value to `re.compile()` with the `r` string prefix. Note that the space after the area code is a part of the pattern.

```py
import re
us_phone_regex = re.compile(r'(\d\d\d) \d\d\d-\d\d\d\d')

```
Pass a string to the `search()` method to see if it matches the pattern stored in the regex object. `None` is returned if the pattern is not found. A match object is returned if the pattern is found. 

```py
import re
us_phone_regex = re.compile(r'\(\d\d\d\) \d\d\d-\d\d\d\d')
num_search = us_phone_regex.search('(555) 555-1234')
print('Phone is a valid US number:', num_search.group())

# Output: Phone is a valid US number: (555) 555-1234
```

In the above example, `num_search` is the variable where the match object is stored. Calling the variable on the `group()` method returns the pattern match. 

### groups within regex objects

`\(` or `\)` allow the parentheses to be part of the string. But parentheses can be used without `\` to create groups within the regex. 

Sources: [ATBS CH 7](https://automatetheboringstuff.com/2e/chapter7/)

# Third-party modules

### import pyperclip

The pyperclip module comes with the `copy()` and `paste()` functions, which act directly on the computer's keyboard. 


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
