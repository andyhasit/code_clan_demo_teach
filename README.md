# Arrays

(I'll give this talk in Python, where arrays are called lists)

### objectives

1. Describe why arrays exist
2. Demonstrate creating an array
3. Demonstrate accessing an element from an array
4. Demonstrate calling array methods

## Why do we have lists

We looked at saving things to variables:

```python
a = 27
b = 89
...
```

And how these can be used for:

1. Storing values
2. Passing those values to other places, like functions

For example:

```python
a = 27
b = 89

add_two_numbers(a, b)
```

But what if we have n number of values?

```python
a = 27
b = 89
c = 46
...panic

add_loads_of_numbers(a, b, c.....help!)
```


Creating a variable for each value is not sustainable.

# Lists to the rescue

Lists allow us to store multiple values a one variable:

```python
my_values = [27, 89, 46]
```

Which can then be passed around like any other variable:

```python    
my_values = [27, 89, 46] 
add_loads_of_numbers(my_values)

// where add_loads_of_numbers looks something like this:

def add_loads_of_numbers(a_list_of_numbers):
    //do stuff..
    ... 
```

# What can you do with lists?

1. Access items
2. Add/Remove/Replace items
3. Iterate (and therefore search, filter or extract sub lists)

# Accessing

You access an element inside a list by specifying it's postion:

```python
my_values = [27, 89, 46]

// this will print the element at position 0 (i.e. 27)
print my_values[0] 

// this will print the element at position 2 (i.e. 46)
print my_values[2]

// this will throw an error
print my_values[5]
```

You can save the extracted element to a variable:

```python
a = my_values[0] 
```

Pass it directly to functions:

```python
add_tow_numbers(my_values[0], my_values[1])
```

Or use it directly, e.g. if the element is a string, we could do this:

```python
words = ['code', 'clan']
words[1].upper() 
```


# Visualising it:

As we saw before, variables are like boxes, each has a label (a, b, x, y...), and contains a value (5, 24, "potato" ...) which you can use, or overwrite.

A list is also a box, with a label, but when you look inside you are presented with a row of smaller boxes, all numbered, starting at 0 and going as far as there are elements in the list.

These smaller boxes also contain values, but they don't have their own labels. To reach the values inside them, you need to give the name of the outer box (i.e. the list) and the number of the inner box (which we call its index):

```python
my_values[1]
```

These two bits of information allow you to read the value of an element:

```python
my_values = [27, 89, 46]
a = my_values[1]
print a
>>> 89
```

And overwrite the value of an element:

```python
my_values = [27, 89, 46]
my_values[1] = 42
print my_values
>>> [27, 42, 46] 
```

# Adding items

There are three principal methods for adding.

The one you will use most often is **append**, which adds a new element to the end of the list:

```python
words = ['code', 'clan']
words.append('rocks')

>>> ['code', 'clan', 'rocks']
```

If you want to insert the element at a different position, use **insert**:
```python
words = ['code', 'clan']
words.insert(1, 'rocks')

>>> ['code', 'rocks', 'clan']
```

This pushes the other elements up.

# Removing

```python
words = ['code', 'clan']
del words[0]

>>> ['code']
```

# Iterating

The **for** expression loops over the list, executing the nested chunk of code on each element.

which will be available as the temporary variable

```python
words = ['code', 'clan']
for x in words:
    print x.upper()

>>> 'CODE'
>>> 'CLAN'
```


# Naming

Giving variables good descriptive names is your first line of defence against bugs (remember, bugs come from your own oversights, so you need to do what you can to minimize the chance of you having any).

Lists store multiple elements so it follows that they should have plural names describing the type of element they contain. You will likely encounter this.

1. people
2. files
3. data_readings

But these are rather generic and ambiguous, which will cause problems if you end up with multiples lists for those types of item in your program, or if there is ambiguity over what those mean, so try to be as specific as possible:

1. people_in_course
2. survey_respondents
2. files_to_process
3. files_with_errors

On no account should you ever use the single letter **l** for a list (or any other variable). In many fonts  **l** is indistinguishable from a **1** an **|** or an **I**.

# Limitations

Lists store their elements by sequential index (starting at 0) and that is the only way you can directly retrieve elements.
 
Make sure you understand this.