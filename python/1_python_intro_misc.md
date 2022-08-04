# 1. Python intro / misc

Code samples were tested using Python 3.10

### 1.1 Escape characters

Use escape characters inside strings to represent characters with special meanings. 

```py
# Single quote: 
\'

# Double quote: 
\"

# Tab: 
\t

# Newline: 
\n

# Backslash: 
\\

# Carriage Return:
\r 	

# Horizontal Tab:
\t

# Vertical Tab:
\v

# Backspace:
\b

# Form Feed:
\f

# Octal Value:
\ooo

# Hex Value:
\xhh

# Null Character:
\0
```

### 1.2 Raw strings

Raw strings can be used to ignore escape characters. This is useful if you have a string with backslash characters, such as a Windows file path. 

Use `r` just before the string: `r'\\MontyPC\C:\Windows\System32\cmd.exe'`

### 1.3 String interpolation and f-strings

Use the `%s` operator within a string to designate where to add new strings. Follow the string with the `%` symbol and a tuple of the data to be passed into the string. 

```py
var1 = 'bow'
var2 = 'axe'
string1 = 'Gimli used an %s, but Legolas preferred a %s.' % (var2, var1)
print(string1)

# Output: Gimli used an axe, but Legolas preferred a bow.
```

f-strings are similar to string interpolation but are more readable. They were added in Python 3.6. 

Place `f` in front of the string then place the variables between `{}`.

```py
var1 = 'bow'
var2 = 'axe'
string1 = f'Gimli used an {var2}, but Legolas preferred a {var1}.' 
print(string1)

# Output: Gimli used an axe, but Legolas preferred a bow.
```

### 1.4 try and except statements

For error handling, use the `try` and `except` statements. Point the `except` statement to specific error messages.

```py
try:
    print(var)
except NameError:
    print('Variable not defined')

# Output: Variable not defined
```
Use the `except` statement multiple times if desired. 

```py
var = 'text'

try:
    print(var + 1)
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
except NameError:
    print('Variable not defined')
else:
    print('No errors found')
finally:
    print('Error handling complete')
    
# Output: Variable not defined
# Output: Error handling complete
```

Use the `raise` statement with the `Exception()` function to create a series of exceptions. Implement this with the `try` and `except` statements.

```py
def error_handler():
    if True:
        raise Exception('Exception thrown:')

try: 
    error_handler()

except Excption as error_message:
    print(error_message)

#Output: 'Exception thrown:'
```

Source(s): [ATBS CH 11](https://automatetheboringstuff.com/2e/chapter11/)

### 1.5 tuple unpacking/multiple assignment

Tuple unpacking is a shortcut for assigning each item in a list or tuple to its own variable. The number of variables must equal the number of items in the list or else an error will occur.

```py
character_list = ['Aragorn', 'Legolas', 'Bilbo']
human, elf, hobbit = character_list
print(human, elf)

# Output: Aragorn Legolas
```

### 1.6 indexing and slicing

Use indexing notation to slice items from a list or string. Syntax: `list[i:j]` where `i` is the starting index and `j` is the stopping index.

```py
test = [1, 2, 3, 4, 5, 6]
test = test[0:2]
print(test)

# Output: [1, 2]
```

Use slicing in a for loop by adding a numeric value to `i`. This designates the stopping point as `(x`) amount + `i`.

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

Leave the starting or ending index empty to designate as either the first or last index: 

`test[:5]` slices the first 5 characters starting at index 0.

`test[5:]` slices the last 5 characters starting at the last index.

### 1.7 Change or delete list items with indices

Use a list index to change the item in a list. A negative index number begins at the end of the list.

```py
test = [1, 2, 3, 4, 5, 6]
test[0] = 'A'
test[-1] = 'F'
print(test)

# Output: ['A', 2, 3, 4, 5, 'F']
```

Use the del keyword to delete a list item.

```py
test = [1, 2, 3, 4, 5, 6]
del test[0]
del test[-1]
print(test)

# Output: [2, 3, 4, 5]
```

### 1.8 Ternary conditional expressions

Combine an `if else` statement into a single line using a ternary conditional. Syntax: `<do this> if <this is True> else <do this>`. The following sample prints `True` if `x` is an even number.

```py
x = 1
y = 2
print(True if x % 2 == 0 else False)

# Output: False
```

Source(s): [Stack Overflow - ternary conditional](https://stackoverflow.com/questions/394809/does-python-have-a-ternary-conditional-operator), [W3 Schools - conditions](https://www.w3schools.com/python/python_conditions.asp)
    
### 1.9 List Comprehension
    
Use list comprehension to create a list with a for loop in a single line. Syntax: `<new list> = <expression> for <iterator> in <iterable> if <condition is True>.` 

```py
prior_list = [1,2,3]
new_list = [i for i in prior_list if i > 0]
print(new_list)

# Output: [1,2,3]
```
    
Source(s): [W3 Schools - lists comprehension](https://www.w3schools.com/python/python_lists_comprehension.asp), [Python Docs - data structures](https://docs.python.org/3/tutorial/datastructures.html)

### 1.10 Use if/else in list comprehension

To use an else statement inside of list comprehension, re-order the syntax as such: `<new list> = <expression> if <condition is True> else <expression> for <iterator> in <iterable>`

NOTE: This is not considered true "list comprehension."

```py
prior_list = [1,2,3]
new_list = [i if i > 0 else 'Cannot append list item' for i in prior_list]
print(new_list)

[1, 2, 3, 'Cannot append list item']
```

[Stack Overflow](https://stackoverflow.com/questions/4260280/if-else-in-a-list-comprehension)

### 1.11 is not None

Use `is` or `is not` when comparing a value against `None` rather than using `==` or `!=`. For certain use cases, this will evaluate to a Boolean value, such as when comparing against the match object of a regex. 

Example: if a regex finds no match, it returns `None`. So `None is not None` evaluates to `False`. If a regex does return a match object, then `None is not None` evaluates to True. 

Source(s): [Stack Overflow - None comparison](https://stackoverflow.com/questions/14247373/python-none-comparison-should-i-use-is-or), [W3 Schools - ref keyword not](https://www.w3schools.com/python/ref_keyword_not.asp), [Stack Overflow - False or None](https://stackoverflow.com/questions/3914667/false-or-none-vs-none-or-false)

### 1.12 import random

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

Source(s): [ATBS CH 2](https://automatetheboringstuff.com/2e/chapter2/), [ATBS CH 4](https://automatetheboringstuff.com/2e/chapter4/)
