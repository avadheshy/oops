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
* __State__: It is represented by the attributes of an object. It also reflects the properties of an object. State or attributes person object can be considered as the height , age  etc information of the person.
* __Behavior__: It is represented by the methods of an object. It also reflects the response of an object to other objects. Behaviour of the person object can be considered as running, eating etc.
* __Identity__: It gives a unique name to an object and enables one object to interact with other objects. The identity of object person can be considered as the name of the person.

####  Creating an object
```python
obj = Person()
```

#### The self  
1. Class methods must have an extra first parameter in the method definition. We do not give a value for this parameter when we call the method, Python provides it
2. If we have a method that takes no arguments, then we still have to have one argument.
3. This is similar to this pointer in C++ and this reference in Java.
* When we call a method of this object as obj.method(arg1, arg2), this is automatically converted by Python into Person.method(obj, arg1, arg2)
#### The __init__ method 
The __init__ method is similar to constructors in C++ and Java. It is run as soon as an object of a class is instantiated. The method is useful to do any initialization you want to do with your object. 
#### Class and Instance Attributes in Python
* All variables which are assigned a value in the class declaration are class variables. And variables that are assigned values inside methods are instance variables.
* Class variable can be access by className.variableName and instanse variable can be access by objectName.variable name.
* If a object changes the class variable with className.classVariableName then it changes to class variable.
* If a object chenges the class variable with obj.classVariable then it is changing to its own class varible, after taht it will not be affected with the change in classname.Class variable.
```python
class Person:
    stream = 'cse'                  # Class Variable
    def __init__(self,name,roll):
        self.name = name            # Instance Variable
        self.roll = roll            # Instance Variable
  
# Objects of CSStudent class
a = CSStudent('Geek', 1)
b = CSStudent('Nerd', 2)
  
print(a.stream)  # prints "cse"
print(b.stream)  # prints "cse"
print(a.name)    # prints "Geek"
print(b.name)    # prints "Nerd"
print(a.roll)    # prints "1"
print(b.roll)    # prints "2"
print(CSStudent.stream) # prints "cse"
  
# Now if we change the stream for just a it won't be changed for b
a.stream = 'ece'
print(a.stream) # prints 'ece'
print(b.stream) # prints 'cse'
  
# To change the stream for all instances of the class we can change it 
# directly from the class
CSStudent.stream = 'mech'
  
print(a.stream) # prints 'ece'
print(b.stream) # prints 'mech'
```
#### Instance, Class, and Static Methods:
* Instance method 

* Class method 
   1. A class method is a method that is bound to the class and not the object of the class.
   2. They have the access to the state of the class as it takes a class parameter that points to the class and not the object instance.
   3. It can modify a class state that would apply across all the instances of the class.
* Static method
   Syntax: 
```python
   class C(object):
      @classmethod
      def fun(cls, arg1, arg2, ...):
       ....
       '''
fun: function that needs to be converted into a class method
returns: a class method for function.
   A static method does not receive an implicit first argument. 

Syntax: 
```python
class C(object):
    @staticmethod
    def fun(arg1, arg2, ...):
        ...
     ```
returns: a static method for function fun.
A static method is also a method that is bound to the class and not the object of the class.
A static method can’t access or modify the class state.
It is present in a class because it makes sense for the method to be present in class.
```python

# Python program to demonstrate
# use of class method and static method.
from datetime import date
  
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
      
    # a class method to create a Person object by birth year.
    @classmethod
    def fromBirthYear(cls, name, year):
        return cls(name, date.today().year - year)
      
    # a static method to check if a Person is adult or not.
    @staticmethod
    def isAdult(age):
        return age > 18
  
person1 = Person('mayank', 21)
person2 = Person.fromBirthYear('mayank', 1996)
  
print (person1.age)
print (person2.age)
  
# print the result
print (Person.isAdult(22))
```
 output 
 ```
21
25
True

 ```

### 2.3 Inheritance
It generally means “inheriting or transfer of characteristics from parent to child class without any modification”. The new class is called the derived/child class and the one from which it is derived is called a parent/base class.
#### Types of inheritance
![](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2017/07/Types-of-Inheritance.jpg)
###### Single Inheritance:
Single level inheritance enables a derived class to inherit characteristics from a single parent class.
```python
class employee1()://This is a parent class
def __init__(self, name, age, salary):  
self.name = name
self.age = age
self.salary = salary
 
class childemployee(employee1)://This is a child class
def __init__(self, name, age, salary,id):
self.name = name
self.age = age
self.salary = salary
self.id = id
emp1 = employee1('harshit',22,1000)
 
print(emp1.age)
```
```
output : 22
```
###### Multilevel Inheritance:
Multi-level inheritance enables a derived class to inherit properties from an immediate parent class which in turn inherits properties from his parent class.
```python
class employee()://Super class
def __init__(self,name,age,salary):  
self.name = name
self.age = age
self.salary = salary
class childemployee1(employee)://First child class
def __init__(self,name,age,salary):
self.name = name
self.age = age
self.salary = salary
 
class childemployee2(childemployee1)://Second child class
def __init__(self, name, age, salary):
self.name = name
self.age = age
self.salary = salary
emp1 = employee('harshit',22,1000)
emp2 = childemployee1('arjun',23,2000)
 
print(emp1.age)
print(emp2.age)
```
``` 
output:22,23
```
## Hierarchical Inheritance:
Hierarchical level inheritance enables more than one derived class to inherit properties from a parent class.
```python 
class employee():
def __init__(self, name, age, salary):     //Hierarchical Inheritance
self.name = name
self.age = age
self.salary = salary
 
class childemployee1(employee):
def __init__(self,name,age,salary):
self.name = name
self.age = age
self.salary = salary
 
class childemployee2(employee):
def __init__(self, name, age, salary):
self.name = name
self.age = age
self.salary = salary
emp1 = employee('harshit',22,1000)
emp2 = employee('arjun',23,2000)
 
print(emp1.age)
print(emp2.age)
```
``` 
output : 22,23 
```
#####  Multiple Inheritance:
Multiple level inheritance enables one derived class to inherit properties from more than one base class.
```python
class employee1()://Parent class
    def __init__(self, name, age, salary):  
        self.name = name
        self.age = age
        self.salary = salary
 
class employee2()://Parent class
    def __init__(self,name,age,salary,id):
     self.name = name
     self.age = age
     self.salary = salary
     self.id = id
 
class childemployee(employee1,employee2):
    def __init__(self, name, age, salary,id):
     self.name = name
     self.age = age
     self.salary = salary
     self.id = id
emp1 = employee1('harshit',22,1000)
emp2 = employee2('arjun',23,2000,1234)
 
print(emp1.age)
print(emp2.id)
```
```
output:22, 1234
```

### 2.4  Polymorphism
it is a property of an object which allows it to take multiple forms.
#### Polymorphism is of two types:

* Compile-time Polymorphism:
A compile-time polymorphism also called as static polymorphism which gets resolved during the compilation time of the program. One common example is “method overloading”. 
```python
class employee1():
def name(self):
print("Harshit is his name")    
def salary(self):
print("3000 is his salary")
 
def age(self):
print("22 is his age")
 
class employee2():
def name(self):
print("Rahul is his name")
 
def salary(self):
print("4000 is his salary")
 
def age(self):
print("23 is his age")
 
def func(obj)://Method Overloading
obj.name()
obj.salary()
obj.age()
 
obj_emp1 = employee1()
obj_emp2 = employee2()
 
func(obj_emp1)
func(obj_emp2)
```
```
output:
Harshit is his name
3000 is his salary
22 is his age
Rahul is his name
4000 is his salary
23 is his age

```
* Run-time Polymorphism:
A run-time Polymorphism is also, called as dynamic polymorphism where it gets resolved into the run time. One common example of Run-time polymorphism is “method overriding”. 
```python 
class employee():
   def __init__(self,name,age,id,salary):  
       self.name = name
       self.age = age
       self.salary = salary
       self.id = id
def earn(self):
        pass
 
class childemployee1(employee):
 
   def earn(self)://Run-time polymorphism
      print("no money")
 
class childemployee2(employee):
 
   def earn(self):
       print("has money")
 
c = childemployee1
c.earn(employee)
d = childemployee2
d.earn(employee)

```
```
Output: no money, has money`

```
### 2.5 Encapsulation
In a raw form, encapsulation basically means binding up of data in a single class. Python does not have any private keyword, unlike Java. A class shouldn’t be directly accessed but be prefixed in an underscore.
```python
class employee():
def __init__(self):
self.__maxearn = 1000000
def earn(self):
print("earning is:{}".format(self.__maxearn))
 
def setmaxearn(self,earn)://setter method used for accesing private class
self.__maxearn = earn
 
emp1 = employee()
emp1.earn()
 
emp1.__maxearn = 10000
emp1.earn()
 
emp1.setmaxearn(10000)
emp1.earn()
```
```
Output:
earning is:1000000,earning is:1000000,earning is:10000
```
### 2.6 Abstraction

Suppose you booked a movie ticket from bookmyshow using net banking or any other process. You don’t know the procedure of how the pin is generated or how the verification is done. This is called ‘abstraction’ from the programming aspect, it basically means you only show the implementation details of a particular process and hide the details from the user. It is used to simplify complex problems by modeling classes appropriate to the problem.
An abstract class cannot be instantiated which simply means you cannot create objects for this type of class. It can only be used for inheriting the functionalities.
```python
from abc import ABC,abstractmethod
class employee(ABC):
def emp_id(self,id,name,age,salary):    //Abstraction
pass
 
class childemployee1(employee):
def emp_id(self,id):
print("emp_id is 12345")
 
emp1 = childemployee1()
emp1.emp_id(id)
```
```
Output: emp_id is 12345
```
## 4. Conclusion

## 5. References
1. https://www.geeksforgeeks.org/python-oops-concepts
2. https://www.programiz.com/python-programming/object-oriented-programming
3. https://www.edureka.co/blog/object-oriented-programming-python


