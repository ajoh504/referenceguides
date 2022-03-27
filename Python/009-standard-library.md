# Standard library

Python comes pre-built with a standard library, a collection of modules that can be imported into your code as needed. Import a new module using the `import` statement.

### 1. import random

Use `random.randint()` on a range of numbers to return a random number. 
```py
import random
print(random.randint(1,100))

# Output: a random integer between 1 and 100
```

Use `random.choice()` on a list to return a random item from that list. 

```py
import random
list1 = ['Mordor', 'The Shire', 'Gondor']
print(random.choice(list1))

# Output: a random item from list1
```

Use `random.shuffle()` on a list to shuffle the contents of a list. The list is modified in place. 
```py
import random
list1 = ['Mordor', 'The Shire', 'Gondor']
print(random.shuffle(list1))

# Output: list1 but rearranged randomly
```

Sources [ATBS CH2](https://automatetheboringstuff.com/2e/chapter2/). [ATBS CH4](https://automatetheboringstuff.com/2e/chapter4/)

### 2. import copy

Use `copy.copy()` to copy the contents of one variable to another. Use `copy.deepcopy()` if the contents contain lists within lists. 

