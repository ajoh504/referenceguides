# Built-In Methods

### 6.1 calling keys(), values(), and items() on dictionaries

The `keys()`, `values`, and `items()` methods can be used to loop through the contents of a dictionary. 

```py
Legolas = {'Race': "Elf", 'Weapon': "Bow"}
for k in Legolas.keys():
    print(k)
        
# Output: Race
# Output: Weapon

Legolas = {'Race': "Elf", 'Weapon': "Bow"}
for v in Legolas.values():
    print(v)
    
# Output: Elf
# Output: Bow

Legolas = {'Race': "Elf", 'Weapon': "Bow"}
for k, v in Legolas.items():
    print(k + ': ' + v)
    
# Output: Race: Elf
# Output: Weapon: Bow
```
Combine these methods with the `list()` or `tuple()` functions to receive a new list or tuple with a dictionary's keys, values, or both.
```py
Legolas = {'Race': "Elf", 'Weapon': "Bow"}
print(list(Legolas.keys()))

# Output: ['Race', 'Weapon']
```

Combine with the `in` or `not in` operators to see if the key or value is inside the dictionary. 
```py
Legolas = {'Race': "Elf", 'Weapon': "Bow"}
print('Sword' in Legolas.keys())

# Output: False
```
The `get()` method searches a dictionary for a given key, and takes an optional argument to return if the key is not found.
```py
Gimli = {'Race': "Dwarf", 'Weapon': "Axe"}
print(Gimli.get('Home', 'No home found'))

# Output: No home found
```
### 6.2 setdefault() with dictionaries

The `setdefault()` method adds a key and sets its default value. If the key is already stored in the dictionary, it returns the value.
```py
Shire = {
  'Location': "Middle Earth",
  'Inhabitants': "Hobbits",
}
test = Shire.setdefault('Location', "")
print(test)

# Output: Middle Earth

Shire = {
  'Location': "Middle Earth",
  'Inhabitants': "Hobbits",
}
test = Shire.setdefault('Farmland', True)
print(Shire)

# Output: {'Location': 'Middle Earth', 'Inhabitants': 'Hobbits', 'Farmland': True}
```

### 6.3 upper() and lower() methods with strings

Use the `upper()` or `lower()` methods on a string value. This returns a new string in all uppercase or all lowercase.

```py
x = 'Abc'
x = x.upper()
print(x)

x = x.lower()
print(x)

# Output: 'ABC'
# Output: 'abc'
```

Use `isupper()` or `islower()` to return a Boolean value, i.e. `True` or `False` if the string is all upper or lowercase. 

```py
x = 'ABC'
print(x.isupper())

# Output: True
```

### 6.4 startswith() and endswith() with strings

Use `startswith()` or `endswith()` to return a Boolean value, i.e. `True` or `False` if the string begins with the designated string. 

```py
x = 'ABC'
print(x.startswith('a'))

# Output: False
```
### 6.5 join() and split() with a list of strings

Pass a list of strings to the `join()` method to return a new string value, with all items in the list concatenated. Preface `join()` with a required string value. Both `join()` and `split()` can act upon the escape characters.  
```py
x = ['abc', 'def']
x = ', '.join(x)
print(x)

# Output: abc, def

```
Use `split()` to break apart a string value into list. 
```py
x = 'abc, def'
x = x.split(', ')
print(x)

# Output: ['abc', 'def']

```
### 6.6 rjust(), ljust(), and center() to justify text

Use `rjust()`, `ljust()`, or `center()` to justify text. A numeric argument is required to specify the number of spaces to justify. The character count of the string is included in this number.
```py
x = 'Flesh wound'
x = x.rjust(13)
print(x)

# Output:   Flesh wound
```
### 6.7 strip(), rstrip(), and lstrip() to remove whitespace characters

Use `strip()`, `rstrip()`, and `lstrip()` to remove whitespace characters (space, tab, and newline). `rstrip()` and `lstrip()` remove spaces from those sides respectively, and `strip()` removes spaces from both sides. 

```py
x = '          Flesh wound'
x = x.lstrip()
print(x)

# Output: Flesh wound
```
Add an optional string value to be removed instead of the whitespace. 

```py
x = 'Flesh wound'
x = x.lstrip('Flesh')
print(x)

# Output: wound
```

From [ATBS Ch 6:](https://automatetheboringstuff.com/2e/chapter6/)

> isalpha() Returns True if the string consists only of letters and isn’t blank
> 
> isalnum() Returns True if the string consists only of letters and numbers and is not blank
> 
> isdecimal() Returns True if the string consists only of numeric characters and is not blank
> 
> isspace() Returns True if the string consists only of spaces, tabs, and newlines and is not blank
> 
> istitle() Returns True if the string consists only of words that begin with an uppercase letter followed by only lowercase letters


### 6.8 index() method on iterable data types

Use the `index()` method on lists, tuples, or strings to return the index value of the given item. 

```py
list1 = ['test1', 'test2', 'test3']
print(list1.index('test1'))

# Output: 0
```

### 6.9 append(), insert(), remove(), sort(), and reverse() with lists

Use `append()` on a list to append an item to the end of the list. Both methods modify the list in place, so the return value is `None`.

```py
test = [1,2,3,4,5]
print(test.append(6))
print(test)

# Output: None
# Output: [1, 2, 3, 4, 5, 6]
```
Use `insert()` with two required arguments to insert an item at any index. The first argument is the index, the second argument is the item to be added.
```py
test = [1,2,3,4,5]
test.insert(5, 6)
print(test)

# Output: [1, 2, 3, 4, 5, 6]
```
Use `remove()` two remove an item from a list. Useful if you do not know the index of the item to be removed. Otherwise, simply use `del`.
```py
test = [1,2,3,4,5]
test.remove(5)
print(test)

# Output: [1, 2, 3, 4]
```

Use `sort()` to sort items in a list. `sort()` takes an optional keyword: `reverse=True` to sort the items in reverse order.
```py
test = [1,4,5,2,3]
test.sort(reverse=True)
print(test)

# Output: [5, 4, 3, 2, 1]
```
If using `sort` on text, uppercase is sorted first and grouped together, followed by lowercase. Use the optional keyword `key=str.lower` to treat the text as all lowercase. The text is not changed to lowercase, but only treated as such for sorting purposes. 

```py
list1 = ['mordor', 'The Shire', 'gondor']
list1.sort(key=str.lower, reverse=True)
print(list1)

# Output: ['The Shire', 'mordor', 'gondor']
```

Use the `reverse()` method to reverse the items in a list.
```py
test = [1,4,5,2,3]
test.reverse()
print(test)

# Output: [1, 2, 3, 4, 5]
```
