# Reference Guides

Explanations and code snippets on syntax, operators, functions, and built-in methods.

[Batch file reference guide](#batch-files)

# Python 

# Python Built-In Methods

### upper() and lower() methods:

The upper() and lower() methods must be called on a string value. They return a new string either in all uppercase or all lowercase.

```
x = 'Abc'
x = x.upper()
print(x)

x = x.lower()
print(x)

# Output: 'ABC'
# Output: 'abc'
```
### Python Custom Classes

In Python, a custom class can be created to organize and store objects.

class test_class:
  pass

test = test_class()
print(test)

# Output: <__main__.testClass object at 0x7fd88c5c6520>

Because the class is empty, the print statement returns the memory address where the object is stored. 
```
class test_class:
  x = 5
  y = 6

test = test_class()
print(test.x)
print(test.y)

# Output: 5
# Output: 6
```
Sources: 
https://learnpython.com/blog/custom-class-python/
https://www.w3schools.com/python/python_classes.asp
https://docs.python.org/3/tutorial/classes.html

# Batch Files
