## PISCINE PYTHON DJANGO
### D02 - OBJECT-ORIENTED PROGRAMMING

##### CLASSES

###### CLASS
```python
# pass mean this empty block owner is Foo
# without 'pass' syntax error is expected
class Foo:
    pass

class Bar:
    pass

if __name__ == '__main__':
    f = Foo()
    b = Bar()
    i = int(1)
    print(type(f))
    print(type(b))
    print(type(i))
```

###### ATTRIBUTES AND METHODS
```python
class Car:
    # class function now is called method
    # class variable now is called attribute
    # self is the actual instance of object, "this" in another languages
    # self always needs to be passed
    def drive(self):
        print("Vroom!")

    def paint(self, color):
        self.color = color
        print("%s is now the new color" % str(color))

    def get_color(self):
        return self.color

if __name__ == '__main__':
    x = Car()
    print("Drive method called:")
    x.drive()

    print("\nChanging attribute value with a setter :")
    x.paint("red")
    print("\nPrint getter return :")
    print(x.get_color())

    print("\nDirect access to attribute :")
    x.color = "blue"
    print(x.color)
```

###### CONSTRUCTOR DESTRUCTOR
```python
class Warrior:
    # constructor default value if not passed "name='Bob'"
    def __init__(self, name='Bob'):
        self.name = name
        print("A warrior appeared! His name is %s." % name)

    def __del__(self):
        print("%s just died." % self.name)

if __name__ == '__main__':
    bob = Warrior()
    tom = Warrior("Tom")
    del tom
```

###### DECORATORS
```python
import datetime

# Raw function

def raw_function(s):
    return s

# With decorators

def decorator(f):

    def function(s):
        return (datetime.datetime.now().__str__() + ' ' + f(s))

    return function

def dec_function_assign(s):
    return s

dec_function_assign = decorator(dec_function_assign)

@decorator
def dec_function_def(s):
    return s

if __name__ == '__main__':
    print("Without decorator: ")
    print(raw_function("foo"))

    print("\nWith decorator (decorated function as variable) :")
    print(dec_function_assign("foo"))

    print("\nWith decorator (@ syntax) :")
    print(dec_function_def("foo"))
```

###### CLASS ATTRIBUTES AND METHODS
In Python, a class method is a method that is bound to the class and not the instance of the object. It is defined using the "@classmethod" decorator, followed by the "classmethod" keyword and a function that takes the class as its first argument (usually named "cls").

The purpose of class methods is to provide a way for a method to be called on the class itself, rather than on an instance of the class. Class method will change all class attributes of all instances of same class.
```python
class Foo:
    # initial value for all created object instances
    counter = 0

    def __init__(self):
        # "self.increment_counter()" will make python search for
        # increment_counter inside class or yourself "self"
        self.increment_counter()
        print("Foo instance created. Number of instances : [%d]." % self.counter)

    def __del__(self):
        self.decrement_counter()
        print("Foo instance deleted. Number of instances : [%d]." % self.counter)

    # "@classmethod" changes methods to class method
    @classmethod
    def increment_counter(cls):
        cls.counter += 1

    @classmethod
    def decrement_counter(cls):
        cls.counter -= 1

if __name__ == '__main__':
    a = Foo()
    del a
    a = Foo()
    b = Foo()
    c = Foo()
    del b
    b = Foo()
```

###### SCOPE - INNER CLASS / NESTED CLASS
```python
class Bar:
    des = 'Bar in main.'

class Foo:
    des = 'Foo in main.'

    class Bar:
        des = 'Bar in Foo.'

    class Foo:
        def method(self):
            print('This is a method in Foo.Foo.')

if __name__ == '__main__':
    print("Description of Bar in main scope :")
    print("- From class :")
    print(Bar.des)
    print("- From instance :")
    b = Bar()
    print(b.des)

    print("\nDescription of Bar in Foo :")
    print("- From class :")
    print(Foo.Bar.des)
    print("- From instance :")
    fb = Foo.Bar()
    print(fb.des)

    print("\nMethod class (method() from Foo.Foo instance) :")
    ff = Foo.Foo()
    ff.method()
```

###### INHERENCE / INHERITANCE
```python
class Dinosaur:
    des = 'All my friends are dead. :('

    def __init__(self):
        print("A dinosaur appeared!")

    def roar(self):
        print("ROAARRR!")

    is_extinct = True

class TRex(Dinosaur):
    des = "If you're happy clap your... oh, nevermind."

if __name__ == '__main__':
    print("Dinosaur case :")
    print("- Instantiation: ")
    d = Dinosaur()
    print("- Description: ")
    print(d.des)
    print("- Roar :")
    d.roar()
    print("- Is this extinct?")
    print(d.is_extinct)

    print("\nTrex case :")
    print("- Instantiation :")
    t = TRex()
    print("- Description :")
    print(t.des)
    print("- Roar :")
    t.roar()
    print("- Is this extinct?")
    print(t.is_extinct)
```

###### METHOD OVERRIDE / POLYMORPHISM
```python
class Dinosaur:
    des = 'All my friends are dead. :('

    def __init__(self):
        print("A dinosaur appeared!")

    def roar(self):
        print("ROAARRR!")

    is_extinct = True

class Chicken(Dinosaur):
    des = "Great camera stabilisator!"

    def __init__(self):
        super().__init__()
        print("It's a chicken!")

    def roar(self):
        print("cot cot?")

    is_extinct = False

if __name__ == '__main__':
    print('Dinosaur case :')
    print("- Instantiation :")
    d = Dinosaur()
    print("- Description :")
    print(d.des)
    print("- Roar :")
    d.roar()
    print("- Is this extinct?")
    print(d.is_extinct)

    print('\nChicken case :')
    print("- Instantiation :")
    c = Chicken()
    print("- Description :")
    print(c.des)
    print("- Roar :")
    c.roar()
    print("- Is this extinct?")
    print(c.is_extinct)
```

###### EXCEPTIONS
```python
class Vegetables:
    pass

class Fries:
    pass

class Human:
    def eat(self, food):
        if isinstance(food, Vegetables):
            raise Exception("I don't like this!")
        else:
            print("Miam!")

if __name__ == '__main__':
    h = Human()
    h.eat(Fries())
    h.eat(Vegetables())
```

###### EXCEPTIONS - TRY / EXCEPT
```python
class Vegetables:
    pass

class Fries:
    pass

class Human:
    def eat(self, food):
        if isinstance(food, Vegetables):
            raise Exception("I don't like this!")
        else:
            print("Miam!")

if __name__ == '__main__':
    h = Human()
    h.eat(Fries())
    try:
        h.eat(Vegetables())
    except Exception as e:
        print(e)
```

###### IMPORT MODULES
###### IMPORT ENTIRE MODULE
module.py
```python
"""This is the description of the module."""

var = "This is a variable."

class Foo:
    """Foo class description."""

    def __str__(self):
        """Foo.__str__() method description."""
        return ("This is a Foo instance.")

def function1():
    """Function1 description."""
    print("This is a call of function1().")

def function2(param : int) -> str :
    """Function2 description. It takes an int and returns a str."""
    print("this is a call of function2().")
    return str(param)
```

main.py
```python
import module

if __name__ == '__main__':
    f = module.Foo()
    f()
    module.function1()
    module.function2(1)
```

###### IMPORT PARTIAL MODULE / FROM
main.py
```python
from module import var
from module import function1, function2

if __name__ == '__main__':
    print(var)
    function1()
    function2(1)
```
