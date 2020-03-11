---
title: "Basic introduction to classes in Python"
teaching: 20
exercises: 20
questions:
- "What is a class?"
- "How do I create a class?"
- "How do I use classes in my programs?"
objectives:
- "Describe what encapsulation means"
- "Differentiate between classes and object instances"
- "Describe what instance attributes and methods are"
- "Describe what class attributes are"
- "Create classes in Python"
- "Use methods and attributes in a program"
keypoints:
- "Any object in Python is an instance - i.e. a concrete realization - of a class"
- "A class combines attributes and behaviors that have some conceptual relationship with each other"
---

# What's Object Oriented Programming?

- [Object Oriented Programming (OOP)](https://en.wikipedia.org/wiki/Object-oriented_programming) is a programming paradigm in which the flow of a program is controlled by the exchange of information and modification of the state of individual units called *objects*.
- These objects bundle together properties and behaviors that have some relationship with each other.
- In many aspects, OOP mimics how real-life objects are and interact with each other.
- Python is a multi-paradigm programing language, meaning it can be used in OOP, but also in [functional programming](https://en.wikipedia.org/wiki/Functional_programming), [procedureal programming](https://en.wikipedia.org/wiki/Procedural_programming), etc. (very often) mixing them to achieve different purposes on differt parts of the program.

> ## Example: A cup of tea
>
> A cup of tea is an object with several properties and behaviors, i.e. actions that can be executed on them:
> - Properties:
>   - hot: if the tea is hot or not
>   - full: if the cup is full or not
>   - kind: the kind of tea. Is it english breakfast or Earl Grey?
> - Actions:
>   - drink: you drink the tea and the cup becomes empty
>   - warm: you warm the tea, becoming hot.
>   - refill: you refill the cup with more tea
>
{: .challenge}

## Encapsulation

- Encapsulation is one of the basic principles of OOP by which an *entity* bundles together properties (or *attributes* as they are called in Python) and behaviors (*methods*) related to the properties that execute actions.
- This entity is called a *class*.
- Encapsulation enables a class to present an interface on how an object belonging to that class (see below) can be acted upon, hiding from the outside world any implementation details and other properties that need not to be known outside that class.

## Classes and instances

- In Python, classes are created by using the keyword `class`, followed by the name of the class (using CamelCase) and the parent class in parenthesis, if any (more on this in the next episode).

```python
class MyClass:
    """ A simple example class. """
    pass    # <- `pass` just indicates python to do nothing
```

- This code creates a class, but to use it, you must create an *instance* of the class, which is also called an *object*:

```python
a = MyClass()
b = MyClass()

print(f"'a' is an instance of the class {type(a)}")
print(f"'b' is an instance of the class {type(b)}")
print(f"Are 'a' and 'b' equal? {a==b}")
```

- Here, both `a` and `b` are instances of the class `MyClass`, but they are different objects. The above code will print:

```
'a' is an instance of the class <class '__main__.MyClass'>
'b' is an instance of the class <class '__main__.MyClass'>
Are 'a' and 'b' equal? False
```
{: .output}

> ## Built-in classes (or types)
> Python built-in types like `list`, `tuple`, `dict`, `str` and all the numeric types are
> classes, and the variables that use them are instances of those classes. To what classes
> do the following variables belong?
>
> ```python
> a = [1, 2, 3]
> b = (1, 2, 3)
> c = {1, 2, 3}
> d = 42
> e = {"name": "Fluffy", "species": "Three-Headed Dog"}
> f = True
> g = "My taylor is rich!"
> ```
> > ## Solution
> > Using `print(type(variable_name))` in each case results in:
> > - a: `<class 'list'>`
> > - b: `<class 'tuple'>`
> > - c: `<class 'set'>`
> > - d: `<class 'int'>`
> > - e: `<class 'dict'>`
> > - f: `<class 'bool'>`
> > - g: `<class 'str'>`
> {: .solution}
{: .challenge}

## Methods

- The above example class has no attributes nor methods, which is pretty useless.
- When creating a class, you must also define its attributes and methods, so the rest of the code can interact with it.
- Methods define the behavior of the class: the functions (or actions) that can be used to interact with the class.
- They are defined like any other function in Python, using the `def` keyword, but the first input parameter that has a special meaning.

```python
class MySecondClass:
    """ A simple example class with a method. """

    def say_hello(self, name):
        print(f"Hello {name}! This instance is {self}")
```

- Here, `MySecondClass` has a method, `say_hello`, with two input parameters:
    - The first one, usually called `self` refers to the specific instance of the class being used. It is compulsory: **all methods within a class must take `self` as its first argument.**
    - The second argument is just a parameter used within the method, like in any regular Python function.
- As with any function in Python, methods can have any number of positional and keyword arguments, as well as returning values using the keyword `return`.
- To call a method of a class, use the dot notation `.` to separate the name of the object and the method being invoked.
- The value for the first argument, `self`, is assigned automatically to the instance being used and **must not be provided**:

```python
a = MySecondClass()
b = MySecondClass()

a.say_hello("Diego")
b.say_hello("Diego")
```
```
Hello Diego! This instance is <__main__.MySecondClass object at 0x10ef01780>
Hello Diego! This instance is <__main__.MySecondClass object at 0x10ef01be0>
```
{: .output}

- As you can see by the numbers at the end, `a` and `b` are two different instances of class `MySecondClass`.

## Attributes

- Attributes are the properties of a class, the variables that can be read and modified (usually).
- There are two types of attributes: **class attributes** and **instance attributes**.

### Class attributes

- Are linked to the class itself and all instance objects of the class will share the same values... at least initially:
    - If a class attribute is `mutable` (eg. a `list`) and changed its value in one instance, it will change its value in all instances.
    - If it is `immutable` (eg. a number), it will only change in that instance.
- They are defined just after the class definition.
- Access to attributes (both class and instance attributes) use the same dot notation `.` as methods, but without parenthesis.
- Class attributes need to have some initial value.

```python
class ShapesAndColours:
    """ A simple class explaining class attributes. """
    colours = []        # <- mutable
    shape = "square"    # <- immutable

a = ShapesAndColours()
b = ShapesAndColours()

print(f"Before, a.colours = {a.colours} and b.colours = {b.colours}.")
print(f"Before, a.shape = {a.shape} and b.shape = {b.shape}.")

a.colours.append("blue")
a.shape = "circle"

print(f"Now, a.colours = {a.colours} and b.colours = {b.colours}.")
print(f"Now, a.shape = {a.shape} and b.shape = {b.shape}.")
```
```
Before, a.colours = [] and b.colours = [].
Before, a.shape = square and b.shape = square.
Now, a.colours = ['blue'] and b.colours = ['blue'].
Now, a.shape = circle and b.shape = square.
```
{: .output}

- As you can see, the class attribute `colours` has changed in `b` after changing its value in `a`.
- However, changing the value of `shape` in `a` does not affect the value of `shape` in `b` (Note: Indeed, a new instance attribute has been created in `a` called `shape` overriding the value of the class attribute of the same name.)

### Instance attributes

- They are properties specific to the instance.
- Each instance has its own copy and changing the value in one instance does not affect the value of that property in the other instances.
- They are defined within a special `__init__` method, called a constructor.
- The `__init__` method is automatically called when creating an instance of a class.
- As with any other method, the first argument is `self` and it can have any number of positional and keyword arguments.
- To create instance attributes, dot notation `.` is used with `self` as the instance object.

```python
class Computers:
    """ A simple class explaining instance attributes. """

    def __init__(self, brand, models):
        self.brand = brand
        self.models = models

apple = Computers("Apple", ["iMac", "MacBook Pro"])
microsoft = Computers("Microsoft", ["Surface Pro"])

print(f"Apple models are: {apple.models} while Microsoft's are {microsoft.models}")
microsoft.models.append("Surface Lite")
print(f"Apple models are: {apple.models} while Microsoft's are {microsoft.models}")
```
```
Apple models are: ['iMac', 'MacBook Pro'] while Microsoft's are ['Surface Pro']
Apple models are: ['iMac', 'MacBook Pro'] while Microsoft's are ['Surface Pro', 'Surface Lite']
```
{: .output}

> ## Restricted attributes
>
> Contrary to other languages, in Python there are not really `public` and `private`
> members (attributes and methods), however, by convention all attributes and methods
> starting with a single underscore `_` are considered private, only to be used within the class.
{: .callout}

> ## The Cup of Tea class
>
> Create a class called `CupOfTea` that implements the attributes and methods described
> in the first example of the episode. The creation of the instances should take only the
> kind of tea as input, and the cups should be initially full and cold. Additionally, it
> should have a method called `status` that will print all the information related to the
> current status of the cup of tea.
>
> > ## Solution
> >
> > ```python
> > class CupOfTea:
> >
> >     def __init__(self, kind):
> >         self.kind = kind
> >         self._hot = False
> >         self._full = True
> >
> >     def warm(self):
> >         self._hot = True
> >
> >     def drink(self):
> >         self._full = False
> >         self._hot = False
> >
> >     def refill(self):
> >         if self._full:
> >             print("The cup is already filled.")
> >         else:
> >             self._full = True
> >
> >     def status(self):
> >         if not self._full:
> >             print(f"Oh my! Someone drank this cup of {self.kind} and is now empty!")
> >         else:
> >             temperature = "hot" if self._hot else "cold"
> >             print(f"This is a full cup of {temperature} {self.kind}.")
> > ```
> {: .solution}
{: .challenge}

## Special methods and attributes

- Special methods and attributes are enclosed between a double underscore `__`.
- They are not meant to be called directly by the user, but rather are used by Python when something is required from a class or an instance of a class.
- Some common methods and attributes present in most classes are:
    - `__init__` is the method called when creating a new instance of a class.
    - `__repr__` is a method called when we require to have a representation of the object, for example when printing the object with `print(microsoft)`.
    - `__call__` is the method executed when trying to call an instance of a class as if it were a function
    - `__dict__` is an attribute that contains a dictionary with all the attributes and methods available for that object. Note: It does not include any attribute or method inherited from the parent class.

> ## Exploring the classes
>
> Explore the attributes and methods available for the classes created in the examples
> above as well as some of the built-in classes using the special attribute `__dict__`.
> What other special methods and attributes can you see? Can you guess their purpose?
{: .challenge}

> ## Improving the representation of our classes
> In the last CupOfTea example, it will be nicer if we could get the status just by
> calling `print(cup_of_tea_object)` rather than `cup_of_tea_object.status()`
>
> Replace the `status` method by a custom `__repr__` method for the class `CupOfTea` that
> produces the same output. Tip: This function should return a string with the information
> to be printed correctly formatted.
>
> > ## Solution
> >
> > ```python
> > class CupOfTea:
> >
> >     # Everything is the same, but we replace status() by:
> >
> >     def __repr__(self):
> >         if not self._full:
> >             return f"Oh my! Someone drank this cup of {self.kind} and is now empty!"
> >         else:
> >             temperature = "hot" if self._hot else "cold"
> >             return f"This is a full cup of {temperature} {self.kind}."
> > ```
> {: .solution}
{: .challenge}


{% include links.md %}

