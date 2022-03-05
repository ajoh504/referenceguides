# Windows Batch Files

Windows batch files are typically stored in a plain text file and saved with the .cmd or .bat extension. In newer versions of Windows, they are run using the cmd.exe application. Most batch files will begin with the

### Variable declaration

To declare a variable in a batch file, use the `set` command, name the variable, then initialize it with a value.
```bat
@ECHO OFF
SET var1='Hello World'
ECHO %var%


```
