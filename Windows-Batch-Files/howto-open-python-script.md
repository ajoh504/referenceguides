### Open a python script in cmd.exe

To open a python script in the Windows command line, simply save a batch script containing the file path leading to the python script. Use `py` or `py.exe` before the file path. 
```cmd
@ECHO OFF
py "C:\Sample Folder\test.py"
PAUSE
```

To run the batch script, either double click it, or use Win+R and enter the file path of the batch script.
