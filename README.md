# Phase 3 Study Guide

The intention of this guide is to give you questions that may (or may not) be on the Phase 3 assessment.

Additionally, as part of the assessment you'll be asked to debug and explain small portions of code related to questions in the programmatic python and object oriented programming sections.

## Pipenv

- What is a virtual environment? Why do we use them?
    - A digital sandbox to play with things and not mess up the rest of your computer
    - gives access to specific packages that get downloaded with `pipenv install`
- What is `pipenv`? What is the difference between `pipenv` and `pip`?
    - `pipenv` is the virtual environment we use to do things without affecting the rest of the computer
    - `pip` affects our entire computer's python environment
    - `pip` is the thing that allows us to install packages globally across the computer
- What does your `pipfile` contain and how does it relate to `pipenv`?
    - dependencies in the `pipfile` show what packages get installed with `pipenv install`
    - `Pipefile` tracks information for the virtual environment including dependencies
- How would you add a new package using `pipenv`?
    - `pipenv install flask`
    - `pipenv shell` --> puts you into the virtual environment

## Imports

- How do you import modules in Python?
    - `import time`
    - `time.date`
- How do you import code from a package in Python?
    - `from time import date` --> this will only import `date`
- What is the syntax for a relative import path in Python?
    - `from lib.models import User`

## Programmatic Python

- What is a Python `list`? What are some common methods used by a `list`?
    - basically it's an array
    - lists are ordered with an implicit index starting at 0 and each index is unique
    - can contain any data type
    - lists are mutable (they can be changed)
    - able to iterate using `for` loops or `while` loops or other things
    - list comprehension --> `[ puppy.name for puppy in Puppy.all_puppies ]`
        - returns a new list like a .map
    - list comprehension for filters --> `[ puppy for puppy in Puppy.all_puppies if puppy.name == "Maxi"]`
        - returns a filtered list like a .filter
- What is a `for` loop in Python? What is a `while` loop in Python?

```python
all_puppies = ["Maxi", "Maxi 2", "Maxi the Third", "Long Live Maxi"]

for puppy in all_puppies:
    print(puppy)

index = 0
while index < len(all_puppies):
    puppy = all_puppies[index]
    print(puppy)
    index += 1
```

- What is a Python `dict`? How do we access data in a `dict`?
    - a dictionary is similar to a list but instead of implicit indexes it has key/value pairs
    - dictionaries are mutable
    - `some_dictionary['some_key']` # accessing a value for a key
    - `some_dictionary['new_key_name'] = "something new!` # creating a new key / value
    - `some_dictionary['some_key'] = "more new stuff!` # assigning a new value to an existing key
    - keys need to be unique
    - strings and numbers are considered unique from each other when it comes to keys bc they're different data types
- What is the syntax for conditional (`if`/`else`) statements in Python?

```python
if len(something > 3):
    return "I am greater than 2"
elif len(something) > 2:
    return "I am greater than 3"
else:
    return "I am pretty short"
```

- How do you declare functions in Python? What does it mean to say functions are first class citizens?
    - can take in arguments
    - able to perform a list of commands when called
    - able to return an output although the perform isn't always necessary especially if it's just performing some sort of other task

```python
def some_name(arg1, arg2, arg3):
    return arg1 + arg2 + arg3
```

    - a function can be saved to a variable and used like any other object in python
    - essentially a function is just another piece of data

```python
list_of_fns = [function_one, function_two, function_three]
list_of_fns[1]() # the same as doing `function_two()`
```

## Object Oriented Programming

- What is a `class`? What is the difference between a `class` and an `instance`?
    - A class is code that creates behaviors for data
    - Classes can create data and attributes
    - An instance is a unit inside the class
    - Example: PeanutButter class and "Creamy JIF Peanut Butter" would be an instance
    - Methods get defined by the class and are usually called by the instance
    - class it the code that creates behavior for instances
    - an instance is created by the class
    - the class is the template and the instance is a unique example of that template

```python
class PeanutButter:

    # instance method
    def describe(self): # self is the instance
        return "I am peanut butter or whatevs"

jif = PeanutButter()
jif.name = "Creamy JIF Peanut Butter"
jif.describe()
```

- What does it mean to instantiate an `instance`? What magic method gets called when you instantiate a new `instance`?
    - essentially we are calling on the class to create a new instance
    - `__init__` gets called whenever we create a new instance
    - generally the `__init__` is used to attach attributes when building the new instance
- What is `self` within an `instance` method?
    - the first argument in instance methods
    - `self` refers to the instance itself
    - `jif.describe()` then self would be `jif`
- What is a `class` method? What is a `class` variable?

```python
class PeanutButter:

    # instance method
    def describe(self): # self is the instance
        return "I am peanut butter or whatevs"

    # class method
    @classmethod
    def define(cls): # cls is the class itself (PeanutButter)
        return "Peanut butter is a substance created by grinded peanuts into a butter blah blah blah..."

PeanutButter.define() #>>> "Peanut butter is a substance created by grinded peanuts into a butter blah blah blah..."
```

- What is a decorator?
    - a template for methods & functions
    - the decorator alters or changes another function
    - for example we could create a decorator that alters a function to run 3 times instead of once
    - decorators need to be defined or pre-defined and always start with the `@` on top of another function
- What is an attribute?
    - an attribute is a variable attached to an instance (or class in the case of class attributes)
    - instance attribute: `jif.creaminess = 10` --> the attribute is `creaminess` and its value is `10`
    - each instance tracks its attributes seperately, changing `jif.creaminess` won't change another peanut butter's creaminess
    - a class attribute looks like this:

```python
class PeanutButter:
    some_class_attribute = "I am a class attribute"
    all_peanut_butters = [] # also a class attribute

    def __init__(self,name):
        self.name = name # setting an instance attribute
        PeanutButter.all_peanut_butters.append(self) # altering a class attribute

PeanutButter.some_class_attribute #>>> "I am a class attribute"
```

- What is an `instance` property? When do property functions (getter and setter) get called?
    - a property allows us to create functions that trigger when we get or set an attribute

```python
@property # GETTER
def something(self):
    return self._something # _something is a private variable

@setter.something # SETTER
def something(self, new_value):
    self._something = new_value

jif.something #>>> call the GETTER
jif.something = "Something else" #>>> call the SETTER
```

- What is object inheritance? How can objects inherit from each other? What does the `super()` function do?
    - inheritance allows us to grab all the attributes / methods from another class
    - the inheriting class is the sub-class and the inherited class is the super-class

```python
class OrganicPeanutButter(PeanutButter):
    
    def describe(self):
        super().describe()
        print("and also more stuff")
```

## SQL

- What keywords allow us to create a table in SQL? What keywords delete a table?
    - `CREATE TABLE` creates a table
    - `CREATE TABLE IF NOT EXISTS` creates a table if it doesn't already exist
    - `DROP TABLE` destroys the table
- What is a primary key and why is it important?
    - The primary key is like an index in that it is the unique identifier
    - Very important so that it can connect different tables
- What is a foreign key? Why is it important?
    - In a one to many relationship the primary key is used in the other table's foreign key
    - The foreign key shows which item in the other table it belongs to
    - The foreign key belongs in the many side of the table
    - Inside a many to many relationship the foreign keys go in the join table
    - If it has a foreign key, it is a many that belongs to another table
- What does `JOIN` do?
    - Can use it when creating a join table
    - This will allow us to join tables together usually while trying to read data
    - In SQL if we want data from multiple tables at the same time we need to use a `JOIN`
- What keyword allows us to add a new row in SQL?
    -   `INSERT INTO` creates a new row
- What keyword allows us to read rows in SQL? How can we filter for specific rows?
    - `SELECT FROM`, the `WHERE` allows us to filter based on a condition
    - If you exclude the `WHERE` you will get all the rows
- What keyword allows us to update a row in SQL?
    - `UPDATE SET` will update a row
    - You can also use `WHERE` here to only update specific rows
- What keyword allows us to delete a row in SQL?
    - `DELETE FROM` which similarly we usually pair with a `WHERE`