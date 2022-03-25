### 1.1. try and except statements

For error handling, use the `try` and `except` statements. 

```py
try:
    print(var)
except:
    print('Variable not defined')

# Output: Variable not defined
```

Use the `except` statement multiple times if desired. Point the `except` statement to specific error messages.

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

Use `else` or `finally` as optional statements. The `else` block executes if no errors occured. The `finally` block executes whether or not errors occured.

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
