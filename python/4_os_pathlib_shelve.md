# 4. os, pathlib, shelve, shutil, and zipfile modules

### 4.1 import pathlib / path() function

The pathlib module offers a number of functions for working with file paths. Use the `/` operator to the right of the `Path()` function to concatenate multiple parts of a file path, such as directories and file names. 

The benefit of the `Path()` function is that it uses the appropriate file path conventions for whatever operating system the user is on. So `\` in Windows file paths would be converted to `/` on macOS and Linux, and vice versa. 

Create a Path object by passing a valid file path to the `Path()` function.

```py
from pathlib import Path
new_filepath = Path('C:\\') / 'new_folder' / 'new_file.txt'
print(new_filepath)

# Output: C:\new_folder\new_file.txt
```
### 4.2 Path.cwd() and Path.home()

Use the `Path.cwd()` function to return the current working directory as a Path object. 

Use the `Path.home()` function to return the user's home directory as a Path object. 

### 4.3 pathlib class attributes

The pathlib module contains class attributes that return various parts of the file path. Use the syntax `x = Path('C:/Windows/commands.txt')` to create a Path object, and call the attributes on the variable x, such as `x.anchor`

`x.anchor` returns `'C:\\'`

`x.parent` returns `WindowsPath('C:/Windows/')`

`x.name` returns `'commands.txt'`

`x.stem` returns `'commands'`

`x.suffix` returns `'.txt'`

`x.drives` returns `'C:'`

### 4.4 glob() method

Use the `glob()` method to search for specific files and subdirectories within a specified directory. The `glob()` method receives arguments that are similar to regular expressions. For example, the `'*'` argument returns every file and subdirectory within the directory. First, create a Path object, then call the `glob()` method on the Path object, and pass it to the `list()` function. 

```py
from pathlib import Path

x = Path.cwd()
y = list(x.glob('*'))
print(y)

# Output: A list of all files and subdirectories in your current working directory 

```

Follow the `'*'` argument with a file extension to return all items with that file type: `x.glob('*.pdf')`

### 4.5 exists(), is_dir(), and is_file()

`x.exists()` returns a Boolean value determining whether the file path is valid. This also works with external and optical drives. 

`x.is_dir()` or `x.is_file()` returns a Boolean value determining whether the path is a directory or file, respectively. 

### 4.6 read(), write(), and open()

`x.write_text(<string argument>)` writes text to a plain text file as long as x contains a valid file. The text must be supplemented as a string argument. `x.read_text()` will return the contents of the plain text file contained in the variable x. 

Path objects can be used in conjunction with Python's `open()` and `read()` methods. The `open()` method opens a file in read mode by default. Pass a string value or a Path object into the `open()` method to open the file. The `read()` method allows you to read the contents of the file. 

```py
x = open('C:\\SomeDir\\SomeFile.txt', 'r')
y = x.read()
print(y)

# Output: A string of all the contents of SomeFile.txt
```
Alternatively, the `readlines()` method can be used to obtain a list of all string contents, separated by lines. 

To write contents to an open file, you must open the file in either write mode or append mode. Write mode overwrites whatever is previously contained in the file. Append mode adds to the file. Use `'w'` or `'a'` as an optional argument to specify either mode. If the specified file doesn't exist, write or append mode will create it. Be sure to close the file before committing any other actions, such as reading the file. 

```py
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

Source(s): [ATBS CH 9](https://automatetheboringstuff.com/2e/chapter9/)

### 4.7 import os, chdir(), and makedirs()

Use `os.chdir()` to change directories by inputting a string value as an argument. 

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

Source(s): [ATBS CH 9](https://automatetheboringstuff.com/2e/chapter9/) and [ATBS CH 10](https://automatetheboringstuff.com/2e/chapter10/)

### 4.9 import shelve

The shelve module will allow you to create and store variables to binary files. In the following code, if 'test_shelve' does not exist, the program will create it. In a Windows environment, there will be three files created in the current working directory: .dat, .bak, and .dir. Once the file is open, you can store values similar to a dictionary by using key/value pairs. 

```py
import shelve
import os

os.chdir('Enter desired directory. The binary files will be stored here')
x = shelve.open('test_shelve')
data_list = ['test1', 'test2']
x['data_list'] = data_list
x.close()
```
Source(s): [ATBS CH 9](https://automatetheboringstuff.com/2e/chapter9/)

### 4.10 import shutil

Use `shutil.copy('source file', 'destination path')` to copy a file and paste it the source destination. This works on both strings and Path objects. The `copy()` method returns a string of the new file path. The new file can be renamed by specifying a new file name in the 'destination path.'

```py
import shutil
shutil.copy('C:\\newFile.txt', 'C:\\newFolder')
```
Use `shutil.copytree('source directory', 'destination path')` to copy the files, directories, and subdirectories of a specified location. This method returns a string of the new file path. The destination path must not exist for this method to work, so you must specify a new destination for the method to create!



Use `shutil.move('source', 'destination path')` to move a file or directory to the given location. This method returns a string of the new file path. If a file with the same name already exists at the source then it will be overwritten during the move. The file can also be renamed during the move by specifying a new name in the 'destination path' section.

Use `shutil.rmtree('file path')` to remove a directory as well as all files and subdirectories

Source(s): [ATBS CH 10](https://automatetheboringstuff.com/2e/chapter10/), [Stack Overflow - FileExistsError](https://stackoverflow.com/questions/54491021/why-am-i-getting-the-error-fileexistserror-winerror-183-cannot-create-a-fil)

### 4.11 create and read zip files with the zipfile module

To create a zipfile in the current working directory, call the `ZipFile()` function in write mode, and use the `write()` method to add files and specify the compression type, such as ZIP_DEFLATED. You must close the ZipFile object just as you would a file object. Note that `'w'` overwrites and previously existing files and `'a'` adds to them. 

```PY
import zipfile
zip_object = zipfile.ZipFile('newfile.zip', 'w')
zip_object.write('file_to_add.txt', compress_type=zipfile.ZIP_DEFLATED)
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
