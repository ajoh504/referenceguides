# 5. Third-party modules

### 5.1 import pyperclip

The pyperclip module comes with the `copy()` and `paste()` functions, which act directly on the computer's keyboard. 

### 5.2 import PyInputPlus

The PyInputPlus module offers more powerful `input()`-like functions. 

Use `import pyinputplus as pyip` to avoid typing the entire module name when calling a PyImportPlus function.

### 5.3 PyInputPlus Functions and optional arguments

`inputStr()` is nearly identical to `input()` and `raw_input` except that it contains the benefits of PyInputPlus, such as timeouts

`inputNum()` requires a number. Returns an int or float. Has optional `min=`, `max=`, `greaterThan=`, and `lessThan=` keyword arguments. 

`inputInt()`/`inputFloat()` requires an int/float respectively, returns int or float. Has optional `min=`, `max=`, `greaterThan=`, and `lessThan=` keyword arguments. Example: `x = pyip.inputNum('Enter a number 10 or higher: ', greaterThan=9)` Or use multiple arguments: `x = pyip.inputNum('Type a number between 0 and 10: ', min=0, max=10)`

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


