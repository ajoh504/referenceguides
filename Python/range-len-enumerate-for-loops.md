### range() function with for loops

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

### 2.2. range() and len() functions with for loops

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

### 2.3. enumerate() function with for loops

The `enumerate()` function can also be used in a `for` loop instead of `range(len(list))`. The for loop can receive two variables, one for list indices and one for list items.
```py
character_list = ['Aragorn', 'Legolas', 'Bilbo']
for index, item in enumerate(character_list):
    if character_list[index] == 'Bilbo':
        print(item, 'found at index', index)

# Output: Bilbo found at index 2

```
