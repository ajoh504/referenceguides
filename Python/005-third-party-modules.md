# 5. Third-party modules

### 5.1 import pyperclip

The pyperclip module comes with the `copy()` and `paste()` functions, which act directly on the computer's keyboard. 

### 5.2 import PyInputPlus

The PyInputPlus module offers more powerful `input()`-like functions. 

Use `import pyinputplus as pyip` to avoid typing the entire module name when calling a PyImportPlus function.

### 5.3 PyIp Functions and optional arguments

`inputStr()` is nearly identical to `input()` and `raw_input`

The blank argument allows for blank input

```py
import pyinputplus as pyip
x = pyip.inputStr('Please enter your name: ', blank=True)
```

Use the limit keyword argument to limit the number of times a user can attempt to input something, such as a password.

```py
import pyinputplus as pyip
x = pyip.inputStr('Please enter your password: ', limit=5)
```
Use the timeout keyword to have the input timeout after a specified number of seconds

```py
import pyinputplus as pyip
x = pyip.inputStr('You have ten seconds to input the password: ', timeout=10)
```
To avoid throwing an error message when using timeout or limit, use the default keyword. 

```py
import pyinputplus as pyip
x = pyip.inputStr('You have ten seconds to input the password: ', timeout=10, default='Time exceeded')
```

### 5.4 PyIp and inputNum

`inputNum()` requires a number. It returns an int or float and has optional `min=`, `max=`, `greaterThan=`, and `lessThan=` keyword arguments. 

`inputInt()`/`inputFloat()` requires an int/float respectively. It returns int or float and has optional `min=`, `max=`, `greaterThan=`, and `lessThan=` keyword arguments. 

```py
import pyinputplus as pyip
x = pyip.inputNum('Enter a number 10 or higher: ', greaterThan=9)
```
Or use multiple arguments: 
```py
import pyinputplus as pyip
`x = pyip.inputNum('Type a number between 0 and 10: ', min=0, max=10)`
```
`inputChoice()` requires user to enter one of the provided choices

`inputMenu()` provides a menu with numbered or lettered choices for the user

`inputDateTime()` requires a date and time

`inputDate()`/`inputTime()` requires a date or time respectively

`inputYesNo()` requires yes or no

`inputBool()` requires a Boolean value
 
`inputEmail()` requires a valid email address

`inputFilepath()` requires a valid file path 

`inputPassword()` hides password as user types

PyInputPlus Sources: [Automate The Boring Stuf Ch. 8](https://automatetheboringstuff.com/2e/chapter8/), [PyPi](https://pypi.org/project/PyInputPlus/), [readthedocs.io](https://pyinputplus.readthedocs.io/en/latest/)


