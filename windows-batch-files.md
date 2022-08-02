# 1. Intro to Windows Batch Files

Windows batch files are typically stored in a plain text file and saved with the .cmd or .bat extension. In newer versions of Windows, batch scripts run in the cmd.exe program which is stored by default at C:\Windows\System32\cmd.exe. The `ECHO` command is used to display messages on-screen. The `@ECHO OFF` command can be used at the beginning of a batch file to disable echoing for the entire script. To create comments in a batch file, use `::` or `REM`.

### 1.1 Variable initialization

To declare a variable in a batch file, use the `set` command, name the variable, then initialize it with the `=` operator and a string value. To print the variable on screen, use the `ECHO` command and surround the variable with `%`.

```cmd
@ECHO OFF
SET var=Hello World!
ECHO %var%

:: Output: Hello World!
```

To declare a variable with an integer value, use the `/A` command.

```cmd
@ECHO OFF
SET /A var=5
ECHO %var%

:: Output: 5
```

echo command:

https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/echo

single quotes vs double quotes: 

https://stackoverflow.com/questions/24173825/what-does-single-quoting-do-in-windows-batch-files

comments in batch files:

https://stackoverflow.com/questions/11269338/how-to-comment-out-add-comment-in-a-batch-cmd

# 2. Open a python script in cmd.exe

To open a python script in the Windows command line, simply save a batch script containing the file path leading to the python script. Use `py` or `py.exe` before the file path. Use `%*` after the file path to pass any arguments from the command line to the python script. 
```cmd
@ECHO OFF
py "C:\Sample Folder\test.py" %*
PAUSE
```

To run the batch script, either double click it, or type Win+R and enter the file path of the batch script.

### 2.1 Add batch script to PATH environment variable

Or, to avoid typing the entire file path in Win+R, add the file path to the PATH environment variable. Navigate to control panel > system > advanced system settings, under the advanced tab, click "enviroment variable." Highlight "Path" then click edit. Add the file path that leads to your batch script. In older versions of Windows, the filepaths must be separated by a semi-colon. 

Now, simply type Win+R and enter the name of your batch script. You don't need to enter the `.bat` or `.cmd` extension. 

### 2.2 Command line arguments 

If you need to pass command line arguments into the python script, you can enter them in Win+R immediately after your batch file name, separated by spaces. 

To access the command line arguments in your python code, import the `sys` module. Command line arguments are stored in the `sys.argv` list. 

### 2.3 Install third party modules with pip

The pip install location must be added to PATH. 

To install a third party module, use the command `pip install --user <ModuleName>`
