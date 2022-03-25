### print() function keyword arguments

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
