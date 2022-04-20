# 4. Standard library

Python comes pre-built with a standard library, a collection of modules that can be imported into your code as needed. Import a new module using the `import` statement.

### 4.1 import random

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

### 4.2 import copy

Use `copy.copy()` to copy the contents of one variable to another. Use `copy.deepcopy()` if the contents contain lists within lists. 

### 4.3 import pathlib

The pathlib module allows the user to act on file paths. The `/` operator when used to the right of the `Path()` function acts as a tool to concatenate multiple parts of a file path, such as directories and file names. The benefit of the `path()` function is that it uses the appropriate file path conventions for whatever operating system the user is on. So `\` in Windows file paths would be converted to `/` on Mac OS and Linux, and vice versa. 

```py
from pathlib import Path
new_filepath = Path('C:\\') / 'new_folder' / 'new_file.txt'
print(new_filepath)

# Output: C:\new_folder\new_file.txt
```

The `Path.cwd()` function stands for "current working directory. Run it to retrieve the current directory as a string. 

Use `Path.home()` to return the user's home directory as a string. 

The pathlib module contains class attributes that return various parts of the file path. Use the syntax `x = Path('C:/Windows/commands.txt')` and call the attributes on the variable x, such as `x.anchor`

`x.anchor` returns `'C:\\'`

`x.parent` returns `WindowsPath('C:/Windows/')`

`x.name` returns `'commands.txt'`

`x.stem` returns `'commands'`

`x.suffix` returns `'.txt'`

`x.drives` returns `'C:'`

Use the `glob()` method to search for specific files and subdirectories within a specified directory. The `glob()` method receives arguments that are similar to regular expressions. For example, the `'*'` argument returns every file and subdirectory within the directory. First, place the desired path into a variable, such as the current working directory: `x = Path.cwd()`. Then, call the `glob()` method on the variable, and pass it to the `list()` function. 

```py
import os
from pathlib import Path

x = Path.cwd()
y = list(x.glob('*'))
print(y)

# Output: A list of all files and subdirectories in your current working directory 

```

`x.exists()` returns a Boolean value determining whether or not the file path is valid. Works with external and optical drives. 

`x.is_dir()` or `x.is_file()` returns a Boolean value determining whether or not the path is a directory or file, respectively. 

`x.write_text(<string argument>)` writes text to a plain text file as long as x contains a valid file. The text must be supplemented as a string argument. `x.read_text()` will return the contents of the plain text file contained in the variable x. 

Follow the `'*'` argument with a file extension to return all items with that file type: `x.glob('*.pdf')`

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

### 4.4 import os

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

Sources: [Automate the Boring Stuff Ch 9](https://automatetheboringstuff.com/2e/chapter9/)

### 4.5 import shelve

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