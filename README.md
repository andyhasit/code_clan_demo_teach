# Lists

(I'll give this talk in Python, where arrays are called lists)

## Topics:

1. What lists are and why we need them
2. How to use lists
3. Naming them
4. When to use lists and when not to
5. Common gotchas

## Why do we need lists

We looked at saving things to variables and how these can be used for:

1. Storing values
2. Passing those values to other places, like functions

For example:

```python
a = 27
b = 89

print_highest_number(a, b)
```

But what if we have **n** number of values?

```python
a = 27
b = 89
c = 46
...panic

print_highest_number(a, b, c.....help!)
```

Creating a variable for each value is not sustainable.

## Lists to the rescue

Lists allow us to store multiple values a one variable:

```python
my_values = [27, 89, 46]
```

Which can then be passed around like any other variable:

```python    
my_values = [27, 89, 46] 
print_highest_number(my_values)

# where add_loads_of_numbers looks something like this:

def print_highest_number(a_list_of_numbers):
    # do stuff..
    ... 
```

## What can you do with lists?

1. Access items
2. Add/Remove/Replace items
3. Iterate (and therefore search, filter or extract sub lists)

## Accessing

You access an element inside a list by specifying it's postion:

```python
my_values = [27, 89, 46]

# this will print the element at position 0 (i.e. 27)
print my_values[0] 

# this will print the element at position 2 (i.e. 46)
print my_values[2]

# this will throw an error
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


#### Visualising it:

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

## Adding items

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

## Removing items

```python
words = ['code', 'clan']
del words[0]

>>> ['code']
```

## Iterating

One of the main reasons for having lists is so you can do something with/to each element in it.

You do this using the **for i in list** expression, which simply executes the nested chunk of code on each element.

The elements will be accessible as the variable **i** (or whatever you call it) inside the nested block:

```python
for i in [1, 2, 3]:
    print i * 3
    
>>> 2
>>> 4
>>> 6

words = ['code', 'clan']
for x in words:
    print x.upper()

>>> 'CODE'
>>> 'CLAN'
```

## Naming

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

Equally, it helps if the iterator variable has a sensible name:

```python
words = ['code', 'clan']
for word in words:
    print word.upper()

>>> 'CODE'
>>> 'CLAN'
```

On no account should you ever use a single lower case **L** to name a list (or any other) variable. In many fonts  **l** is indistinguishable from **1**, **|** or **I**.

# When to use lists

Ask yourself:
  
  - Do I have more than one thing I want to treat the same way?
  - Will the number of those things ever possibly grow beyond two?

If the answer is yes to those, then you should use a list or other collection instead of individual variables.

Key signs that you should be using a list are duplication in your code:

```python
data_from_glasgow_survey = get_data_from_file('glasgow_data.txt')
data_from_edinburgh_survey = get_data_from_file('edinburgh_data.txt')

process_data(data_from_glasgow_survey)
process_data(data_from_edinburgh_survey)
```

And the presence of numbers in variables (or first, 2nd etc...)


```python
data_set_1 = get_data_one_way('data_set_1.txt')
data_set_2 = get_data_another_way('data_set_2.txt')

process_one_way(data_set_1)
process_another_way(data_set_2)
```

Here the duplication is less obvious and you might not yet know how to get round it (topic for another lesson) but the problem remains: what if there is a third data set?


# When not to use lists

Lists store their elements by sequential index (starting at 0) and that is the only way you can directly retrieve elements.

If you want to remember values by a certain key, then you would use a dictionary:

```python
glasgow = 598830
edinburgh = 495360

#replace with
populations = {
    'glasgow' : 598830
    'edinburgh': 495360
}
```

# Common Gotchas

Lists are objects. When you pass it to another function, you are passing a reference to the same list object. 

The function creates its own variable for the the list, but the list is the same object, and any changes made to it will impact other places you use the list:


```python
do_things_with_list(a_list):
    a_list.append(4)

my_list = [1, 2, 3]
do_things_with_list(my_list)

print my_list
>>> [1, 2, 3, 4]

   
#Is this what you expected/intended?
```

The same rationale applies to:
```python    
a = [1, 2, 3]
b = a
b.append(4)

print a
>>> [1, 2, 3, 4]

print b
>>> [1, 2, 3, 4]
```

In fact this is how Python works for all variables, including strings and numbers. It just doesn't feel that way because those are immutable types, so you think you are copying the value around.

Another common mistake is modifying the list as you iterate over it:

```python
numbers = [1, 2, 3, 6, 10, 20]
for i in numbers: 
    if i < 10:
        # This will go horribly wrong!
        del numbers[i] 
```

Do not manipulate the list you are iterating over! Create a copy instead, or think of another way.
