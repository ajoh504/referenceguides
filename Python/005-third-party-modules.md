# 5. Third-party modules

### 5.1 import pyperclip

The pyperclip module comes with the `copy()` and `paste()` functions, which act directly on the computer's keyboard. 

### 5.2 import PyInputPlus

The PyInputPlus module offers more powerful `input()`-like functions. 

Use `import pyinputplus as pyip` to avoid typing the entire module name when calling a PyImportPlus function.

### 5.3 PyInputPlus Functions and optional arguments

1.`inputStr()` is nearly identical to `input()` and `raw_input` except that it contains the benefits of PyInputPlus, such as timeouts

2. `inputNum()` requires a number. Returns an int or float. Has optional `min=`, `max=`, `greaterThan=`, and `lessThan=` keyword arguments. 

3. `inputInt()`/`inputFloat()` requires an int/float respectively, returns int or float. Has optional `min=`, `max=`, `greaterThan=`, and `lessThan=` keyword arguments. 
 
  Example: `x = pyip.inputNum('Enter a number 10 or higher: ', greaterThan=9)` 

  Or use multiple arguments: `x = pyip.inputNum('Type a number between 0 and 10: ', min=0, max=10)`

4. `inputChoice()` requires user to enter one of the provided choices

5. `inputMenu()` provides a menu with numbered or lettered choices for the user

6. `inputDateTime()` requires a date and time

7. `inputDate()`/`inputTime()` requires a date or time respectively

8. `inputYesNo()` requires yes or no
 
9. `inputBool()` requires a Boolean value

10. `inputEmail()` requires a valid email address

11. `inputFilepath()` requires a valid file path 

12. `inputPassword()` hides password as user types

PyInputPlus Sources: [Automate The Boring Stuf Ch. 8](https://automatetheboringstuff.com/2e/chapter8/), [PyPi](https://pypi.org/project/PyInputPlus/), [readthedocs.io](https://pyinputplus.readthedocs.io/en/latest/)


