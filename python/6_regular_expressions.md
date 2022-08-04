# 6. import re / regex

The `re` module allows you to find patterns of text with regular expressions, or regexes. Pass the regex pattern as a string value to `re.compile()` function with the `r` string prefix. This function returns a regular expression object. 

Use `\d` to denote a digit, and add string values wherever necessary. Use a backslash in front of the string values, such as `\(` for parentheses. If you don't use a backslash on the parentheses, they will perform a specific function, which we'll cover later.

To search for a US phone number, use the pattern `\(\d\d\d\) \d\d\d-\d\d\d\d` or `(\d{3}) \d{3}-\d{4}` where `{3}` denotes how many `\d`'s to search for. Note that the space after the area code is a part of the pattern.
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
In the above example, `num_search` is the variable where the match object is stored. Match objects have a specific method called `group()`. Calling the match object variable on the `group()` method returns the pattern match.


### 6.1 groups within regex objects

`\(` or `\)` allow the parentheses to be part of the string. But parentheses can be used without `\` to create groups within the regex. 

Using the code sample from above, we'll separate the phone number into two groups: the area code, and the last seven digits. Since the backslashes denote the parenthese as part of the string, all we need to do is surround each group with a new set of parentheses and leave out the backslash. So the area code from before looks like this: `\(\d\d\d\)`. To separate it into a group, we'll surround it with parentheses: `(\(\d\d\d\))`. Then we'll surround the last seven digits with parentheses: `(\d\d\d-\d\d\d\d)`. The final regex will look like this: `(\(\d\d\d\)) (\d\d\d-\d\d\d\d)`. Or, as mentioned previously, to avoid typing `d` over and over again, we can use a number inside curly braces to denote how many digits to search for: `(\(\d\{3})) (\d{3}-\d{4})`.

To view the match object by group, we call the object using the `group()` method. Passing no argument or `0` into the `group()` method returns the entire match.

```py
import re

us_phone_regex = re.compile(r'(\(\d\d\d\)) (\d\d\d-\d\d\d\d)')
num_search = us_phone_regex.search('(555) 555-1234')
x = num_search.group()
y = num_search.group(0)
print(x)
print(y)

# Output: Phone is a valid US number: (555) 555-1234
# Output: Phone is a valid US number: (555) 555-1234
```

As shown above, the output of `group()` and `group(0)` are the same. Passing `1` into `group(1)` will return the first group only. `2` will return the second group.

```py
import re

us_phone_regex = re.compile(r'(\(\d\d\d\)) (\d\d\d-\d\d\d\d)')
num_search = us_phone_regex.search('(555) 555-1234')
x = num_search.group(1)
y = num_search.group(2)
print(x)
print(y)

# Output: (555) 
# Output: 555-1234
```

Using `groups()` in the plural form prints a tuple of all groups stored in the match object. 

```py
import re

us_phone_regex = re.compile(r'(\(\d\d\d\)) (\d\d\d-\d\d\d\d)')
num_search = us_phone_regex.search('(555) 555-1234')
x = num_search.groups()
print(x)

# Output: ('(555)', '555-1234')

```

### 6.2 Multiple assignment with regex groups

Use the multiple assignment trick to assign the groups to variables

```py
import re

us_phone_regex = re.compile(r'(\(\d\d\d\)) (\d\d\d-\d\d\d\d)')
num_search = us_phone_regex.search('(555) 555-1234')
area_code, suffix = num_search.groups()
print(area_code)
print(suffix)

# Output: '(555)'
# Output: '555-1234'

```

### 6.3 Pipe character with regex groups

The pipe `|` operator works similarly to a logical `or` operator. Using `|` in regular expressions tells the interpreter to return the first occurence of any string in the regular expression. In the following code, we'll create a regex to search for a US area code in two formats: `'555'` or `'(555)'`. Separating the two formats with the `|` operator will return the first occurence of either. Recall that using `\d{3}` tells the interpreter to use `\d` three times. 

```py
import re

us_area_code = re.compile(r'(\(\d{3}\))|(\d{3})')
area_code_mo = us_area_code.search('(555) 555-5555')
x = area_code_mo.group()
print(x)

# Output: (555)
```
The following section is from [Automate the Boring Stuff with Python CH7:](https://automatetheboringstuff.com/2e/chapter7/)

> You can also use the pipe to match one of several patterns as part of your regex. For example, say you wanted to match any of the strings 'Batman', > 'Batmobile', 'Batcopter', and 'Batbat'. Since all these strings start with Bat, it would be nice if you could specify that prefix only once. This can be > done with parentheses. Enter the following into the interactive shell:
> ```py
> batRegex = re.compile(r'Bat(man|mobile|copter|bat)')
> mo = batRegex.search('Batmobile lost a wheel')
> mo.group()
> # Output: Batmobile
> mo.group(1)
> # Output mobile
> ```

In the above text, 'Bat' is used almost as a prefix to the group `(man|mobile|copter|bat)`. The same method can be used as a suffix. Next we'll create a regex that searches for an entire US phone number, but we'll group the area codes first, and use the rest of the phone number as a suffix. The format will be like this: `'((555)|555) 555-5555'`. Two area code formats are grouped together: `(555)` and `555` because they're contained within parentheses and separated by the pipe operator. The second part of the phone number, ` 555-5555`, is used almost as a suffix. The interpreter will search for that exact string. For readability, I'll write out the regex in long form instead of using `\d{3}`

```py
import re

us_phone_number = re.compile(r'(\(\d\d\d\)|\d\d\d) \d\d\d-\d\d\d\d')
number_mo = us_phone_number.search('(555) 555-5555')
x = number_mo.group()
print(x)

# Output: (555) 555-5555

```
### 6.4 Optional matching with the regex question mark

Previously, the code contains a space between the area code and the rest of the phone number. Not all phone numbers contain a space at that position; sometimes numbers are written as `(555)555-5555`. The space can be made optional by using parentheses with a question mark at the end and placing a single space in the middle: `( )?`. 

```py
import re

us_phone_number = re.compile(r'(\(\d\d\d\)|\d\d\d)( )?\d\d\d-\d\d\d\d')
number_mo = us_phone_number.search('(555)555-5555')
x = number_mo.group()
print(x)

# Output: (555)555-5555
```
### 6.5 asterisk and plus sign with regex groups

The `*` symbol before a group matches 0 or more of any string designated in that group. The `+` sign matches 1 or more of any string designated within that group.

### 6.6 Use braces in regex to set a range

We previously covered using braces to designate how many times to search for a given string. `\d{3}` searches for three digits. The braces can also be used to set a range. `\d{1,10}` will return the first occurence of any string within that range.

```py
import re

number = re.compile(r'\d{1,10}')
number_mo = number.search('5555555')
x = number_mo.group()
print(x)

# Output: 555

```
One of the two numbers can be left out. `{,9}` means 0-9, and `{9,}` means start at nine and match infinitely. 

### 6.7 regex greedy vs. non-greedy

Python is greedy be default. In other words, it always matches the longest possible string within a range. To return the shortest possible string instead, use the `?`. Note that the question mark in this context is different than using it to designate an optional string. 

```py
import re

number = re.compile(r'\d{1,10}?')
number_mo = number.search('5555555')
x = number_mo.group()
print(x)

# Output: 5
```

### 6.8 The findall() method with regex

While the `search()` method returns the first occurence of the given string in the regex, the `findall()` method returns a list with every matching string (as long as there are no groups). If there is no match, Python returns an empty string. 

```py
import re

us_phone_number = re.compile(r'\d\d\d-\d\d\d-\d\d\d\d')
x = us_phone_number.findall('555-555-5555')
print(x)

# Output: ['555-555-5555']
```

### 6.9 Regex findall() with groups

If the regex contains either zero or one group, findall() will return a list of string matches. If the regex contains two or more groups, then findall() will return a list of tuples. Inside each tuple are the string matches for each group in the regex. 

The following comes from [Automate the Boring Stuff with Python CH 7:](https://automatetheboringstuff.com/2e/chapter7/)
> ```py
> `phoneNumRegex = re.compile(r'(\d\d\d)-(\d\d\d)-(\d\d\d\d)') # has groups`
> `phoneNumRegex.findall('Cell: 415-555-9999 Work: 212-555-0000')`
> # Output: [('415', '555', '9999'), ('212', '555', '0000')]
> ```
> To summarize what the findall() method returns, remember the following:
> 
> When called on a regex with no groups, such as \d\d\d-\d\d\d-\d\d\d\d, the method findall() returns a list of string matches, such as ['415-555-9999', '212-555-0000'].
> When called on a regex that has groups, such as (\d\d\d)-(\d\d\d)-(\d\d\d\d), the method findall() returns a list of tuples of strings (one string for each group), such as [('415', '555', '9999'), ('212', '555', '0000')].

### 6.10 Regex character classes

The following table comes from [Automate the Boring Stuff with Python CH 7:](https://automatetheboringstuff.com/2e/chapter7/)

> In the earlier phone number regex example, you learned that \d could stand for any numeric digit. That is, \d is shorthand for the regular expression (0|1|2|3|4|5|6|7|8|9).
> 
> \d	Any numeric digit from 0 to 9.
> 
> \D	Any character that is not a numeric digit from 0 to 9.
> 
> \w	Any letter, numeric digit, or the underscore character. (Think of this as matching “word” characters.)
> 
> \W	Any character that is not a letter, numeric digit, or the underscore character.
> 
> \s	Any space, tab, or newline character. (Think of this as matching “space” characters.)
> 
> \S	Any character that is not a space, tab, or newline.

```py
import re

test_regex = re.compile(r'\d+\s+\w+')
x = test_regex.findall('7 Samurai')
print(x)

# Output: ['7 Samurai', '7 samurai']
```

### 6.11 Regex custom classes

Python allows you to create custom classes that function similarly to character classes. For example, there is no class for letters only. But ranges can be set for letters to create a custom class: `[a-zA-z]`. When using regular expression characters inside brackets, the backslash is not needed. For example, `[a-zA-z?!.:;]` searches for all letters plus the punctuation signs. 

Using the caret symbol after the opening bracket creates a negative character class. `[^a-zA-z]` returns all values except letters. Note that by default, your custom character class will only match a single occurence of the given character set, just like a standard character class.  

### 6.12 Beginning and ending symbols with regex

Use the caret symbol at the beginning of a regex to return a match object that begins with the designated string.

```py
import re

test_regex = re.compile('^\d')
test_mo = test_regex.search('7 Samurai')
x = test_mo.group()
print(x)

# Output: 7
```
Use the dollar sign at the end of a regex to return a match object that ends with the designated string.

```py
import re

test_regex = re.compile(r'\d$')
test_mo = test_regex.search('Lucky Number 7')
x = test_mo.group()
print(x)

# Output: 7
```
Using both `^` and `$` tells the compiler to match the entire pattern. Example: `re.compile(r'^\d+$')` will only match a string with a number of any length at the beginning and end. The number cannot contain anything else but a number because it's been surrounded by the caret and dollar sign. 

### 6.13 Wildcard symbol

The period is the wildcard symbol in regexes. It returns any character at that desigation. 

```py
import re

test_regex = re.compile(r'xy.')
test_mo = test_regex.search('xyz')
x = test_mo.group()
print(x)

# Output: xyz
```

### 6.14 Dot-star and re.DOTALL

The dot-star matches everything except newline characters.

```py
import re

test_regex = re.compile(r'abc.*')
test_mo = test_regex.search('abc_xyz\nabc')
x = test_mo.group()
print(x)

# Output: abc_xyz
```

Using `re.DOTALL` as an optional argument in `re.compile()` forces the dot-star to match all characters.


```py
import re

test_regex = re.compile(r'abc.*', re.DOTALL)
test_mo = test_regex.search('abc_xyz\nabc')
x = test_mo.group()
print(x)

# Output: abc_xyz
# Output: abc
```

### 6.15 re.IGNORECASE and re.I

Pass `re.IGNORECASE` or `re.I` as optional arguments to `re.compile()` to ignore case sensitivity. 

```py
import re

test_regex = re.compile(r'abc', re.I)
test_mo = test_regex.search('Abc')
x = test_mo.group()
print(x)

# Output: abc_xyz
```

### 6.16 regex and the sub() method

Use the `sub()` method to replace the matched regex with the given string. The `sub()` method replaces all matches, not just the first occurence. The first string is what replaces the match, and the second string is the item to search through.

```py
import re

test_regex = re.compile(r'abc')
test_replace = test_regex.sub('ABC', 'abc')
print(test_replace)

# Output: ABC
```

If groups exist within the regex, use `\1`, `\2`, and so on, to replace the regex with the text from the given group. The r-string is required before the group number.

```py
import re

test_regex = re.compile(r'abc(\w*)')
test_replace = test_regex.sub(r'\1', 'abcdef')
print(test_replace)

# Output: def
```

### 6.17 re.VERBOSE and multi-line formatting

Complex regexes can be easier to read when broken into multiple lines. With a combination of multiline strings, newlines, spaces, and re.VERBOSE, the regex can be made much more readable. Consider this sample code from [ATBS CH7:](https://automatetheboringstuff.com/2e/chapter7/)

```py
phoneRegex = re.compile(r'''(
    (\d{3}|\(\d{3}\))?            # area code
    (\s|-|\.)?                    # separator
    \d{3}                         # first 3 digits
    (\s|-|\.)                     # separator
    \d{4}                         # last 4 digits
    (\s*(ext|x|ext.)\s*\d{2,5})?  # extension
    )''', re.VERBOSE)
```
To use multiple optional arguments at the end of a regex, separate them with the pipe character: `re.compile('...'. re.VERBOSE | re.DOTALL | re.I)`

Sources: [Automate the Boring Stuff with Python CH 7](https://automatetheboringstuff.com/2e/chapter7/), [Python Docs](https://docs.python.org/3/library/re.html), [Python Docs HOWTO](https://docs.python.org/3/howto/regex.html)

### 6.18 Using variables inside regular expressions

A variable containing a string value can be used inside of a regular expression. Simply surround the variable with the `+` operator. The regular expression will evaluate to a concatenated version of the string.

```py
import re
x = 'Legolas'
y = 'Gimli'
z = 'Legolas eventually became friends with Gimli'
regex = re.compile(r'['+x+']*.*['+y+']*')
mo = regex.search(z)
print(mo.group())

# Output: Legolas eventually became friends with Gimli

```

The same expression also works without the brackets 
```py
x = 'Legolas'
y = 'Gimli'
z = 'Legolas eventually became friends with Gimli'
regex = re.compile(r'('+x+').*('+y+')')
mo = regex.search(z)
print(mo.group())

# Output: Legolas eventually became friends with Gimli
```
Source: [github gist](https://gist.github.com/johnmccormick/0b74fd6c544b47a8da3d812e80197ded)
