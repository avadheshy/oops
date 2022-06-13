# Introduction to Object Oriented Programming in Python
## Abstract
With the incrementing need of representing realworld objects into software programs, object oriented
programming has emerged as one of the popular methods to
do so. Python is one such object oriented programming
language, that is used for performing a variety of tasks such as
interactive desktop application development, web application
development, artificial intelligence and image processing, and
many more applications. In this we concentrates on how
object oriented concepts can be implemented using the python
programming language.


 

##  1. Introduction
In Python, object-oriented Programming (OOPs) is a programming paradigm that uses objects and classes in programming. It aims to implement real-world entities like inheritance, polymorphisms, encapsulation, etc. in the programming. The main concept of OOPs is to bind the data and the functions that work on that together as a single unit so that no other part of the code can access this data.
![OOps](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20200623174126/Python-OOPS-Concept.png)

## 2. Main Concepts of Object-Oriented Programming (OOPs) 

### 2.1 Class
A class is a collection of objects. A class contains the blueprints or the prototype from which the objects are being created. It is a logical entity that contains some attributes and methods. 
#### Some points on Python class:  
* Classes are created by keyword class.
* Attributes are the variables that belong to a class.
* Attributes are always public and can be accessed using the dot (.) operator.

#### Class Definition Syntax:
```python
class ClassName:
   Statement-1
   .
   .
   Statement-N
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

#### self  parameter
1. Class methods must have an extra first parameter in the method definition. We do not give a value for this parameter when we call the method, Python provides it
2. If we have a method that takes no arguments, then we still have to have one argument.
3. This is similar to this pointer in C++ and this reference in Java.
* When we call a method of this object as obj.method(arg1, arg2), this is automatically converted by Python into Person.method(obj, arg1, arg2)
#### __init__ method 
The __init__ method is similar to constructors in C++ and Java. It is run as soon as an object of a class is instantiated. The method is useful to do any initialization you want to do with your object. 
#### Class and Instance Attributes in Python
* All variables which are assigned a value in the class declaration are class variables and variables that are assigned values inside methods are instance variables.
* Class variable can be access by className.variableName and instanse variable can be access by objectName.variable name.
* If a object changes the class variable with className.classVariableName then it changes to class variable.
* If a object chenges the class variable with obj.classVariable then it is changing to its own instance variable, after that it will not be affected with the change in classname.ClassVariable.
#### Instance, Class, and Static Methods:
* Instance method 
1. Instance methonds are those which are related with the instance of the class. 
2. This type of methods must contain self parameter in the defenition.
* Class method 
1. A class method is a method that is bound to the class and not the object of the class.
2. They have the access to the state of the class as it takes a class parameter that points to the class and not the object instance.
3. It can modify a class state that would apply across all the instances of the class.
4. A method can be declared class methond with the   __@classmethod__ decorator.
   
   Syntax of class method
   ```python
   class Person():
     @classmethod
     def fun(cls,arg1):
       ...
   ```

* Static method

A static method does not receive an implicit first argument
Syntax: 
```python
class Person():
    @staticmethod
    def fun(arg1, arg2, ...):
        ....
```

1. A static method is also a method that is bound to the class and not the object of the class.
2. A static method can’t access or modify the class state.
3. It is present in a class because it makes sense for the method to be present in class.
    
 Example
 ```python
 class Person(): # making Person class
    person_state = 'bengaluru' # making a class/static variable
    def __init__(self,name,age): # initialising attributes of person class
        self.name = name
        self.age = age
    def display(self): # defining instance method
        print(f'{self.name} home town is {self.person_state} and age :{self.age}')
    @classmethod   # defining class method
    def change_state(cls,state):
        cls.person_state = state
    @staticmethod # defining static method
    def is_adult(age):
        if age >= 18:
            print('yes')
        else:
            print('No')

if __name__ == '__main__':
    p1=Person('Kaif',23) # making object of Person class
    p2=Person('bhuasn',24)
    p3=Person('abc',17)
    p1.display() # calling display function of p1 object
    p2.display()
    p3.display()
    p3.person_state = 'delhi' # changing p3 person state to delhi
    Person.change_state('kolkata') # calling class method and changing state of 
    #all the objects except p3 to kolkata
    p1.display()
    p2.display()
    p3.display()
    Person.is_adult(p1.age) # calling static method
 ```
 ```
output:
Kaif home town is bengaluru and age :23
bhuasn home town is bengaluru and age :24
abc home town is bengaluru and age :17
Kaif home town is kolkata and age :23
bhuasn home town is kolkata and age :24
abc home town is delhi and age :17
yes
```
## 3. Inheritance
It generally means “inheriting or transfer of characteristics from parent to child class without any modification”. The new class is called the derived/child class and the one from which it is derived is called a parent/base class.

Syntax of inheritance
```python
class Base():
   pass
class child(Base):
   pass
```
There are four types of inheritance in python.
### 3.1 Single Inheritance:
Single level inheritance enables a derived class to inherit characteristics from a single parent class.
![](https://media.geeksforgeeks.org/wp-content/uploads/20200108135809/inheritance11.png)
Example 
```python
class Person(): # making Person class
    def __init__(self,name,age): # initialising attributes of person class
        self.name = name
        self.age = age
    def display(self): # defining instance method
        print(f'empolyee name is {self.name}  and age :{self.age}')
class Employee(Person):y# single inheritance
    def __init__(self, name, age,id,salary):
        super().__init__(name, age)
        self.id = id
        self.salary=salary
    def show(self):
        print(f'employee id is {self.id},salary is {self.salary}')

if __name__ == '__main__':
   emp1 = Employee('abc',21,1122,50000)
   emp1.display()
   emp1.show()
```
```
output :
empolyee name is abc  and age :21
employee id is 1122,salary is 50000
```
### 3.2 Multilevel Inheritance:
Multi-level inheritance enables a derived class to inherit properties from an immediate parent class which in turn inherits properties from his parent class.![](https://media.geeksforgeeks.org/wp-content/uploads/20200108144705/Multilevel-inheritance1.png)
Example
```python
class Person(): # making Person class
    def __init__(self,name,age): # initialising attributes of person class
        self.name = name
        self.age = age
    def display(self): # defining instance method
        print(f'empolyee name is {self.name}  and age :{self.age}')
class Employee(Person):# single inheritance
    def __init__(self, name, age,id,salary):
        super().__init__(name, age)
        self.id = id
        self.salary=salary
    def show(self):
        print(f'employee id is {self.id},salary is {self.salary}')
class Manager(Employee):# multilabel inheritance
    def __init__(self, name, age, id, salary,number):
        super().__init__(name, age, id, salary)
        self.number_of_employee = number
    def total_employee(self):
        print(f'number of employee is under the manager {self.name} is {self.number_of_employee}')

if __name__ == '__main__':
   mngr = Manager('abc',21,1122,50000,11)
   mngr.display()
   mngr.show()
   mngr.total_employee()

```
``` 
empolyee name is abc  and age :21
employee id is 1122,salary is 50000
number of employee is under the manager abc is 11
```
### 3.3 Hierarchical Inheritance:
Hierarchical level inheritance enables more than one derived class to inherit properties from a parent class.
![](https://media.geeksforgeeks.org/wp-content/uploads/20200108144949/Hierarchical-inheritance1.png)
Example:
```python 
class Manager():
    def __init__(self,manager_name):
        self.manager_name = manager_name
    def display_manager(self):
        print(f'manager name is {self.manager_name}')
class Employee1(Manager):
    def __init__(self, manager_name,name):
        super().__init__(manager_name)
        self.name=name
    def display_employee(self):
        print(f'employee name is {self.name}')
class Employee2(Manager):
    def __init__(self, manager_name,name):
        super().__init__(manager_name)
        self.name=name
    def display_employee(self):
        print(f'employee name is {self.name}')

if __name__ == '__main__':
    emp1=Employee1('abc','ram')
    emp2=Employee2('def','sita')
    emp1.display_manager()
    emp1.display_employee()
    emp2.display_manager()
    emp2.display_employee()

```
``` 
output : 
manager name is abc
employee name is ram
manager name is def
employee name is sita
```
###  3.4 Multiple Inheritance:
Multiple level inheritance enables one derived class to inherit properties from more than one base class.
![](https://media.geeksforgeeks.org/wp-content/uploads/20200108144424/multiple-inheritance1.png)
```python
class Manage():
    def __init__(self,number):
        self.number=number
    def show_number(self):
        print(f'number of employee under manager is {self.number}')
class Employee():
    def __init__(self,salary):
        self.salary=salary
    def dispalye_salary(self):
        print(f'salary of employee is {self.salary}')
class Person(Manage,Employee): #multiple inheritance
    def __init__(self, number,salary,name,age,id):
        Manage.__init__(self,number)
        Employee.__init__(self,salary)
        self.name = name
        self.age=age
        self.e_id=id
    def show(self):
        print(f'name is {self.name} age is {self.age} employee id is {self.e_id}')
if __name__ == '__main__':
    person=Person(11,50000,'abc',25,1122)
    person.show()
    person.dispalye_salary()
    person.show_number()
```
```
output:
name is abc age is 25 employee id is 1122
salary of employee is 50000
number of employee under manager is 11
```

## 4  Polymorphism
It is a property of an object which allows it to take multiple forms.
### Polymorphism is of two types:

* Compile-time Polymorphism:
A compile-time polymorphism also called as static polymorphism which gets resolved during the compilation time of the program.
### 4.1 Method overloading
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
 
def func(obj):#Method Overloading
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
A run-time Polymorphism is also, called as dynamic polymorphism where it gets resolved into the run time.

### 4.2 method overriding
Example:
```python 
from abc import ABC,abstractmethod
from curses.ascii import EM
class Person(ABC):
    def emp_id(self):    #Abstraction
        pass
 
class Employee(Person):
    def emp_id(self):
        print("emp_id is 12345")
 
emp1 = Employee()
emp1.emp_id()

```
```
Output: no money, has money`

```
## 5. Encapsulation
Encapsulation in Python describes the concept of bundling data and methods within a single unit. So, when you create a class, it means you are implementing encapsulation.Also, encapsulation allows us to restrict accessing variables and methods directly and prevent accidental data modification by creating private data members and methods within a class.


![](https://media.geeksforgeeks.org/wp-content/uploads/20191013164254/encapsulation-in-python.png)
### Access Modifiers in Python
Encapsulation can be achieved by declaring the data members and methods of a class either as private or protected. But In Python, we don’t have direct access modifiers like public, private, and protected. We can achieve this by using single underscore and double underscores.

Access modifiers limit access to the variables and methods of a class. Python provides three types of access modifiers private, public, and protected.

* __Public Member__: Accessible anywhere from otside oclass.
* __Private Member__: Accessible within the class
* __Protected Member__: Accessible within the class and its sub-classes
Example
```python
class Employee:
    def __init__(self, name, salary,project):
        self.name = name  # public data member
        self._salary = salary # protected member
        self.__project = project # private member
    def show(self):
        print(f'employee name is {self.name}, salary is {self._salary}') 
        print(f'project name is {self.__project}')

# creating object of a class
emp = Employee('Jessa', 10000,'abc')
emp.show()
print(emp._salary) # name mangling
print(emp._Employee__project) # name mangling
```
```
Output:
employee name is Jessa, salary is 10000
project name is abc
10000
abc
```
## 6. Abstraction

Data abstraction in python and data encapsulation in python programming are related to each other. The main point that is necessary here to note is that data abstraction is only possible to achieve through encapsulation.Encapsulation means storing or placing data in a single place to make it easily readable and compact in one place. Whereas data abstraction in python programming means to hide internal functionalities that are performing on the application using codes and to show only essential information (class attributes).



## 7. Conclusion
Python being an object oriented programming language provides all the features of OOP such as inheritance, abstraction, polymorphism and encapsulation.
## 8. References
1. https://www.geeksforgeeks.org/python-oops-concepts
2. https://www.programiz.com/python-programming/object-oriented-programming
3. https://www.edureka.co/blog/object-oriented-programming-python
4. https://pynative.com/python-encapsulation
5. https://www.javatpoint.com/inheritance-in-python
