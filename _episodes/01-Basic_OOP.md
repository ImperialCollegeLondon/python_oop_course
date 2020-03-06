---
title: "Basic Objetc Oriented Programming (OOP) in Python"
teaching: 30
exercises: 30
questions:
- "What is a class?"
- "How do I create a class?"
- "How do I use classes in my programs?"
objectives:
- "Describe what inheritance means"
- "Describe what composition means"
- "Describe what encapsulation means"
- "Differentiate between classes and object instances"
- "Describe what instance attributes and methods are"
- "Describe what class atributes are"
- "Create classes and subclasses in Python"
- "Use methods and attributes in a program"
keypoints:
- "Any object in Python is an instance - i.e. a concrete realization - of a class"
- "Classes encapsulate attributes and methods that have some conceptual relationship with each other"
- "A subclass inherits the attributes and methods of its parent class"
- "A subclass can overwrite its parent's attributes and methods with its own versions"
---

# What's Object Oriented Programming?

- [Object Oriented Programming (OOP)](https://en.wikipedia.org/wiki/Object-oriented_programming) is a programming paradigm in which the flow of a program is controlled by the exchange of information and modification of the state of individual units called *objects*.
- These objects bundle together properties and behaviours that have some relationship with each other.
- In many aspects, OOP mimics how real-life objects are and interact with each other.
- Python is a multi-paradigm programing language, meaning it can be used in OOP, but also in [functional programming](https://en.wikipedia.org/wiki/Functional_programming), [procedureal programming](https://en.wikipedia.org/wiki/Procedural_programming), etc. (very often) mixing them to achieve different purposes on differt parts of the program.

> ## Example: A cup of tea
>
> A cup of tea is an object with several properties and actions that can be executed on them:
> - Properties:
>   - hot: if the tea is hot or not
>   - full: if the cup is full or not
>   - kind: the kind of tea. Is it english breakfast or Earl Grey?
> - Actions:
>   - drink: you drink the tea and the cup becomes empty
>   - warm: you warm the tea, becoming hot.
>
{: .callout}


{% include links.md %}

