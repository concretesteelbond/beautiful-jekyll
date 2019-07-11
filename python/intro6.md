---
layout: page
title: Python Intro
subtitle: Practice makes Expert
---
All the IPython Notebooks in this lecture series are available at https://github.com/rajathkumarmp/Python-Lectures

#Functions

Most of the times, In a algorithm the statements keep repeating and it will be a tedious job to execute the same statements again and again and will consume a lot of memory and is not efficient. Enter Functions.

This is the basic syntax of a function

def funcname(arg1, arg2,... argN):

    ''' Document String'''

    statements


    return <value>

Read the above syntax as, A function by name "funcname" is defined, which accepts arguements "arg1,arg2,....argN". The function is documented and it is '''Document String'''. The function after executing the statements returns a "value".


```python
print "Hey Rajath!"
print "Rajath, How do you do?"
```

    Hey Rajath!
    Rajath, How do you do?


Instead of writing the above two statements every single time it can be replaced by defining a function which would do the job in just one line.

Defining a function firstfunc().


```python
def firstfunc():
    print "Hey Rajath!"
    print "Rajath, How do you do?"   
```


```python
firstfunc()
```

    Hey Rajath!
    Rajath, How do you do?


**firstfunc()** every time just prints the message to a single person. We can make our function **firstfunc()** to accept arguements which will store the name and then prints respective to that accepted name. To do so, add a argument within the function as shown.


```python
def firstfunc(username):
    print "Hey", username + '!'
    print username + ',' ,"How do you do?"
```


```python
name1 = raw_input('Please enter your name : ')
```

    Please enter your name : Guido


The name "Guido" is actually stored in name1. So we pass this variable to the function **firstfunc()** as the variable username because that is the variable that is defined for this function. i.e name1 is passed as username.


```python
firstfunc(name1)
```

    Hey Guido!
    Guido, How do you do?


Let us simplify this even further by defining another function **secondfunc()** which accepts the name and stores it inside a variable and then calls the **firstfunc()** from inside the function itself.


```python
def firstfunc(username):
    print "Hey", username + '!'
    print username + ',' ,"How do you do?"
def secondfunc():
    name = raw_input("Please enter your name : ")
    firstfunc(name)
```


```python
secondfunc()
```

    Please enter your name : karthik
    Hey karthik!
    karthik, How do you do?


##Return Statement

When the function results in some value and that value has to be stored in a variable or needs to be sent back or returned for further operation to the main algorithm, return statement is used.


```python
def times(x,y):
    z = x*y
    return z
```

The above defined **times( )** function accepts two arguements and return the variable z which contains the result of the product of the two arguements


```python
c = times(4,5)
print c
```

    20


The z value is stored in variable c and can be used for further operations.

Instead of declaring another variable the entire statement itself can be used in the return statement as shown.


```python
def times(x,y):
    '''This multiplies the two input arguments'''
    return x*y
```


```python
c = times(4,5)
print c
```

    20


Since the **times( )** is now defined, we can document it as shown above. This document is returned whenever **times( )** function is called under **help( )** function.


```python
help(times)
```

    Help on function times in module __main__:

    times(x, y)
        This multiplies the two input arguments



Multiple variable can also be returned, But keep in mind the order.


```python
eglist = [10,50,30,12,6,8,100]
```


```python
def egfunc(eglist):
    highest = max(eglist)
    lowest = min(eglist)
    first = eglist[0]
    last = eglist[-1]
    return highest,lowest,first,last
```

If the function is just called without any variable for it to be assigned to, the result is returned inside a tuple. But if the variables are mentioned then the result is assigned to the variable in a particular order which is declared in the return statement.


```python
egfunc(eglist)
```




    (100, 6, 10, 100)




```python
a,b,c,d = egfunc(eglist)
print ' a =',a,'\n b =',b,'\n c =',c,'\n d =',d
```

     a = 100
     b = 6
     c = 10
     d = 100


##Implicit arguments

When an argument of a function is common in majority of the cases or it is "implicit" this concept is used.


```python
def implicitadd(x,y=3):
    return x+y
```

**implicitadd( )** is a function accepts two arguments but most of the times the first argument needs to be added just by 3. Hence the second argument is assigned the value 3. Here the second argument is implicit.

Now if the second argument is not defined when calling the **implicitadd( )** function then it considered as 3.


```python
implicitadd(4)
```




    7



But if the second argument is specified then this value overrides the implicit value assigned to the argument


```python
implicitadd(4,4)
```




    8



##Any number of arguments

If the number of arguments that is to be accepted by a function is not known then a asterisk symbol is used before the argument.


```python
def add_n(*args):
    res = 0
    reslist = []
    for i in args:
        reslist.append(i)
    print reslist
    return sum(reslist)
```

The above function accepts any number of arguments, defines a list and appends all the arguments into that list and return the sum of all the arguments.


```python
add_n(1,2,3,4,5)
```

    [1, 2, 3, 4, 5]





    15




```python
add_n(1,2,3)
```

    [1, 2, 3]





    6



##Global and Local Variables

Whatever variable is declared inside a function is local variable and outside the function in global variable.


```python
eg1 = [1,2,3,4,5]
```

In the below function we are appending a element to the declared list inside the function. eg2 variable declared inside the function is a local variable.


```python
def egfunc1():
    def thirdfunc(arg1):
        eg2 = arg1[:]
        eg2.append(6)
        print "This is happening inside the function :", eg2
    print "This is happening before the function is called : ", eg1
    thirdfunc(eg1)
    print "This is happening outside the function :", eg1   
    print "Accessing a variable declared inside the function from outside :" , eg2
```


```python
egfunc1()
```

    This is happening before the function is called :  [1, 2, 3, 4, 5]
    This is happening inside the function : [1, 2, 3, 4, 5, 6]
    This is happening outside the function : [1, 2, 3, 4, 5]
    Accessing a variable declared inside the function from outside :


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-26-949117e1ddc5> in <module>()
    ----> 1 egfunc1()


    <ipython-input-25-0da329480da9> in egfunc1()
          7     thirdfunc(eg1)
          8     print "This is happening outside the function :", eg1
    ----> 9     print "Accessing a variable declared inside the function from outside :" , eg2


    NameError: global name 'eg2' is not defined


If a **global** variable is defined as shown in the example below then that variable can be called from anywhere.


```python
eg3 = [1,2,3,4,5]
```





```python
def egfunc1():
    def thirdfunc(arg1):
        global eg2
        eg2 = arg1[:]
        eg2.append(6)
        print "This is happening inside the function :", eg2
    print "This is happening before the function is called : ", eg1
    thirdfunc(eg1)
    print "This is happening outside the function :", eg1   
    print "Accessing a variable declared inside the function from outside :" , eg2
```


```python
egfunc1()
```

    This is happening before the function is called :  [1, 2, 3, 4, 5]
    This is happening inside the function : [1, 2, 3, 4, 5, 6]
    This is happening outside the function : [1, 2, 3, 4, 5]
    Accessing a variable declared inside the function from outside : [1, 2, 3, 4, 5, 6]


##Lambda Functions

These are small functions which are not defined with any name and carry a single expression whose result is returned. Lambda functions comes very handy when operating with lists. These function are defined by the keyword **lambda** followed by the variables, a colon and the respective expression.


```python
z = lambda x: x * x
```


```python
z(8)
```




    64



###map

**map( )** function basically executes the function that is defined to each of the list's element separately.


```python
list1 = [1,2,3,4,5,6,7,8,9]
```


```python
eg = map(lambda x:x+2, list1)
print eg
```

    [3, 4, 5, 6, 7, 8, 9, 10, 11]


You can also add two lists.


```python
list2 = [9,8,7,6,5,4,3,2,1]
```


```python
eg2 = map(lambda x,y:x+y, list1,list2)
print eg2
```

    [10, 10, 10, 10, 10, 10, 10, 10, 10]


Not only lambda function but also other built in functions can also be used.


```python
eg3 = map(str,eg2)
print eg3
```

    ['10', '10', '10', '10', '10', '10', '10', '10', '10']


###filter

**filter( )** function is used to filter out the values in a list. Note that **filter()** function returns the result in a new list.


```python
list1 = [1,2,3,4,5,6,7,8,9]
```

To get the elements which are less than 5,


```python
filter(lambda x:x<5,list1)
```




    [1, 2, 3, 4]



Notice what happens when **map()** is used.


```python
map(lambda x:x<5, list1)
```




    [True, True, True, True, False, False, False, False, False]



We can conclude that, whatever is returned true in **map( )** function that particular element is returned when **filter( )** function is used.


```python
filter(lambda x:x%4==0,list1)
```




    [4, 8]
