### String interpolation and f-strings 

Using the `%s` operator within a string to designate where to add new strings. 

```py
var1 = 'bow'
var2 = 'axe'
string1 = 'Legolas used a %s, but Gimli preferred an %s.' % (var1, var2)
print(string1)

# Output: Legolas used a bow, but Gimli preferred an axe.

```
f-strings are similar, except the expression is placed inside of the string. Place `f` in front of the string to edit, and place the variables between `{}`.

```py
var1 = 'bow'
var2 = 'axe'
string1 = f'Legolas used a {var1}, but Gimli preferred an {var2}." 
print(string1)

# Output: Legolas used a bow, but Gimli preferred an axe.
```
