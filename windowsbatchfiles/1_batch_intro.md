# 1. Windows Batch Files

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
