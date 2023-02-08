## PISCINE PYTHON DJANGO
### D01 - PYTHON BASICS

##### HELLO WORLD

###### INTERPRETER / HELP
```bash
# open python3 real time interpreter
python3

# inside python3 interpreter you can call the manual or help
>>> help()

# in python3 help you can print help keywords
> help keywords

# in python3 help you can search for a def example
> help def

# in python3 help you can print help topis
> help topics
```

###### hello_world.py
```python
if __name__ == '__main__' :
    s = "Hello World !"
    print(s)
```

What does ```if __name__ == '__main__'``` do in Python?

Nesting code under ```if __name__ == '__main__'``` allows you to cater to different use cases:
Example:
```python
# echo.py

def echo(text: str, repetitions: int = 3) -> str:
    """Imitate a real-world echo."""
    echoed_text = ""
    for i in range(repetitions, 0, -1):
        echoed_text += f"{text[-i:]}\n"
    return f"{echoed_text.lower()}."

if __name__ == "__main__":
    text = input("Yell something at a mountain: ")
    print(echo(text))
```

- Script: When run as a script, your code prompts the user for input, calls echo(), and prints the result.
Example: if you call **python3 echo.py**.
- Module: When you import echo as a module, then echo() gets defined, but no code executes. You provide echo() to the main code session without any side effects.
Example: **from echo import echo** in another python file.

##### BASIC TYPES

###### INT / FLOAT
```python
if __name__ == '__main__' :
    a = 1
    a = int(1)
    b = int(a)

    a = 1.0
    a = float(1.0)
    b = float(a)
```

###### STRING
```python
if __name__ == '__main__' :
    a = "this is a string"
    b = str("this, again, is a sring")
    c = str(b)

    print(a)
    print(c)
```

###### STRING QUOTES
```python
if __name__ == '__main__' :
    a = 'I can put double quotes " <-- like this --> " '
    print(a)

    a = "I can put simple quotes '  <-- like that --> ' "
    print(a)

    a = """
            'I can put what I "want' and carriage return are ...
            preserved'.
    """
    print(a)

    a = '''
            'I can put what I "want' and carriage returns are ...
            AGAIN, preserved'.
    '''
    print(a)
```

###### PRINTING STRING
```python
if __name__ == '__main__' :
    beatles = "Hey Jude, don't make it bad"
    print(beatles[0])
    print(beatles[1])
    print(beatles[2])
    # prints "Jude", includes [4]=J excludes [8]=,
    print(beatles[4:8])

    # you cannot change a string by index like in C/C++, strings in python are declared immutable
    beatles[0] = 'Z'
```

##### FUNCTIONS

###### FUNCTION DECLARATION
```python
def hello_world():
    print('Hello World !')

if __name__ == '__main__':
    hello_world()
```

###### ARGUMENTS
```python
def my_function():
    print('...always look on the bright side')

def my_function2(argument):
    print(argument)

def my_function3(argument='(Whistle)'):
    print(argument)

def my_function4(argument, argument2):
    print(argument, argument2)

if __name__ == '__main__':
    my_function()
    my_function2(' of life...')
    my_function3()
    # argument label
    my_function4(argument2 ='of life...', argument='Always look on the light side')
```

###### DOCSTRING
```python
def hello_world():
    """
            This function prints Hello World !
    """
    print('Hello World !')

if __name__ == '__main__':
    # prints documentation if exists about the function
    help(hello_world)
```

###### SCOPE
```python
global_var = "This var is in the global module namespace"

def my_function():
    local_func_var = 'This variable is in the function namespace'

    def inner_function():
        enclosed_func_var = 'This variable is in the enclosed function namespace'
        print('[inner_function] - ', global_var)
        print('[inner_function] - ', local_func_var)
        print('[inner_function] - ', enclosed_func_var, '\n')

    inner_function()

    print('[my_function] - ', global_var,)
    print('[my_function] - ', local_func_var, '\n')
    #print('[my_function] - ', enclosed_func_var, '\n')

if __name__ == '__main__':
    my_function()
    print('[global scope] - ', global_var, '\n')
    print('[global scope] - ', local_func_var, '\n')
    #print('[global scope] - ', enclosed_func_var, '\n')
```

###### LAMBDA / ANONYMOUS FUNCTIONS
```python
def apply_modifier(modifier, target):
    result = modifier(target)
    return result

if __name__ == '__main__':
    a = 1
    modifier = lambda x : x / 2
    b = apply_modifier(modifier, a)
    print(b)
```

##### METHODS

###### TYPE
```python
if __name__ == '__main__':
    a = "To be or not to be"
    print(type(a))

    b = 1
    print(type(b))

    c = False
    print(type(c))

    # Null in python
    d = None
    print(type(d))

    print(type(type(a)))
```

###### CALL A METHOD
```python
if __name__ == '__main__':
    var = str('This is a string')

    var2 = var.replace(' string', 'mazing !')

    print(var2)
```

###### CHECK ALL METHODS IN A CLASS
```bash
# type python3 in a shell
python3

# inside python3 interpreter you can call help with a class
# to see all methods
>>> help(str)

# inside python3 interpreter you can call dir with a class
# to see all methods in a list format
>>> dir(str)
```

##### FORMAT STRING

###### FORMAT
```python
if __name__ == '__main__':
    base_string = "{0} bites the {1}"
    print(base_string)
    new_string = base_string.format('Another one', 'dust')
    print(new_string)

    base_string = "{who} bites the {what}"
    print(base_string)
    new_string = base_string.format(what='another one', who='Dust')
    print(new_string)

    base_string = "%s bites the %s"
    print(base_string)
    new_string = base_string%('She', 'life to the fullest')
    print(new_string)
```

##### TYPE CONTAINERS

###### SEQUENCE - LIST, TUPLE, RANGE
```python
def list_type():
    # mutable
    my_list = ['a', 'b', 'c']
    my_list = list()
    my_list.append('a')
    my_list.append(2)
    my_list.append(3.0)
    print("my_list : ", my_list)
    print("my_list[2] : ", my_list[2])

def tuple_type():
    # immutable
    my_tuple = tuple()
    my_tuple = (1, 'b', 3.0)
    print("my_tuple :", my_tuple)
    print("my_tuple[2] :", my_tuple[2])

def range_type():
    # immutable
    # create range elements between 0 and 4, 5 is excluded
    my_range = range(5)
    # create range elements between 2 and 5, 2 and 5 is excluded
    my_range = range(2, 5)
    # to print range, you need to convert in a list
    my_range = list(range(2, 10, 2))
    print("my_range : ", my_range)

if __name__ == '__main__':
    list_type()
    tuple_type()
    range_type()
```

###### HASHMAP - DICTIONARY
```python
if __name__ == '__main__':
    # mutable
    # dictionnary is not sorted / ordered automatic
    # after insert elements the order by default is not the same
    my_dict = {'type':'dictionnary'}
    my_dict = dict()
    my_dict['type'] = 'dictionnary'
    # print key
    print("my_dict : ", my_dict)
    # print value
    print("my_dict['type'] : ", my_dict['type'])
```

##### OPERATORS AND CONDITIONS

###### OPERATORS
```python
def math_operators():
    print(5 - 1)
    print(2 + 1.0)
    print(1 * 2)
    print(42 / 41)
    print(42 // 42)
    print(42 % 42)

def comparison_operators():
    print(1 == 2)
    print(1 != 2)
    print(1 > 2)
    print(1 < 2)
    print(1 >= 2)
    print(1 <= 2)

def concatenations_operators():
    print("FUUUUUU" + "SIOOOOOOON !!")
    print(0 + "This will fail miserably.")

if __name__ == '__main__':
    math_operators()
    print()
    comparison_operators()
    print()
    concatenations_operators()
```

###### CONDITIONS
```python
def what_is_love(love):
    if love == True :
        print('Love is true')
    elif love == False :
        print('Love is not true')
    else:
        print("What is love ? Baby don't hurt me, come on !")

if __name__ == '__main__':
    what_is_love(None)
```

###### IDENTITY COMPARISONS
```python
if __name__ == '__main__':
    a = int(1)
    b = float(1)
    c = int(2)
    print('a of type : ', type(a), 'and value :', a)
    print('b of type : ', type(b), 'and value :', b)

    if a == b :
        print('a has the same value as b')
    else:
        print('a has NOT the same value as b')

    # is compare type and value, true only if object type and value are equal
    if a is b :
        print('a is the same object as b')
    else:
        print('a is NOT the same object as b')

    if a is c :
        print('a is the same object as c')
    else:
        print('a is NOT the same object as c')
```

###### ITERATE AND SEARCH INSIDE A SEQUENCE / LIST
```python
if __name__ == '__main__':
    mamas_and_papas = ['Michelle', 'Cass', 'Denny', 'John']

    # in return true if "value" is inside of a list
    if 'Jill' in mamas_and_papas:
        print('Jill is not in The Mamas & Papas')
    elif 'Cass' in mamas_and_papas:
        print('Cass is in the Mamas & Papas')
```

##### LOOPS

###### WHILE
```python
if __name__ == '__main__':
    my_list = [1, 2, 3, 4, 5]

    print('my_list:')
    i = 0
    while i < len(my_list):
        print(my_list[i])
        i += 1
```

###### FOR
```python
if __name__ == '__main__':
    print('my_range:')
    for element in range(5):
        print(element)
```

###### FOR WITH DICTIONARY
```python
if __name__ == '__main__':
    my_dict = {
            'France': 'fr',
            'Italy': 'it',
            'Spain': 'es',
            'Japan': 'jp',
    }
    print('my_dict:')
    for key, value in my_dict.items():
        print(key, ':', value)
```

##### COMPREHENSION

###### LIST COMPREHENSION
List comprehension offers a shorter syntax when you want to create a new list based on the values of an existing list.
```python
if __name__ == '__main__':
    l = []
    for i in range(10):
        if i % 2 == 0:
            l.append(i ** 2)
    print(l)

    # The return value is a new list, leaving the old list unchanged.
    l = [i ** 2 for i in range(10) if i % 2 == 0]
    print(l)
```

##### I/O FILE SYSTEM

###### OPEN
```python
if __name__ == '__main__':
    filename = 'my_file.txt'

    f = open(filename, 'w')
    f.write('Hard as a rock !')
    f.close()
```

###### OPEN WITH
```with open``` is a context manager in Python that is used to open a file and create a context in which the file will be used. The advantage of using ```with open``` is that it automatically takes care of closing the file after the indented block of code is executed, even if an exception is raised. This way, you don't have to explicitly close the file, which can help you avoid resource leaks.
```python
if __name__ == '__main__':
    filename = 'my_file.txt'

    with open(filename, 'r') as f:
        for line in f:
            print(line)
```

##### PROGRAM ARGUMENTS

###### ARGV
```python
import sys

if __name__ == '__main__':
    print(sys.argv)
```
