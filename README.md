# Introduction of Object Oriented Programming in Python 

## Abstract

In Python, object-oriented Programming (OOPs) is a programming paradigm that uses objects and classes in programming. It aims to implement real-world entities like inheritance, polymorphisms, encapsulation, etc. in the programming. The main concept of OOPs is to bind the data and the functions that work on that together as a single unit so that no other part of the code can access this data. 

##  1. Introduction

![OOps](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20200623174126/Python-OOPS-Concept.png)

## 2. Main Concepts of Object-Oriented Programming (OOPs) 

### 2.1 Class
A class is a collection of objects. A class contains the blueprints or the prototype from which the objects are being created. It is a logical entity that contains some attributes and methods. 
#### Some points on Python class:  
* Classes are created by keyword class.
* Attributes are the variables that belong to a class.
* Attributes are always public and can be accessed using the dot (.) operator. Eg.: Myclass.Myattribute

#### Class Definition Syntax:
```
class ClassName:
   Statement-1
   .
   .
   .Statement-N
   ```
  
  #### Creating an empty class
  
  ```python
  
  class Person():
    pass
    
  ```


### 2.2 Objects
The object is an entity that has a state and behavior associated with it. It may be any real-world object like a mouse, keyboard, chair, table, pen, person etc.
#### An object consists of :
* __State__: It is represented by the attributes of an object. It also reflects the properties of an object. State or attributes can be considered as the height , age  etc information of the person.
* __Behavior__: It is represented by the methods of an object. It also reflects the response of an object to other objects. Behaviour of the person can be considered as running, eating etc.
* __Identity__: It gives a unique name to an object and enables one object to interact with other objects. The identity of person can be considered as the name of the person.

####  Creating an object
```python
obj = Person()
```

#### The self  
1. Class methods must have an extra first parameter in the method definition. We do not give a value for this parameter when we call the method, Python provides it
2. If we have a method that takes no arguments, then we still have to have one argument.
3. This is similar to this pointer in C++ and this reference in Java.
* When we call a method of this object as obj.method(arg1, arg2), this is automatically converted by Python into Person.method(obj, arg1, arg2)

### 2.3  Polymorphism
### 2.4 Encapsulation
### 2.5 Inheritance

## 4. Conclusion

## 5. References
1. https://www.geeksforgeeks.org/python-oops-concepts
2. https://www.programiz.com/python-programming/object-oriented-programming


