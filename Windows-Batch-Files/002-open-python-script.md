### 2. Open a python script in cmd.exe

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
