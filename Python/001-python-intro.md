# Python intro

This reference guide contains brief explanations of certain Python concepts and how to implement them. It is not a tutorial, but instead it shows samples of code along with notation for what the code does.

### 1.1 Escape characters

Escape characters allow you to use special characters inside strings without affecting the interpreter. For quotes, single quotes can be used inside of double quotes (or vice versa) in place of using a backslash character. Example: 'Test your string "inside a string" like this'
```py
Single quote: \'

Double quote: \"

Tab: \t

Newline: \n

Backslash: \\
```
### 1.2 Raw strings

Raw strings can be used to ignore escape characters. This is useful if you have a string with lots of backslash characters that need to be printed, such as a Windows file path. Use the r just before the string: r'\\MontyPC\C:\Windows\System32\cmd.exe'

### 1.3 String interpolation and f-strings

Use the %s operator within a string to designate where to add new strings.
```py
var1 = 'bow'
var2 = 'axe'
string1 = 'Legolas used a %s, but Gimli preferred an %s.' % (var1, var2)
print(string1)

# Output: Legolas used a bow, but Gimli preferred an axe.
```
f-strings are similar, except the expression is placed inside of the string. Place f in front of the string to edit, and place the variables between {}.
```py
var1 = 'bow'
var2 = 'axe'
string1 = f'Legolas used a {var1}, but Gimli preferred an {var2}." 
print(string1)

# Output: Legolas used a bow, but Gimli preferred an axe.
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

Tuple unpacking is a shortcut for assigning each item in a list to their own variable. The variable names must equal the number of items in the list or else an error will occur.
```py
character_list = ['Aragorn', 'Legolas', 'Bilbo']
human, elf, hobbit = character_list
print(human, elf)

# Output: Aragorn Legolas
```
### 1.6 indexing and slicing

Use indexing notation to slice items from a list or string. Syntax: list[i:j] where i is the starting index and j is the stopping index.
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
Use negative numbers to begin at the ending index: test[-1]

Leave the starting or ending index empty to designate as either the first or last index: test[:5] or test[5:]

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
