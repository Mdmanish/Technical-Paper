<!--hii-->
# Python cheat sheet

## String

In Python, Strings are arrays of bytes representing Unicode characters.

Strings in Python can be created using single quotes or double quotes or even triple quotes.

To define a multi-line string, we surround our string with tripe quotes (“””).

```python
#Program to reverse a string
gfg = "geeksforgeeks"
print(gfg[::-1])

gfg = "geeksforgeeks"
 
Reverse the strinh using reversed and join function
gfg = "".join(reversed(gfg))
```

## String slicing

To access a range of characters in the String, the method of slicing is used. Slicing in a String is done by using a Slicing operator (colon).

```python
String1 = "GeeksForGeeks"
print("Initial String: ")
print(String1)
 
# Printing 3rd to 12th character
print("\nSlicing characters from 3-12: ")
print(String1[3:12])

# output
#Slicing characters from 3-12: 
#ksForGeek
```

```python

s.capitalize()      Capitalize s # 'hello' => 'Hello'
s.lower()       Lowercase s # 'HELLO' => 'hello'
s.swapcase()    Swap cases of all characters in s # 'Hello' => "hELLO"
s.title()       Titlecase s # 'hello world' => 'Hello World'
s.upper()       Uppercase s # 'hello' => 'HELLO' 

s2 in s     # Return true if s contains s2
s + s2      # Concat s and s2
len(s)      # Length of s
min(s)      # Smallest character of s
max(s)      # Largest character of s 

s2 not in s     # Return true if s does not contain s2
s * integer     # Return integer copies of s concatenated # 'hello' => 'hellohellohello'
s[index]        # Character at index of s
s[i:j:k]        # Slice of s from i to j with step k
s.count(s2)     # Count of s2 in s 

s.center(width)     #Center s with blank padding of width # 'hi' => ' hi '
s.isspace()         #Return true if s only contains whitespace characters
s.ljust(width)      #Left justifiy s with total size of width # 'hello' => 'hello '
s.rjust(width)      #Right justify s with total size of width # 'hello' => ' hello'
s.strip()           #Remove leading and trailing whitespace from s # ' hello ' => 'hello' 

s.index(s2, i, j)       #Index of first occurrence of s2 in s after index i and before index j
s.find(s2)      #Find and return lowest index of s2 in s
s.index(s2)     #Return lowest index of s2 in s (but raise ValueError if not found)
s.replace(s2, s3)       #Replace s2 with s3 in s
s.replace(s2, s3, count)        #Replace s2 with s3 in s at most count times
s.rfind(s2)     #Return highest index of s2 in s
s.rindex(s2)        #Return highest index of s2 in s (raise ValueError if not found)

s.casefold()    # Casefold s (aggressive lowercasing for caseless matching) # 'ßorat' => 'ssorat'
s.islower()     # Return true if s is lowercase
s.istitle()     # Return true if s is titlecased # 'Hello World' => true
s.isupper()     # Return true if s is uppercase 

s.endswith(s2)      # Return true if s ends with s2
s.isalnum()     # Return true if s is alphanumeric
s.isalpha()     # Return true if s is alphabetic
s.isdecimal()       # Return true if s is decimal
s.isnumeric()       # Return true if s is numeric
s.startswith(s2)        # Return true is s starts with s2 


s.join('123')       # Return s joined by iterable '123' # 'hello' => '1hello2hello3'
s.partition(sep)        # Partition string at sep and return 3-tuple with part before, the sep itself, and part after # 'hello' => ('he', 'l', 'lo')
s.rpartition(sep)       # Partition string at last occurrence of sep, return 3-tuple with part before, the sep, and part after # 'hello' => ('hel', 'l', 'o')
s.rsplit(sep, maxsplit)     # Return list of s split by sep with rightmost maxsplits performed
s.split(sep, maxsplit)      # Return list of s split by sep with leftmost maxsplits performed
s.splitlines()      # Return a list of lines in s # 'hello\nworld' => ['hello', 'world'] 


s[i:j]      # Slice of s from i to j
s.endswith((s1, s2, s3))        # Return true if s ends with any of string tuple s1, s2, and s3
s.isdigit()     # Return true if s is digit
s.isidentifier()        # Return true if s is a valid identifier
s.isprintable()     # Return true is s is printable 


s.center(width, pad)        # Center s with padding pad of width # 'hi' => 'padpadhipadpad'
s.expandtabs(integer)       # Replace all tabs with spaces of tabsize integer # 'hello\tworld' => 'hello world'
s.lstrip()      # Remove leading whitespace from s # ' hello ' => 'hello '
s.rstrip()      # Remove trailing whitespace from s # ' hello ' => ' hello'
s.zfill(width)      # Left fill s with ASCII '0' digits with total length width # '42' => '00042' 
```

## Lists

```python

numbers = [1, 2, 3, 4, 5]
numbers[0] # returns the first item
numbers[1] # returns the second item
numbers[-1] # returns the first item from the end
numbers[-2] # returns the second item from the end
numbers.append(6) # adds 6 to the end
numbers.insert(0, 6) # adds 6 at index position of 0
numbers.remove(6) # removes 6
numbers.pop() # removes the last item
numbers.clear() # removes all the items
numbers.index(8) # returns the index of first occurrence of 8
numbers.sort() # sorts the list
numbers.reverse() # reverses the list
numbers.copy() # returns a copy of the list

```

## Tuples

They are like read-only lists. We use them to store a list of items. But once we define a tuple, we cannot add or remove items or change the existing items.
coordinates = (1, 2, 3)
We can unpack a list or a tuple into separate variables:
x, y, z = coordinates

## Dictionaries

```python

values()

The values() method gets the values of the dictionary:

pet = {'color': 'red', 'age': 42}
for value in pet.values():
    print(value)
# red
# 42

key()

The keys() method gets the keys of the dictionary

pet = {'color': 'red', 'age': 42}
for key in pet.keys():
    print(key)

# color
# age

There is no need to use .keys() since by default you will loop through keys:

pet = {'color': 'red', 'age': 42}
for key in pet:
    print(key)

# color
# age

items()

The items() method gets the items of a dictionary and return them as a Tuple:

pet = {'color': 'red', 'age': 42}
for item in pet.items():
    print(item)

# ('color', 'red')
# ('age', 42)

Using the keys(), values(), and items() methods, a for loop can iterate over the keys, values, or key-value pairs in a dictionary, respectively.

pet = {'color': 'red', 'age': 42}
for key, value in pet.items():
    print(f'Key: {key} Value: {value}')

# Key: color Value: red
# Key: age Value: 42

get()

# The get() method returns the value of an item with by using the key. If the key doesn’t exist, it returns None:

wife = {'name': 'Rose', 'age': 33}
f'My wife name is {wife.get("name")}'
# 'My wife name is Rose'
f'She is {wife.get("age")} years old.'
# 'She is 33 years old.'
f'She is deeply in love with {wife.get("husband")}'
# 'She is deeply in love with None'


You can also change the default None value for other of your choice:

wife = {'name': 'Rose', 'age': 33}
f'She is deeply in love with {wife.get("husband", "lover")}'
# 'She is deeply in love with lover'


Adding items with setdefault()

It’s possible to add an item to a dictionary in this way:

wife = {'name': 'Rose', 'age': 33}
if 'has_hair' not in wife:
    wife['has_hair'] = True


Using the setdefault method we can make the same code more short:

wife = {'name': 'Rose', 'age': 33}
wife.setdefault('has_hair', True)
wife
# {'name': 'Rose', 'age': 33, 'has_hair': True}


Removing Items
pop()
The pop() method removes and return an item based on a given key.

wife = {'name': 'Rose', 'age': 33, 'hair': 'brown'}
wife.pop('age')
# 33
wife
# {'name': 'Rose', 'hair': 'brown'}


popitem()

The popitem() method remove the last item in a dictionary and returns it.

wife = {'name': 'Rose', 'age': 33, 'hair': 'brown'}
wife.popitem()
# ('hair', 'brown')
wife
# {'name': 'Rose', 'age': 33}


del()

The del() method removes an item based on a given key.

wife = {'name': 'Rose', 'age': 33, 'hair': 'brown'}
del wife['age']
wife
# {'name': 'Rose', 'hair': 'brown'}


clear()

Theclear() method removes all the items in a dictionary.

wife = {'name': 'Rose', 'age': 33, 'hair': 'brown'}
wife.clear()
wife
# {}


Checking keys in a Dictionary

person = {'name': 'Rose', 'age': 33}
'name' in person.keys()
# True
'height' in person.keys()
# False
'skin' in person # You can omit keys()
# False


Checking values in a Dictionary

person = {'name': 'Rose', 'age': 33}
'Rose' in person.values()
# True
33 in person.values()
# True


Pretty Printing

import pprint
wife = {'name': 'Rose', 'age': 33, 'has_hair': True, 'hair_color': 'brown', 'height': 1.6, 'eye_color': 'brown'}
pprint.pprint(wife)

# {'age': 33,
#  'eye_color': 'brown',
#  'hair_color': 'brown',
#  'has_hair': True,
#  'height': 1.6,
#  'name': 'Rose'}


Merge two dictionaries

dict_a = {'a': 1, 'b': 2}
dict_b = {'b': 3, 'c': 4}
dict_c = {**dict_a, **dict_b}
dict_c
# {'a': 1, 'b': 3, 'c': 4}


```

## Functions

```python
# We use functions to break up our code into small chunks. These chunks are easier to read, understand and maintain. If there are bugs, it’s easier to find bugs in a small chunk than the entire program. We can also re-use these chunks.

def greet_user(name):
    print(f”Hi {name}”)
greet_user(“John”)

# Parameters are placeholders for the data we can pass to functions. Arguments are the actual values we pass.
# We have two types of arguments:
# • Positional arguments: their position (order) matters
# • Keyword arguments: position doesn’t matter - we prefix them with the parameter name.
# Two positional arguments
greet_user(“John”, “Smith”)

# Keyword arguments
# calculate_total(order=50, shipping=5, tax=0.1)
# Our functions can return values. If we don’t use the return statement, by default None is returned. None is an object that represents the absence of a value.
def square(number):
    return number * number
result = square(2)
print(result) # prints 4

```

## Exceptions

```python

# Exceptions are errors that crash our programs. They often happen because of bad input or programming errors. It’s our job to anticipate and handle these exceptions to prevent our programs from cashing.

try:
    age = int(input(‘Age: ‘))
    income = 20000
    risk = income / age
    print(age)
except ValueError:
    print('Not a valid number')
except ZeroDivisionError:
    print('Age cannot be 0')

```

## Classes

```python
# We use classes to define new types.
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    def move(self):
        print(“move”)

# When a function is part of a class, we refer to it as a method.
# Classes define templates or blueprints for creating objects. An object is an instance of a class. Every time we create a new instance, that instance follows the structure we define using the class.

point1 = Point(10, 5)
point2 = Point(2, 4)

# __init__ is a special method called constructor. It gets called at the time of creating new objects. We use it to initialize our objects

```

## Inheritance

Inheritance is a technique to remove code duplication. We can create a base class to define the common methods and then have other classes inherit these methods.

```python
class Mammal:
    def walk(self):
        print(“walk”)
        
class Dog(Mammal):
    def bark(self):
        print(“bark”)
dog = Dog()
dog.walk() # inherited from Mammal
dog.bark() # defined in Dog

```
