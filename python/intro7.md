---
layout: page
title: Python Intro
subtitle: Practice makes Expert
---
All the IPython Notebooks in this lecture series are available at https://github.com/rajathkumarmp/Python-Lectures

#Classes

Variables, Lists, Dictionaries etc in python is a object. Without getting into the theory part of Object Oriented Programming, explanation of the concepts will be done along this tutorial.

A class is declared as follows

class class_name:

    Functions


```python
class FirstClass:
    pass
```

**pass** in python means do nothing.

Above, a class object named "FirstClass" is declared now consider a "egclass" which has all the characteristics of "FirstClass". So all you have to do is, equate the "egclass" to "FirstClass". In python jargon this is called as creating an instance. "egclass" is the instance of "FirstClass"


```python
egclass = FirstClass()
```


```python
type(egclass)
```




    instance




```python
type(FirstClass)
```




    classobj



Now let us add some "functionality" to the class. So that our "FirstClass" is defined in a better way. A function inside a class is called as a "Method" of that class

Most of the classes will have a function named "\_\_init\_\_". These are called as magic methods. In this method you basically initialize the variables of that class or any other initial algorithms which is applicable to all methods is specified in this method. A variable inside a class is called an attribute.

These helps simplify the process of initializing a instance. For example,

Without the use of magic method or \_\_init\_\_ which is otherwise called as constructors. One had to define a **init( )** method and call the **init( )** function.


```python
eg0 = FirstClass()
eg0.init()
```

But when the constructor is defined the \_\_init\_\_ is called thus intializing the instance created.

We will make our "FirstClass" to accept two variables name and symbol.

I will be explaining about the "self" in a while.


```python
class FirstClass:
    def __init__(self,name,symbol):
        self.name = name
        self.symbol = symbol
```

Now that we have defined a function and added the \_\_init\_\_ method. We can create a instance of FirstClass which now accepts two arguments.


```python
eg1 = FirstClass('one',1)
eg2 = FirstClass('two',2)
```


```python
print eg1.name, eg1.symbol
print eg2.name, eg2.symbol
```

    one 1
    two 2


**dir( )** function comes very handy in looking into what the class contains and what all method it offers


```python
dir(FirstClass)
```




    ['__doc__', '__init__', '__module__']



**dir( )** of an instance also shows it's defined attributes.


```python
dir(eg1)
```




    ['__doc__', '__init__', '__module__', 'name', 'symbol']



Changing the FirstClass function a bit,


```python
class FirstClass:
    def __init__(self,name,symbol):
        self.n = name
        self.s = symbol
```

Changing self.name and self.symbol to self.n and self.s respectively will yield,


```python
eg1 = FirstClass('one',1)
eg2 = FirstClass('two',2)
```


```python
print eg1.name, eg1.symbol
print eg2.name, eg2.symbol
```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    <ipython-input-13-3717d682d1cf> in <module>()
    ----> 1 print eg1.name, eg1.symbol
          2 print eg2.name, eg2.symbol


    AttributeError: FirstClass instance has no attribute 'name'


AttributeError, Remember variables are nothing but attributes inside a class? So this means we have not given the correct attribute for the instance.


```python
dir(eg1)
```




    ['__doc__', '__init__', '__module__', 'n', 's']




```python
print eg1.n, eg1.s
print eg2.n, eg2.s
```

    one 1
    two 2


So now we have solved the error. Now let us compare the two examples that we saw.

When I declared self.name and self.symbol, there was no attribute error for eg1.name and eg1.symbol and when I declared self.n and self.s, there was no attribute error for eg1.n and eg1.s

From the above we can conclude that self is nothing but the instance itself.

Remember, self is not predefined it is userdefined. You can make use of anything you are comfortable with. But it has become a common practice to use self.


```python
class FirstClass:
    def __init__(asdf1234,name,symbol):
        asdf1234.n = name
        asdf1234.s = symbol
```


```python
eg1 = FirstClass('one',1)
eg2 = FirstClass('two',2)
```


```python
print eg1.n, eg1.s
print eg2.n, eg2.s
```

    one 1
    two 2


Since eg1 and eg2 are instances of FirstClass it need not necessarily be limited to FirstClass itself. It might extend itself by declaring other attributes without having the attribute to be declared inside the FirstClass.


```python
eg1.cube = 1
eg2.cube = 8
```


```python
dir(eg1)
```




    ['__doc__', '__init__', '__module__', 'cube', 'n', 's']



Just like global and local variables as we saw earlier, even classes have it's own types of variables.

Class Attribute : attributes defined outside the method and is applicable to all the instances.

Instance Attribute : attributes defined inside a method and is applicable to only that method and is unique to each instance.


```python
class FirstClass:
    test = 'test'
    def __init__(self,name,symbol):
        self.name = name
        self.symbol = symbol
```

Here test is a class attribute and name is a instance attribute.


```python
eg3 = FirstClass('Three',3)
```


```python
print eg3.test, eg3.name
```

    test Three


Let us add some more methods to FirstClass.


```python
class FirstClass:
    def __init__(self,name,symbol):
        self.name = name
        self.symbol = symbol
    def square(self):
        return self.symbol * self.symbol
    def cube(self):
        return self.symbol * self.symbol * self.symbol
    def multiply(self, x):
        return self.symbol * x
```


```python
eg4 = FirstClass('Five',5)
```


```python
print eg4.square()
print eg4.cube()
```

    25
    125



```python
eg4.multiply(2)
```




    10



The above can also be written as,


```python
FirstClass.multiply(eg4,2)
```




    10



##Inheritance

There might be cases where a new class would have all the previous characteristics of an already defined class. So the new class can "inherit" the previous class and add it's own methods to it. This is called as inheritance.

Consider class SoftwareEngineer which has a method salary.


```python
class SoftwareEngineer:
    def __init__(self,name,age):
        self.name = name
        self.age = age
    def salary(self, value):
        self.money = value
        print self.name,"earns",self.money
```


```python
a = SoftwareEngineer('Kartik',26)
```


```python
a.salary(40000)
```

    Kartik earns 40000



```python
dir(SoftwareEngineer)
```




    ['__doc__', '__init__', '__module__', 'salary']



Now consider another class Artist which tells us about the amount of money an artist earns and his artform.


```python
class Artist:
    def __init__(self,name,age):
        self.name = name
        self.age = age
    def money(self,value):
        self.money = value
        print self.name,"earns",self.money
    def artform(self, job):
        self.job = job
        print self.name,"is a", self.job
```


```python
b = Artist('Nitin',20)
```


```python
b.money(50000)
b.artform('Musician')
```

    Nitin earns 50000
    Nitin is a Musician



```python
dir(Artist)
```




    ['__doc__', '__init__', '__module__', 'artform', 'money']



money method and salary method are the same. So we can generalize the method to salary and inherit the SoftwareEngineer class to Artist class. Now the artist class becomes,


```python
class Artist(SoftwareEngineer):
    def artform(self, job):
        self.job = job
        print self.name,"is a", self.job
```


```python
c = Artist('Nishanth',21)
```


```python
dir(Artist)
```




    ['__doc__', '__init__', '__module__', 'artform', 'salary']




```python
c.salary(60000)
c.artform('Dancer')
```

    Nishanth earns 60000
    Nishanth is a Dancer


Suppose say while inheriting a particular method is not suitable for the new class. One can override this method by defining again that method with the same name inside the new class.


```python
class Artist(SoftwareEngineer):
    def artform(self, job):
        self.job = job
        print self.name,"is a", self.job
    def salary(self, value):
        self.money = value
        print self.name,"earns",self.money
        print "I am overriding the SoftwareEngineer class's salary method"
```


```python
c = Artist('Nishanth',21)
```


```python
c.salary(60000)
c.artform('Dancer')
```

    Nishanth earns 60000
    I am overriding the SoftwareEngineer class's salary method
    Nishanth is a Dancer


If not sure how many times methods will be called it will become difficult to declare so many variables to carry each result hence it is better to declare a list and append the result.


```python
class emptylist:
    def __init__(self):
        self.data = []
    def one(self,x):
        self.data.append(x)
    def two(self, x ):
        self.data.append(x**2)
    def three(self, x):
        self.data.append(x**3)
```


```python
xc = emptylist()
```


```python
xc.one(1)
print xc.data
```

    [1]


Since xc.data is a list direct list operations can also be performed.


```python
xc.data.append(8)
print xc.data
```

    [1, 8]



```python
xc.two(3)
print xc.data
```

    [1, 8, 9]


If the number of input arguments varies from instance to instance asterisk can be used as shown.


```python
class NotSure:
    def __init__(self, *args):
        self.data = ''.join(list(args))
```


```python
yz = NotSure('I', 'Do' , 'Not', 'Know', 'What', 'To','Type')
```


```python
yz.data
```




    'IDoNotKnowWhatToType'



#Where to go from here?

Practice alone can help you get the hang of python. Give your self problem statements and solve them. You can also sign up to any competitive coding platform for problem statements. The more you code the more you discover and the more you start appreciating the language.


Now that you have been introduced to python, You can try out the different python libraries in the field of your interest. I highly recommend you to check out this curated list of Python frameworks, libraries and software http://awesome-python.com


The official python documentation : https://docs.python.org/2/


You can also check out Python practice programs written by my friend, Kartik Kannapur. Github Repo : https://github.com/rajathkumarmp/Python-Lectures


Enjoy solving problem statements because life is short, you need python!


Peace.


Rajath Kumar M.P ( rajathkumar dot exe at gmail dot com)
