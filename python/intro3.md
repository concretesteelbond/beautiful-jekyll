---
layout: page
title: Python Intro
subtitle: Practice makes Expert
---
All the IPython Notebooks in this lecture series are available at https://github.com/rajathkumarmp/Python-Lectures

#Data Structures

In simple terms, It is the the collection or group of data in a particular structure.

##Lists

Lists are the most commonly used data structure. Think of it as a sequence of data that is enclosed in square brackets and data are separated by a comma. Each of these data can be accessed by calling it's index value.

Lists are declared by just equating a variable to '[ ]' or list.


```python
a = []
```


```python
print type(a)
```

    <type 'list'>


One can directly assign the sequence of data to a list x as shown.


```python
x = ['apple', 'orange']
```

### Indexing

In python, Indexing starts from 0. Thus now the list x, which has two elements will have apple at 0 index and orange at 1 index.


```python
x[0]
```




    'apple'



Indexing can also be done in reverse order. That is the last element can be accessed first. Here, indexing starts from -1. Thus index value -1 will be orange and index -2 will be apple.


```python
x[-1]
```




    'orange'



As you might have already guessed, x[0] = x[-2], x[1] = x[-1]. This concept can be extended towards lists with more many elements.


```python
y = ['carrot','potato']
```

Here we have declared two lists x and y each containing its own data. Now, these two lists can again be put into another list say z which will have it's data as two lists. This list inside a list is called as nested lists and is how an array would be declared which we will see later.


```python
z  = [x,y]
print z
```

    [['apple', 'orange'], ['carrot', 'potato']]


Indexing in nested lists can be quite confusing if you do not understand how indexing works in python. So let us break it down and then arrive at a conclusion.

Let us access the data 'apple' in the above nested list.
First, at index 0 there is a list ['apple','orange'] and at index 1 there is another list ['carrot','potato']. Hence z[0] should give us the first list which contains 'apple'.


```python
z1 = z[0]
print z1
```

    ['apple', 'orange']


Now observe that z1 is not at all a nested list thus to access 'apple', z1 should be indexed at 0.


```python
z1[0]
```




    'apple'



Instead of doing the above, In python, you can access 'apple' by just writing the index values each time side by side.


```python
z[0][0]
```




    'apple'



If there was a list inside a list inside a list then you can access the innermost value by executing z[ ][ ][ ].

### Slicing

Indexing was only limited to accessing a single element, Slicing on the other hand is accessing a sequence of data inside the list. In other words "slicing" the list.

Slicing is done by defining the index values of the first element and the last element from the parent list that is required in the sliced list. It is written as parentlist[ a : b ] where a,b are the index values from the parent list. If a or b is not defined then the index value is considered to be the first value for a if a is not defined and the last value for b when b is not defined.


```python
num = [0,1,2,3,4,5,6,7,8,9]
```


```python
print num[0:4]
print num[4:]
```

    [0, 1, 2, 3]
    [4, 5, 6, 7, 8, 9]


You can also slice a parent list with a fixed length or step length.


```python
num[:9:3]
```




    [0, 3, 6]



###Built in List Functions

To find the length of the list or the number of elements in a list, **len( )** is used.


```python
len(num)
```




    10



If the list consists of all integer elements then **min( )** and **max( )** gives the minimum and maximum value in the list.


```python
min(num)
```




    0




```python
max(num)
```




    9



Lists can be concatenated by adding, '+' them. The resultant list will contain all the elements of the lists that were added. The resultant list will not be a nested list.


```python
[1,2,3] + [5,4,7]
```




    [1, 2, 3, 5, 4, 7]



There might arise a requirement where you might need to check if a particular element is there in a predefined list. Consider the below list.


```python
names = ['Earth','Air','Fire','Water']
```

To check if 'Fire' and 'Rajath' is present in the list names. A conventional approach would be to use a for loop and iterate over the list and use the if condition. But in python you can use 'a in b' concept which would return 'True' if a is present in b and 'False' if not.


```python
'Fire' in names
```




    True




```python
'Rajath' in names
```




    False



In a list with elements as string, **max( )** and **min( )** is applicable. **max( )** would return a string element whose ASCII value is the highest and the lowest when **min( )** is used. Note that only the first index of each element is considered each time and if they value is the same then second index considered so on and so forth.


```python
mlist = ['bzaa','ds','nc','az','z','klm']
```


```python
print max(mlist)
print min(mlist)
```

    z
    az


Here the first index of each element is considered and thus z has the highest ASCII value thus it is returned and minimum ASCII is a. But what if numbers are declared as strings?


```python
nlist = ['1','94','93','1000']
```


```python
print max(nlist)
print min(nlist)
```

    94
    1


Even if the numbers are declared in a string the first index of each element is considered and the maximum and minimum values are returned accordingly.

But if you want to find the **max( )** string element based on the length of the string then another parameter 'key=len' is declared inside the **max( )** and **min( )** function.


```python
print max(names, key=len)
print min(names, key=len)
```

    Earth
    Air


But even 'Water' has length 5. **max()** or **min()** function returns the first element when there are two or more elements with the same length.

Any other built in function can be used or lambda function (will be discussed later) in place of len.

A string can be converted into a list by using the **list()** function.


```python
list('hello')
```




    ['h', 'e', 'l', 'l', 'o']



**append( )** is used to add a element at the end of the list.


```python
lst = [1,1,4,8,7]
```


```python
lst.append(1)
print lst
```

    [1, 1, 4, 8, 7, 1]


**count( )** is used to count the number of a particular element that is present in the list.


```python
lst.count(1)
```




    3



**append( )** function can also be used to add a entire list at the end. Observe that the resultant list becomes a nested list.


```python
lst1 = [5,4,2,8]
```


```python
lst.append(lst1)
print lst
```

    [1, 1, 4, 8, 7, 1, [5, 4, 2, 8]]


But if nested list is not what is desired then **extend( )** function can be used.


```python
lst.extend(lst1)
print lst
```

    [1, 1, 4, 8, 7, 1, [5, 4, 2, 8], 5, 4, 2, 8]


**index( )** is used to find the index value of a particular element. Note that if there are multiple elements of the same value then the first index value of that element is returned.


```python
lst.index(1)
```




    0



**insert(x,y)** is used to insert a element y at a specified index value x. **append( )** function made it only possible to insert at the end.


```python
lst.insert(5, 'name')
print lst
```

    [1, 1, 4, 8, 7, 'name', 1, [5, 4, 2, 8], 5, 4, 2, 8]


**insert(x,y)** inserts but does not replace element. If you want to replace the element with another element you simply assign the value to that particular index.


```python
lst[5] = 'Python'
print lst
```

    [1, 1, 4, 8, 7, 'Python', 1, [5, 4, 2, 8], 5, 4, 2, 8]


**pop( )** function return the last element in the list. This is similar to the operation of a stack. Hence it wouldn't be wrong to tell that lists can be used as a stack.


```python
lst.pop()
```




    8



Index value can be specified to pop a ceratin element corresponding to that index value.


```python
lst.pop(0)
```




    1



**pop( )** is used to remove element based on it's index value which can be assigned to a variable. One can also remove element by specifying the element itself using the **remove( )** function.


```python
lst.remove('Python')
print lst
```

    [1, 4, 8, 7, 1, [5, 4, 2, 8], 5, 4, 2]


Alternative to **remove** function but with using index value is **del**


```python
del lst[1]
print lst
```

    [1, 8, 7, 1, [5, 4, 2, 8], 5, 4, 2]


The entire elements present in the list can be reversed by using the **reverse()** function.


```python
lst.reverse()
print lst
```

    [2, 4, 5, [5, 4, 2, 8], 1, 7, 8, 1]


Note that the nested list [5,4,2,8] is treated as a single element of the parent list lst. Thus the elements inside the nested list is not reversed.

Python offers built in operation **sort( )** to arrange the elements in ascending order.


```python
lst.sort()
print lst
```

    [1, 1, 2, 4, 5, 7, 8, [5, 4, 2, 8]]


For descending order, By default the reverse condition will be False for reverse. Hence changing it to True would arrange the elements in descending order.


```python
lst.sort(reverse=True)
print lst
```

    [[5, 4, 2, 8], 8, 7, 5, 4, 2, 1, 1]


Similarly for lists containing string elements, **sort( )** would sort the elements based on it's ASCII value in ascending and by specifying reverse=True in descending.


```python
names.sort()
print names
names.sort(reverse=True)
print names
```

    ['Air', 'Earth', 'Fire', 'Water']
    ['Water', 'Fire', 'Earth', 'Air']


To sort based on length key=len should be specified as shown.


```python
names.sort(key=len)
print names
names.sort(key=len,reverse=True)
print names
```

    ['Air', 'Fire', 'Water', 'Earth']
    ['Water', 'Earth', 'Fire', 'Air']


### Copying a list

Most of the new python programmers commit this mistake. Consider the following,


```python
lista= [2,1,4,3]
```


```python
listb = lista
print listb
```

    [2, 1, 4, 3]


Here, We have declared a list, lista = [2,1,4,3]. This list is copied to listb by assigning it's value and it get's copied as seen. Now we perform some random operations on lista.


```python
lista.pop()
print lista
lista.append(9)
print lista
```

    [2, 1, 4]
    [2, 1, 4, 9]



```python
print listb
```

    [2, 1, 4, 9]


listb has also changed though no operation has been performed on it. This is because you have assigned the same memory space of lista to listb. So how do fix this?

If you recall, in slicing we had seen that parentlist[a:b] returns a list from parent list with start index a and end index b and if a and b is not mentioned then by default it considers the first and last element. We use the same concept here. By doing so, we are assigning the data of lista to listb as a variable.


```python
lista = [2,1,4,3]
```


```python
listb = lista[:]
print listb
```

    [2, 1, 4, 3]



```python
lista.pop()
print lista
lista.append(9)
print lista
```

    [2, 1, 4]
    [2, 1, 4, 9]



```python
print listb
```

    [2, 1, 4, 3]


##Tuples

Tuples are similar to lists but only big difference is the elements inside a list can be changed but in tuple it cannot be changed. Think of tuples as something which has to be True for a particular something and cannot be True for no other values. For better understanding, Recall **divmod()** function.


```python
xyz = divmod(10,3)
print xyz
print type(xyz)
```

    (3, 1)
    <type 'tuple'>


Here the quotient has to be 3 and the remainder has to be 1. These values cannot be changed whatsoever when 10 is divided by 3. Hence divmod returns these values in a tuple.

To define a tuple, A variable is assigned to paranthesis ( ) or tuple( ).


```python
tup = ()
tup2 = tuple()
```

If you want to directly declare a tuple it can be done by using a comma at the end of the data.


```python
27,
```




    (27,)



27 when multiplied by 2 yields 54, But when multiplied with a tuple the data is repeated twice.


```python
2*(27,)
```




    (27, 27)



Values can be assigned while declaring a tuple. It takes a list as input and converts it into a tuple or it takes a string and converts it into a tuple.


```python
tup3 = tuple([1,2,3])
print tup3
tup4 = tuple('Hello')
print tup4
```

    (1, 2, 3)
    ('H', 'e', 'l', 'l', 'o')


It follows the same indexing and slicing as Lists.


```python
print tup3[1]
tup5 = tup4[:3]
print tup5
```

    2
    ('H', 'e', 'l')


### Mapping one tuple to another


```python
(a,b,c)= ('alpha','beta','gamma')
```


```python
print a,b,c
```

    alpha beta gamma



```python
d = tuple('RajathKumarMP')
print d
```

    ('R', 'a', 'j', 'a', 't', 'h', 'K', 'u', 'm', 'a', 'r', 'M', 'P')


### Built In Tuple functions

**count()** function counts the number of specified element that is present in the tuple.


```python
d.count('a')
```




    3



**index()** function returns the index of the specified element. If the elements are more than one then the index of the first element of that specified element is returned


```python
d.index('a')
```




    1



##Sets

Sets are mainly used to eliminate repeated numbers in a sequence/list. It is also used to perform some standard set operations.

Sets are declared as set() which will initialize a empty set. Also set([sequence]) can be executed to declare a set with elements


```python
set1 = set()
print type(set1)
```

    <type 'set'>



```python
set0 = set([1,2,2,3,3,4])
print set0
```

    set([1, 2, 3, 4])


elements 2,3 which are repeated twice are seen only once. Thus in a set each element is distinct.

###Built-in Functions


```python
set1 = set([1,2,3])
```


```python
set2 = set([2,3,4,5])
```

**union( )** function returns a set which contains all the elements of both the sets without repition.


```python
set1.union(set2)
```




    {1, 2, 3, 4, 5}



**add( )** will add a particular element into the set. Note that the index of the newly added element is arbitrary and can be placed anywhere not neccessarily in the end.


```python
set1.add(0)
set1
```




    {0, 1, 2, 3}



**intersection( )** function outputs a set which contains all the elements that are in both sets.


```python
set1.intersection(set2)
```




    {2, 3}



**difference( )** function ouptuts a set which contains elements that are in set1 and not in set2.


```python
set1.difference(set2)
```




    {0, 1}



**symmetric_difference( )** function ouputs a function which contains elements that are in one of the sets.


```python
set2.symmetric_difference(set1)
```




    {0, 1, 4, 5}



**issubset( ), isdisjoint( ), issuperset( )** is used to check if the set1/set2 is a subset, disjoint or superset of set2/set1 respectively.


```python
set1.issubset(set2)
```




    False




```python
set2.isdisjoint(set1)
```




    False




```python
set2.issuperset(set1)
```




    False



**pop( )** is used to remove an arbitrary element in the set


```python
set1.pop()
print set1
```

    set([1, 2, 3])


**remove( )** function deletes the specified element from the set.


```python
set1.remove(2)
set1
```




    {1, 3}



**clear( )** is used to clear all the elements and make that set an empty set.


```python
set1.clear()
set1
```




    set()
