# Built-in functions

### 1. range() function with for loops

The `range()` function returns a series of numbers. By default it starts at 0 and increments by 1. An integer argument is required to designate the stopping point, and the item at the stopping point index is not returned. The `range()` function can also be called directly inside a `for` loop.

```py
for i in range(3):
  print(i)
 
# Output: 0
# Output: 1
# Output: 2
```

Optionally, the `range()` function can receive two arguments: `range(start, stop)`, or three arguments: `range(start, stop, step)`. Start and stop refer to the beginning and ending integers, and step refers to the incrementation. 

```py
x = range(7, 10)
for i in x:
  print(i)
 
# Output: 7
# Output: 8
# Output: 9
```
The step argument can be used in a variety of scenarios. For example, printing only even or odd numbers, or every (x) number. 

```py
for i in range(0, 10, 2):
  print(i)
  
# Output: 0
# Output: 2
# Output: 4
# Output: 6
# Output: 8

for i in range(10, 60, 10):
  print(i)
  
# Output: 10
# Output: 20
# Output: 30
# Output: 40
# Output: 50
```

range() sources: [ATBS](https://automatetheboringstuff.com/2e/chapter2/)

### 2. range() and len() functions with for loops

Call `len()` inside of `range()` when accessing multiple items in a single list, or when accessing both the index and the item at that index.


```py
character_list = ['Aragorn', 'Legolas', 'Bilbo']
for i in range(len(character_list)):
    if character_list[i] == 'Bilbo':
        print('Hobbit found')

# Output: Hobbit found
```
Run the above code without the `len()` function and you'll receive the error: `TypeError: 'list' object cannot be interpreted as an integer` because the `range()` function expects to receive an integer. Run the above code without the `len()` and `range()` functions and you'll receive the error: `TypeError: list indices must be integers or slices, not str` because 

Sources: [SO len() range()](https://stackoverflow.com/questions/19184335/is-there-a-need-for-rangelena), [SO TypeError](https://stackoverflow.com/questions/28036309/typeerror-list-object-cannot-be-interpreted-as-an-integer), [SO TypeError](https://stackoverflow.com/questions/32554527/typeerror-list-indices-must-be-integers-or-slices-not-str)

### 3. enumerate() function with for loops

The `enumerate()` function can also be used in a `for` loop instead of `range(len(list))`. The for loop can receive two variables, one for list indices and one for list items.
```py
character_list = ['Aragorn', 'Legolas', 'Bilbo']
for index, item in enumerate(character_list):
    if character_list[index] == 'Bilbo':
        print(item, 'found at index', index)

# Output: Bilbo found at index 2

```


### 4. print() function keyword arguments

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


### 5. list() and tuple() functions

Convert a list to a tuple, or vice versa, using either the `list()` or `tuple()` function. Both functions work with strings. 
```py
character_list = ['Aragorn', 'Legolas', 'Bilbo']
character_tuple = tuple(character_list)
print(character_tuple)

# Output: ('Aragorn', 'Legolas', 'Bilbo')
```
```
character = 'Aragorn'
character = list(character)
print(character)

# Output: ['A', 'r', 'a', 'g', 'o', 'r', 'n']
```


### id() function returns the memory address where the object is stored
```py
character = 'Aragorn'
print(id(character))

# Output: Memory address location

```
