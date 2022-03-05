# Python 

A non-comprehensive guide on built-in functions, built-in methods, and custom class creation. Links to sources where applicable. All examples were used on Python v. 3.10.2

# Built-In Functions

### range() function with for loops

The range() function returns a series of numbers. By default it starts at 0 and increments by 1. An integer argument is required to designate the stopping point, and the stopping point integer is not returned. The range() function can also be called directly inside the for loop.

```py
for i in range(3):
  print(i)
 
# Output: 0
# Output: 1
# Output: 2
```

Optionally, the range() function can receive three arguments: range(start, stop, step). Start and stop refer to the beginning and ending integers, and step refers to the incrementation. 

```py
x = range(7, 10)
for i in x:
  print(i)
 
# Output: 7
# Output: 8
# Output: 9
```

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
