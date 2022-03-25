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

# 5. import re / regex

The `re` module allows you to find patterns of text with regular expressionss, or regexes. Use `\d` to denote a digit, and add string values wherever necessary. Use a backslash in front of the string values, such as `\(` for parentheses. 

To search for a US phone number, use the pattern `\(\d\d\d\) \d\d\d-\d\d\d\d` or `(\d{3}) \d{3}-\d{4}` where `{3}` denotes how many `\d`'s to search for. Pass the regex pattern as a string value to `re.compile()` with the `r` string prefix. Note that the space after the area code is a part of the pattern.

```py
import re
us_phone_regex = re.compile(r'(\d\d\d) \d\d\d-\d\d\d\d')

```
Pass a string to the `search()` method to see if it matches the pattern stored in the regex object. `None` is returned if the pattern is not found. A match object is returned if the pattern is found. 

```py
import re
us_phone_regex = re.compile(r'\(\d\d\d\) \d\d\d-\d\d\d\d')
num_search = us_phone_regex.search('(555) 555-1234')

print('Phone is a valid US number:', num_search.group())

# Output: Phone is a valid US number: (555) 555-1234
```

In the above example, `num_search` is the variable where the match object is stored. Calling the variable on the `group()` method returns the pattern match.
