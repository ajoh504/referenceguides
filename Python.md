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

Sources [Automate the Boring Stuff CH2](https://automatetheboringstuff.com/2e/chapter2/). [Automate the Boring Stuff CH4](https://automatetheboringstuff.com/2e/chapter4/)

# 2. Built-In Methods

### 2.1 calling keys(), values(), and items() on dictionaries

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
### 2.2 setdefault() with dictionaries

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

### 2.3 upper() and lower() methods with strings

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

### 2.4 startswith() and endswith() with strings

Use `startswith()` or `endswith()` to return a Boolean value, i.e. `True` or `False` if the string begins with the designated string. 

```py
x = 'ABC'
print(x.startswith('a'))

# Output: False
```
### 2.5 join() and split() with a list of strings

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
### 2.6 rjust(), ljust(), and center() to justify text

Use `rjust()`, `ljust()`, or `center()` to justify text. A numeric argument is required to specify the number of spaces to justify. The character count of the string is included in this number.
```py
x = 'Flesh wound'
x = x.rjust(13)
print(x)

# Output:   Flesh wound
```
### 2.7 strip(), rstrip(), and lstrip() to remove whitespace characters

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


### 2.8 index() method on iterable data types

Use the `index()` method on lists, tuples, or strings to return the index value of the given item. 

```py
list1 = ['test1', 'test2', 'test3']
print(list1.index('test1'))

# Output: 0
```

### 2.9 append(), insert(), remove(), sort(), and reverse() with lists

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
# 3. Built-in functions

### 3.1 range() function with for loops

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

### 3.2 range() and len() functions with for loops

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

### 3.3 enumerate() function with for loops

The `enumerate()` function can also be used in a `for` loop instead of `range(len(list))`. The for loop can receive two variables, one for list indices and one for list items.
```py
character_list = ['Aragorn', 'Legolas', 'Bilbo']
for index, item in enumerate(character_list):
    if character_list[index] == 'Bilbo':
        print(item, 'found at index', index)

# Output: Bilbo found at index 2

```


### 3.4 print() function keyword arguments

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


### 3.5 list() and tuple() functions

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


### 3.6 id() function returns the memory address where the object is stored
```py
character = 'Aragorn'
print(id(character))

# Output: Memory address location

```
# 4. os, pathlib, and shelve modules

### 4.1 import pathlib / path() function

The pathlib module allows the user to act on file paths. The `/` operator when used to the right of the `Path()` function acts as a tool to concatenate multiple parts of a file path, such as directories and file names. The benefit of the `path()` function is that it uses the appropriate file path conventions for whatever operating system the user is on. So `\` in Windows file paths would be converted to `/` on Mac OS and Linux, and vice versa. 

```py
from pathlib import Path
new_filepath = Path('C:\\') / 'new_folder' / 'new_file.txt'
print(new_filepath)

# Output: C:\new_folder\new_file.txt
```
### 4.2 Path.cwd() and Path.home()

The `Path.cwd()` function stands for "current working directory. Run it to retrieve the current directory as a string. 

Use `Path.home()` to return the user's home directory as a string. 

### 4.3 pathlib class attributes

The pathlib module contains class attributes that return various parts of the file path. Use the syntax `x = Path('C:/Windows/commands.txt')` and call the attributes on the variable x, such as `x.anchor`

`x.anchor` returns `'C:\\'`

`x.parent` returns `WindowsPath('C:/Windows/')`

`x.name` returns `'commands.txt'`

`x.stem` returns `'commands'`

`x.suffix` returns `'.txt'`

`x.drives` returns `'C:'`

### 4.4 glob() method

Use the `glob()` method to search for specific files and subdirectories within a specified directory. The `glob()` method receives arguments that are similar to regular expressions. For example, the `'*'` argument returns every file and subdirectory within the directory. First, place the desired path into a variable, such as the current working directory: `x = Path.cwd()`. Then, call the `glob()` method on the variable, and pass it to the `list()` function. 

```py
import os
from pathlib import Path

x = Path.cwd()
y = list(x.glob('*'))
print(y)

# Output: A list of all files and subdirectories in your current working directory 

```

Follow the `'*'` argument with a file extension to return all items with that file type: `x.glob('*.pdf')`

### 4.5 exists(), is_dir(), and is_file()

`x.exists()` returns a Boolean value determining whether or not the file path is valid. Works with external and optical drives. 

`x.is_dir()` or `x.is_file()` returns a Boolean value determining whether or not the path is a directory or file, respectively. 

### 4.6 read(), write(), and open()

`x.write_text(<string argument>)` writes text to a plain text file as long as x contains a valid file. The text must be supplemented as a string argument. `x.read_text()` will return the contents of the plain text file contained in the variable x. 

Pathlib's `.read()` method allows you to read the contents of a file. First, pass a valid file path into the `open()` method. The `open()` method opens a file in read mode by default, so the file cannot be written to using this method. The optional arguemnt `'r'` can be passed to the `open()` method to specify opening the file in read mode, but since read mode is the default, `'r'` is optional.

```py
from pathlib import Path
x = open('C:\\SomeDir\\SomeFile.txt', 'r')
y = x.read()
print(y)

# Output: A string of all the contents of SomeFile.txt
```
Alternatively, the `readlines()` method can be used to obtain a list of all string contents, separated by lines. 

To write contents to an open file, you must open the file in either write mode or append mode. Write mode overwrites whatever is previously contained in the file. Append mode adds to the file. Use 'w' or 'a' as the optional argument to specify either of these modes. If the specified file doesn't exist, write or append mode will create it. Be sure to close the file before commiting any other actions, such as reading the file. 

```py
from pathlib import Path
import os

os.chdir('C:\\SomeDir')
x = open('SomeFile.txt', 'a')
x.write('This text will be appended to the file.')
x.close()
x = open('SomeFile.txt', 'r')
y = x.read()
print(y)

# Output: A string of all the contents of SomeFile.txt, plus 'This text will be appended to the file.'
```

Sources: [Automate the Boring Stuff Ch 9](https://automatetheboringstuff.com/2e/chapter9/)

### 4.7 import os, chdir(), and makedirs()

The `os.chdir()` function allows you to change directories by inputting a string value as an argument. 

Use `os.makedirs()` to create a new directory by specifying its absolute file path as a string argument. New subdirectories can be added at the time of making the parent directory. 

Use `os.path.abspath('.')` to return the absolute path of the current working directory. 

Use `os.path.abspath('..')` to return the absolute path of the parent directory. 

Use `os.path.abspath('.\\NewFile')` to return the absolute path of the argument, where 'NewFile' is relative to the current working directory

Use `os.path.relpath(<file path>, <starting path>)` to return the relative path of the first argument, `<file path>`, when starting at the second argument, `<starting path>`.
```py
import os
x = os.path.relpath('C:\\Windows\\System32', '\\some\\file\\path')
print(x)

# Output: '..\\..\\..\\Windows\\System32'
```
The three `..` tell the user to go back three directories, i.e. 'some', 'file', and 'path'. Then, the interpreter provides the relative path from `C:\` to the first argument, which is `\\Windows\\System`

### 4.8 os.unlink() and os.rmdir()

Use `os.unlink()` to remove a single file. Place a file path into the parentheses.

Use `os.rmdir()` to remove a directory. Place a directory path into the parentheses.

Sources: [Automate the Boring Stuff Ch 9](https://automatetheboringstuff.com/2e/chapter9/) and [Automate the Boring Stuff Ch 10](https://automatetheboringstuff.com/2e/chapter10/)

### 4.9 import shelve

The shelve module will allow you to create and store variables to binary files. In the following code, if 'test_shelve' does not exist, the program will create it. On a Windows PC, there will be three files created in the current working directory: .dat, .bak, and .dir. Once the file is open, you can store values similar to a dictionary by using key/value pairs. 

```py
import shelve
import os

os.chdir('Enter desired directory. The binary files will be stored here')
x = shelve.open('test_shelve')
data_list = ['test1', 'test2']
x['data_list'] = data_list
x.close()
```
Sources: [Automate the Boring Stuff Ch 9](https://automatetheboringstuff.com/2e/chapter9/)

### 4.10 import shutil

Use `shutil.copy('source file', 'destination path')` to copy a file and paste it the source destination. This works on both strings and Path objects. The `copy()` method returns a string of the new file path. The new file can be renamed by specifying a new file name in the 'destination path.'

```py
import shutil
shutil.copy('C:\\newFile.txt', 'C:\\newFolder')
```
Use `shutil.copytree('source directory', 'destination path')` to copy all of the files, directories, and subdirectories of a specified location. This method returns a string of the new file path. The destination path must not exist for this method to work, so you must specify a new destination for the method to create!

Source: [Stack Overflow](https://stackoverflow.com/questions/54491021/why-am-i-getting-the-error-fileexistserror-winerror-183-cannot-create-a-fil)

Use `shutil.move('source', 'destination path')` to move a file or directory to the given location. This method returns a string of the new file path. If a file with the same name already exists at the source then it will be overwritten during the move. The file can also be renamed during the move by specifying a new name in the 'destination path' section.

Use `shutil.rmtree('file path')` to remove a directory as well as all files and subdirectories

Sources: [Automate the Boring Stuff Ch 10](https://automatetheboringstuff.com/2e/chapter10/)

### 4.11 create and read zip files with the zipfile module

To create a zipfile in the current working directory, call the `ZipFile()` function in write mode, and use the `write()` method to add files and specify the compression type, such as ZIP_DEFLATED. You must close the ZipFile object just as you would a file object. Note that `'w'` overwrites and previously existing files and `'a'` adds to them. 

```PY
import zipfile
zip_object = zipfile.ZipFile('newfile.zip', 'w')
zip_object.write('file_to_add.txt', compress_type=zipfile.ZIP_DEFLATED))
zip_object.close()
```

Use the `extractall()` method on a ZipFile object to extract its content to the current working directory. Or, pass a directory path into `extractall()` to extract the files to a different location. If the directory does not exist, it will be created. 

```PY
import zipfile
zip_object = zipfile.ZipFile('C:\\Folder\\newfile.zip')
zip_object.extractall()
zip_object.close()
```
Use `extract()` to extract a single file from the ZipFile object to the current working directory. Or, pass a directory path into `extract()` to extract the file to a different location. If the directory does not exist, it will be created.

```PY
import zipfile
zip_object = zipfile.ZipFile('C:\\Folder\\newfile.zip')
zip_object.extract('single_file.txt')
zip_object.close()
```
To read the files contained inside a zipfile, use the `namelist()` method on a ZipFile object.

```PY
import zipfile
zip_object = zipfile.ZipFile('C:\\Folder\\newfile.zip')
x = zip_object.namelist()
zip_object.close()
print(x)

# Output: all the files names from the zipfile
```

# 6. import re / regex

The `re` module allows you to find patterns of text with regular expressions, or regexes. Pass the regex pattern as a string value to `re.compile()` function with the `r` string prefix. This function returns a regular expression object. 

Use `\d` to denote a digit, and add string values wherever necessary. Use a backslash in front of the string values, such as `\(` for parentheses. If you don't use a backslash on the parentheses, they will perform a specific function, which we'll cover later.

To search for a US phone number, use the pattern `\(\d\d\d\) \d\d\d-\d\d\d\d` or `(\d{3}) \d{3}-\d{4}` where `{3}` denotes how many `\d`'s to search for. Note that the space after the area code is a part of the pattern.
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
In the above example, `num_search` is the variable where the match object is stored. Match objects have a specific method called `group()`. Calling the match object variable on the `group()` method returns the pattern match.


### 6.1 groups within regex objects

`\(` or `\)` allow the parentheses to be part of the string. But parentheses can be used without `\` to create groups within the regex. 

Using the code sample from above, we'll separate the phone number into two groups: the area code, and the last seven digits. Since the backslashes denote the parenthese as part of the string, all we need to do is surround each group with a new set of parentheses and leave out the backslash. So the area code from before looks like this: `\(\d\d\d\)`. To separate it into a group, we'll surround it with parentheses: `(\(\d\d\d\))`. Then we'll surround the last seven digits with parentheses: `(\d\d\d-\d\d\d\d)`. The final regex will look like this: `(\(\d\d\d\)) (\d\d\d-\d\d\d\d)`. Or, as mentioned previously, to avoid typing `d` over and over again, we can use a number inside curly braces to denote how many digits to search for: `(\(\d\{3})) (\d{3}-\d{4})`.

To view the match object by group, we call the object using the `group()` method. Passing no argument or `0` into the `group()` method returns the entire match.

```py
import re

us_phone_regex = re.compile(r'(\(\d\d\d\)) (\d\d\d-\d\d\d\d)')
num_search = us_phone_regex.search('(555) 555-1234')
x = num_search.group()
y = num_search.group(0)
print(x)
print(y)

# Output: Phone is a valid US number: (555) 555-1234
# Output: Phone is a valid US number: (555) 555-1234
```

As shown above, the output of `group()` and `group(0)` are the same. Passing `1` into `group(1)` will return the first group only. `2` will return the second group.

```py
import re

us_phone_regex = re.compile(r'(\(\d\d\d\)) (\d\d\d-\d\d\d\d)')
num_search = us_phone_regex.search('(555) 555-1234')
x = num_search.group(1)
y = num_search.group(2)
print(x)
print(y)

# Output: (555) 
# Output: 555-1234
```

Using `groups()` in the plural form prints a tuple of all groups stored in the match object. 

```py
import re

us_phone_regex = re.compile(r'(\(\d\d\d\)) (\d\d\d-\d\d\d\d)')
num_search = us_phone_regex.search('(555) 555-1234')
x = num_search.groups()
print(x)

# Output: ('(555)', '555-1234')

```

### 6.2 Multiple assignment with regex groups

Use the multiple assignment trick to assign the groups to variables

```py
import re

us_phone_regex = re.compile(r'(\(\d\d\d\)) (\d\d\d-\d\d\d\d)')
num_search = us_phone_regex.search('(555) 555-1234')
area_code, suffix = num_search.groups()
print(area_code)
print(suffix)

# Output: '(555)'
# Output: '555-1234'

```

### 6.3 Pipe character with regex groups

The pipe `|` operator works similarly to a logical `or` operator. Using `|` in regular expressions tells the interpreter to return the first occurence of any string in the regular expression. In the following code, we'll create a regex to search for a US area code in two formats: `'555'` or `'(555)'`. Separating the two formats with the `|` operator will return the first occurence of either. Recall that using `\d{3}` tells the interpreter to use `\d` three times. 

```py
import re

us_area_code = re.compile(r'(\(\d{3}\))|(\d{3})')
area_code_mo = us_area_code.search('(555) 555-5555')
x = area_code_mo.group()
print(x)

# Output: (555)
```
The following section is from [Automate the Boring Stuff with Python CH7:](https://automatetheboringstuff.com/2e/chapter7/)

> You can also use the pipe to match one of several patterns as part of your regex. For example, say you wanted to match any of the strings 'Batman', > 'Batmobile', 'Batcopter', and 'Batbat'. Since all these strings start with Bat, it would be nice if you could specify that prefix only once. This can be > done with parentheses. Enter the following into the interactive shell:
> ```py
> batRegex = re.compile(r'Bat(man|mobile|copter|bat)')
> mo = batRegex.search('Batmobile lost a wheel')
> mo.group()
> # Output: Batmobile
> mo.group(1)
> # Output mobile
> ```

In the above text, 'Bat' is used almost as a prefix to the group `(man|mobile|copter|bat)`. The same method can be used as a suffix. Next we'll create a regex that searches for an entire US phone number, but we'll group the area codes first, and use the rest of the phone number as a suffix. The format will be like this: `'((555)|555) 555-5555'`. Two area code formats are grouped together: `(555)` and `555` because they're contained within parentheses and separated by the pipe operator. The second part of the phone number, ` 555-5555`, is used almost as a suffix. The interpreter will search for that exact string. For readability, I'll write out the regex in long form instead of using `\d{3}`

```py
import re

us_phone_number = re.compile(r'(\(\d\d\d\)|\d\d\d) \d\d\d-\d\d\d\d')
number_mo = us_phone_number.search('(555) 555-5555')
x = number_mo.group()
print(x)

# Output: (555) 555-5555

```
### 6.4 Optional matching with the regex question mark

Previously, the code contains a space between the area code and the rest of the phone number. Not all phone numbers contain a space at that position; sometimes numbers are written as `(555)555-5555`. The space can be made optional by using parentheses with a question mark at the end and placing a single space in the middle: `( )?`. 

```py
import re

us_phone_number = re.compile(r'(\(\d\d\d\)|\d\d\d)( )?\d\d\d-\d\d\d\d')
number_mo = us_phone_number.search('(555)555-5555')
x = number_mo.group()
print(x)

# Output: (555)555-5555
```
### 6.5 asterisk and plus sign with regex groups

The `*` symbol before a group matches 0 or more of any string designated in that group. The `+` sign matches 1 or more of any string designated within that group.

### 6.6 Use braces in regex to set a range

We previously covered using braces to designate how many times to search for a given string. `\d{3}` searches for three digits. The braces can also be used to set a range. `\d{1,10}` will return the first occurence of any string within that range.

```py
import re

number = re.compile(r'\d{1,10}')
number_mo = number.search('5555555')
x = number_mo.group()
print(x)

# Output: 555

```
One of the two numbers can be left out. `{,9}` means 0-9, and `{9,}` means start at nine and match infinitely. 

### 6.7 regex greedy vs. non-greedy

Python is greedy be default. In other words, it always matches the longest possible string within a range. To return the shortest possible string instead, use the `?`. Note that the question mark in this context is different than using it to designate an optional string. 

```py
import re

number = re.compile(r'\d{1,10}?')
number_mo = number.search('5555555')
x = number_mo.group()
print(x)

# Output: 5
```

### 6.8 The findall() method with regex

While the `search()` method returns the first occurence of the given string in the regex, the `findall()` method returns a list with every matching string (as long as there are no groups). If there is no match, Python returns an empty string. 

```py
import re

us_phone_number = re.compile(r'\d\d\d-\d\d\d-\d\d\d\d')
x = us_phone_number.findall('555-555-5555')
print(x)

# Output: ['555-555-5555']
```

### 6.9 Regex findall() with groups

If the regex contains either zero or one group, findall() will return a list of string matches. If the regex contains two or more groups, then findall() will return a list of tuples. Inside each tuple are the string matches for each group in the regex. 

The following comes from [Automate the Boring Stuff with Python CH 7:](https://automatetheboringstuff.com/2e/chapter7/)
> ```py
> `phoneNumRegex = re.compile(r'(\d\d\d)-(\d\d\d)-(\d\d\d\d)') # has groups`
> `phoneNumRegex.findall('Cell: 415-555-9999 Work: 212-555-0000')`
> # Output: [('415', '555', '9999'), ('212', '555', '0000')]
> ```
> To summarize what the findall() method returns, remember the following:
> 
> When called on a regex with no groups, such as \d\d\d-\d\d\d-\d\d\d\d, the method findall() returns a list of string matches, such as ['415-555-9999', '212-555-0000'].
> When called on a regex that has groups, such as (\d\d\d)-(\d\d\d)-(\d\d\d\d), the method findall() returns a list of tuples of strings (one string for each group), such as [('415', '555', '9999'), ('212', '555', '0000')].

### 6.10 Regex character classes

The following table comes from [Automate the Boring Stuff with Python CH 7:](https://automatetheboringstuff.com/2e/chapter7/)

> In the earlier phone number regex example, you learned that \d could stand for any numeric digit. That is, \d is shorthand for the regular expression (0|1|2|3|4|5|6|7|8|9).
> 
> \d	Any numeric digit from 0 to 9.
> 
> \D	Any character that is not a numeric digit from 0 to 9.
> 
> \w	Any letter, numeric digit, or the underscore character. (Think of this as matching “word” characters.)
> 
> \W	Any character that is not a letter, numeric digit, or the underscore character.
> 
> \s	Any space, tab, or newline character. (Think of this as matching “space” characters.)
> 
> \S	Any character that is not a space, tab, or newline.

```py
import re

test_regex = re.compile(r'\d+\s+\w+')
x = test_regex.findall('7 Samurai')
print(x)

# Output: ['7 Samurai', '7 samurai']
```

### 6.11 Regex custom classes

Python allows you to create custom classes that function similarly to character classes. For example, there is no class for letters only. But ranges can be set for letters to create a custom class: `[a-zA-z]`. When using regular expression characters inside brackets, the backslash is not needed. For example, `[a-zA-z?!.:;]` searches for all letters plus the punctuation signs. 

Using the caret symbol after the opening bracket creates a negative character class. `[^a-zA-z]` returns all values except letters. Note that by default, your custom character class will only match a single occurence of the given character set, just like a standard character class.  

### 6.12 Beginning and ending symbols with regex

Use the caret symbol at the beginning of a regex to return a match object that begins with the designated string.

```py
import re

test_regex = re.compile('^\d')
test_mo = test_regex.search('7 Samurai')
x = test_mo.group()
print(x)

# Output: 7
```
Use the dollar sign at the end of a regex to return a match object that ends with the designated string.

```py
import re

test_regex = re.compile(r'\d$')
test_mo = test_regex.search('Lucky Number 7')
x = test_mo.group()
print(x)

# Output: 7
```
Using both `^` and `$` tells the compiler to match the entire pattern. Example: `re.compile(r'^\d+$')` will only match a string with a number of any length at the beginning and end. The number cannot contain anything else but a number because it's been surrounded by the caret and dollar sign. 

### 6.13 Wildcard symbol

The period is the wildcard symbol in regexes. It returns any character at that desigation. 

```py
import re

test_regex = re.compile(r'xy.')
test_mo = test_regex.search('xyz')
x = test_mo.group()
print(x)

# Output: xyz
```

### 6.14 Dot-star and re.DOTALL

The dot-star matches everything except newline characters.

```py
import re

test_regex = re.compile(r'abc.*')
test_mo = test_regex.search('abc_xyz\nabc')
x = test_mo.group()
print(x)

# Output: abc_xyz
```

Using `re.DOTALL` as an optional argument in `re.compile()` forces the dot-star to match all characters.


```py
import re

test_regex = re.compile(r'abc.*', re.DOTALL)
test_mo = test_regex.search('abc_xyz\nabc')
x = test_mo.group()
print(x)

# Output: abc_xyz
# Output: abc
```

### 6.15 re.IGNORECASE and re.I

Pass `re.IGNORECASE` or `re.I` as optional arguments to `re.compile()` to ignore case sensitivity. 

```py
import re

test_regex = re.compile(r'abc', re.I)
test_mo = test_regex.search('Abc')
x = test_mo.group()
print(x)

# Output: abc_xyz
```

### 6.16 regex and the sub() method

Use the `sub()` method to replace the matched regex with the given string. The `sub()` method replaces all matches, not just the first occurence. The first string is what replaces the match, and the second string is the item to search through.

```py
import re

test_regex = re.compile(r'abc')
test_replace = test_regex.sub('ABC', 'abc')
print(test_replace)

# Output: ABC
```

If groups exist within the regex, use `\1`, `\2`, and so on, to replace the regex with the text from the given group. The r-string is required before the group number.

```py
import re

test_regex = re.compile(r'abc(\w*)')
test_replace = test_regex.sub(r'\1', 'abcdef')
print(test_replace)

# Output: def
```

### 6.17 re.VERBOSE and multi-line formatting

Complex regexes can be easier to read when broken into multiple lines. With a combination of multiline strings, newlines, spaces, and re.VERBOSE, the regex can be made much more readable. Consider this sample code from [ATBS CH7:](https://automatetheboringstuff.com/2e/chapter7/)

```py
phoneRegex = re.compile(r'''(
    (\d{3}|\(\d{3}\))?            # area code
    (\s|-|\.)?                    # separator
    \d{3}                         # first 3 digits
    (\s|-|\.)                     # separator
    \d{4}                         # last 4 digits
    (\s*(ext|x|ext.)\s*\d{2,5})?  # extension
    )''', re.VERBOSE)
```
To use multiple optional arguments at the end of a regex, separate them with the pipe character: `re.compile('...'. re.VERBOSE | re.DOTALL | re.I)`

### 6.18 Using variables inside regular expressions

A variable containing a string value can be used inside of a regular expression. Simply surround the variable with the `+` operator. The regular expression will evaluate to a concatenated version of the string.

```py
import re
x = 'Legolas'
y = 'Gimli'
z = 'Legolas eventually became friends with Gimli'
regex = re.compile(r'['+x+'].*['+y+']')
mo = regex.search(z)
print(mo.group())

# Output: Legolas eventually became friends with Gimli

```

Sources: [Automate the Boring Stuff with Python CH 7](https://automatetheboringstuff.com/2e/chapter7/), [Python Docs](https://docs.python.org/3/library/re.html), [Python Docs HOWTO](https://docs.python.org/3/howto/regex.html)

# 7. Classes

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

### 7.2 Class attributes vs. instance attributes

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

