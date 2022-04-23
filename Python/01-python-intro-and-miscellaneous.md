# 1. Python intro / misc

Explanations of certain Python concepts accompanied by code samples

### 1.1 Escape characters

Escape characters allow you to use special characters inside strings without affecting the interpreter. For quotes, single quotes can be used inside of double quotes (or vice versa) in place of using a backslash character. Example: 'Test your string "inside a string" like this'
```py
#Single quote: 
\'

#Double quote: 
\"

#Tab: 
\t

#Newline: 
\n

#Backslash: 
\\
```
### 1.2 Raw strings

Raw strings can be used to ignore escape characters. This is useful if you have a string with lots of backslash characters that need to be printed, such as a Windows file path. Use the r just before the string: r'\\MontyPC\C:\Windows\System32\cmd.exe'

### 1.3 String interpolation and f-strings

Use the %s operator within a string to designate where to add new strings.
```py
var1 = 'bow'
var2 = 'axe'
string1 = 'Gimli used an %s, but Legolas preferred a %s.' % (var2, var1)
print(string1)

# Output: Gimli used an axe, but Legolas preferred a bow.
```
f-strings are similar, except the expression is placed inside of the string. Place f in front of the string to edit, and place the variables between {}.
```py
var1 = 'bow'
var2 = 'axe'
string1 = f'Gimli used an {var2}, but Legolas preferred a {var1}.' 
print(string1)

# Output: Gimli used an axe, but Legolas preferred a bow.
```
### 1.4 try and except statements

For error handling, use the try and except statements.
```py
try:
    print(var)
except:
    print('Variable not defined')

# Output: Variable not defined
```
Use the except statement multiple times if desired. Point the except statement to specific error messages.
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
Use else or finally as optional statements. The else block executes if no errors occured. The finally block executes whether or not errors occured.
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
### 1.5 tuple unpacking/multiple assignment

Tuple unpacking is a shortcut for assigning each item in a list to its own variable. The variable names must equal the number of items in the list or else an error will occur.
```py
character_list = ['Aragorn', 'Legolas', 'Bilbo']
human, elf, hobbit = character_list
print(human, elf)

# Output: Aragorn Legolas
```
### 1.6 indexing and slicing

Use indexing notation to slice items from a list or string. Syntax: `list[i:j]` where i is the starting index and j is the stopping index.
```py
test = [1, 2, 3, 4, 5, 6]
test = test[0:2]
print(test)

# Output: [1, 2]
```
Use slicing in a for loop by adding a numeric value to i. This designates the stopping point as (x) amount + i.
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

Sources: [Stack Overflow](https://stackoverflow.com/questions/394809/does-python-have-a-ternary-conditional-operator), [W3 Schools](https://www.w3schools.com/python/python_conditions.asp)
    
### 1.9 List Comprehension
    
Use list comprehension to create a new list based on a prior list, while also combining a for loop into a single line. Syntax: `<new list> = <expression> for <iterator> in <iterable> if <condition is True>.`

```py
prior_list = [1,2,3]
new_list = [i for i in prior_list if i > 0]
print(new_list)

# Output: [1,2,3]
```
    
Sources: [W3 Schools](https://www.w3schools.com/python/python_lists_comprehension.asp), [Python Docs](https://docs.python.org/3/tutorial/datastructures.html)

### 1.10 Use if/else in list comprehension

To use an else statement inside of list comprehension, re-order the syntax as such: `<new list> = <expression> if <condition is True> else <expression> for <iterator> in <iterable>`

```py
prior_list = [1,2,3]
new_list = [i if i > 0 else 'Cannot append list item' for i in prior_list]
print(new_list)

[1, 2, 3, 'Cannot append list item']
```

[Stack Overflow](https://stackoverflow.com/questions/4260280/if-else-in-a-list-comprehension)

### 1.11 is not None

Use `is` or `is not` when comparing a value against `None` rather than using `==` or `!=`. This will convert `None` to a Boolean value, such as when comparing against the match object of a regex. This is useful if the return statement needs to be a Boolean value, and the expression evaluates to a possible `None` value. Example: if a regex finds no match, it returns `None`. So `None is not None` evaluates to `False`. If a regex does return a match object, then `None is not None` evaluates to True. 

Sources: [Stack Overflow](https://stackoverflow.com/questions/14247373/python-none-comparison-should-i-use-is-or), [W3 Schools](https://www.w3schools.com/python/ref_keyword_not.asp), [Stack Overflow](https://stackoverflow.com/questions/3914667/false-or-none-vs-none-or-false)
