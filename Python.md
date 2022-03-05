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

# Custom Classes

In Python, a custom class can be created to organize and store objects. 

```py
class test_class:
  pass

test = test_class()
print(test)

# Output: <__main__.testClass object at 0x7fd88c5c6520>
```

Because the class is empty, the print statement returns the memory address where the object is stored. 

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

Sources for custom classes: 

https://learnpython.com/blog/custom-class-python/

https://www.w3schools.com/python/python_classes.asp

https://docs.python.org/3/tutorial/classes.html

# Standard library

Python comes pre-built with a standard library, a collection of modules that can be imported into your code as needed. Import a new module using the `import` statement.

### import random

Standard library sources:

https://automatetheboringstuff.com/2e/chapter2/
