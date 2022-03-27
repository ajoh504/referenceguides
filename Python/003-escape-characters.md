### 3.1 Escape characters

Escape characters allow you to use special characters inside strings without affecting the interpreter. For quotes, single quotes can be used inside of double quotes (or vice versa) in place of using a backslash character. Example: `'Test your string "inside a string" like this'`

Single quote: `\'`

Double quote: `\"`

Tab: `\t`

Newline: `\n`

Backslash: `\\`

### 3.2 Raw strings 

Raw strings can be used to ignore escape characters. This is useful if you have a string with lots of backslash characters that need to be printed, such as a Windows file path. Use the `r` just before the string: `r'\\MontyPC\C:\Windows\System32\cmd.exe'`
