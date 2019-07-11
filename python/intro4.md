---
layout: page
title: Python Intro
subtitle: Practice makes Expert
---
All the IPython Notebooks in this lecture series are available at https://github.com/rajathkumarmp/Python-Lectures

##Strings

Strings are ordered text based data which are represented by enclosing the same in single/double/triple quotes.


```python
String0 = 'Taj Mahal is beautiful'
String1 = "Taj Mahal is beautiful"
String2 = '''Taj Mahal
is
beautiful'''
```


```python
print String0 , type(String0)
print String1, type(String1)
print String2, type(String2)
```

    Taj Mahal is beautiful <type 'str'>
    Taj Mahal is beautiful <type 'str'>
    Taj Mahal
    is
    beautiful <type 'str'>


String Indexing and Slicing are similar to Lists which was explained in detail earlier.


```python
print String0[4]
print String0[4:]
```

    M
    Mahal is beautiful


###Built-in Functions

**find( )** function returns the index value of the given data that is to found in the string. If it is not found it returns **-1**. Remember to not confuse the returned -1 for reverse indexing value.


```python
print String0.find('al')
print String0.find('am')
```

    7
    -1


The index value returned is the index of the first element in the input data.


```python
print String0[7]
```

    a


One can also input **find( )** function between which index values it has to search.


```python
print String0.find('j',1)
print String0.find('j',1,3)
```

    2
    2


**capitalize( )** is used to capitalize the first element in the string.


```python
String3 = 'observe the first letter in this sentence.'
print String3.capitalize()
```

    Observe the first letter in this sentence.


**center( )** is used to center align the string by specifying the field width.


```python
String0.center(70)
```




    '                        Taj Mahal is beautiful                        '



One can also fill the left out spaces with any other character.


```python
String0.center(70,'-')
```




    '------------------------Taj Mahal is beautiful------------------------'



**zfill( )** is used for zero padding by specifying the field width.


```python
String0.zfill(30)
```




    '00000000Taj Mahal is beautiful'



**expandtabs( )** allows you to change the spacing of the tab character. '\t' which is by default set to 8 spaces.


```python
s = 'h\te\tl\tl\to'
print s
print s.expandtabs(1)
print s.expandtabs()
```

    h	e	l	l	o
    h e l l o
    h       e       l       l       o


**index( )** works the same way as **find( )** function the only difference is find returns '-1' when the input element is not found in the string but **index( )** function throws a ValueError


```python
print String0.index('Taj')
print String0.index('Mahal',0)
print String0.index('Mahal',10,20)
```

    0
    4



    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-12-6062e7a32deb> in <module>()
          1 print String0.index('Taj')
          2 print String0.index('Mahal',0)
    ----> 3 print String0.index('Mahal',10,20)


    ValueError: substring not found


**endswith( )** function is used to check if the given string ends with the particular char which is given as input.


```python
print String0.endswith('y')
```

    False


The start and stop index values can also be specified.


```python
print String0.endswith('l',0)
print String0.endswith('M',0,5)
```

    True
    True


**count( )** function counts the number of char in the given string. The start and the stop index can also be specified or left blank. (These are Implicit arguments which will be dealt in functions)


```python
print String0.count('a',0)
print String0.count('a',5,10)
```

    4
    2


**join( )** function is used add a char in between the elements of the input string.


```python
'a'.join('*_-')
```




    '*a_a-'



'*_-' is the input string and char 'a' is added in between each element

**join( )** function can also be used to convert a list into a string.


```python
a = list(String0)
print a
b = ''.join(a)
print b
```

    ['T', 'a', 'j', ' ', 'M', 'a', 'h', 'a', 'l', ' ', 'i', 's', ' ', 'b', 'e', 'a', 'u', 't', 'i', 'f', 'u', 'l']
    Taj Mahal is beautiful


Before converting it into a string **join( )** function can be used to insert any char in between the list elements.


```python
c = '/'.join(a)[18:]
print c
```

     /i/s/ /b/e/a/u/t/i/f/u/l


**split( )** function is used to convert a string back to a list. Think of it as the opposite of the **join()** function.


```python
d = c.split('/')
print d
```

    [' ', 'i', 's', ' ', 'b', 'e', 'a', 'u', 't', 'i', 'f', 'u', 'l']


In **split( )** function one can also specify the number of times you want to split the string or the number of elements the new returned list should conatin. The number of elements is always one more than the specified number this is because it is split the number of times specified.


```python
e = c.split('/',3)
print e
print len(e)
```

    [' ', 'i', 's', ' /b/e/a/u/t/i/f/u/l']
    4


**lower( )** converts any capital letter to small letter.


```python
print String0
print String0.lower()
```

    Taj Mahal is beautiful
    taj mahal is beautiful


**upper( )** converts any small letter to capital letter.


```python
String0.upper()
```




    'TAJ MAHAL IS BEAUTIFUL'



**replace( )** function replaces the element with another element.


```python
String0.replace('Taj Mahal','Bengaluru')
```




    'Bengaluru is beautiful'



**strip( )** function is used to delete elements from the right end and the left end which is not required.


```python
f = '    hello      '
```

If no char is specified then it will delete all the spaces that is present in the right and left hand side of the data.


```python
f.strip()
```




    'hello'



**strip( )** function, when a char is specified then it deletes that char if it is present in the two ends of the specified string.


```python
f = '   ***----hello---*******     '
```


```python
f.strip('*')
```




    '   ***----hello---*******     '



The asterisk had to be deleted but is not. This is because there is a space in both the right and left hand side. So in strip function. The characters need to be inputted in the specific order in which they are present.


```python
print f.strip(' *')
print f.strip(' *-')
```

    ----hello---
    hello


**lstrip( )** and **rstrip( )** function have the same functionality as strip function but the only difference is **lstrip( )** deletes only towards the left side and **rstrip( )** towards the right.


```python
print f.lstrip(' *')
print f.rstrip(' *')
```

    ----hello---*******     
       ***----hello---


##Dictionaries

Dictionaries are more used like a database because here you can index a particular sequence with your user defined string.

To define a dictionary, equate a variable to { } or dict()


```python
d0 = {}
d1 = dict()
print type(d0), type(d1)
```

    <type 'dict'> <type 'dict'>


Dictionary works somewhat like a list but with an added capability of assigning it's own index style.


```python
d0['One'] = 1
d0['OneTwo'] = 12
print d0
```

    {'OneTwo': 12, 'One': 1}


That is how a dictionary looks like. Now you are able to access '1' by the index value set at 'One'


```python
print d0['One']
```

    1


Two lists which are related can be merged to form a dictionary.


```python
names = ['One', 'Two', 'Three', 'Four', 'Five']
numbers = [1, 2, 3, 4, 5]
```

**zip( )** function is used to combine two lists


```python
d2 = zip(names,numbers)
print d2
```

    [('One', 1), ('Two', 2), ('Three', 3), ('Four', 4), ('Five', 5)]


The two lists are combined to form a single list and each elements are clubbed with their respective elements from the other list inside a tuple. Tuples because that is what is assigned and the value should not change.

Further, To convert the above into a dictionary. **dict( )** function is used.


```python
a1 = dict(d2)
print a1
```

    {'Four': 4, 'Five': 5, 'Three': 3, 'Two': 2, 'One': 1}


###Built-in Functions

**clear( )** function is used to erase the entire database that was created.


```python
a1.clear()
print a1
```

    {}


Dictionary can also be built using loops.


```python
for i in range(len(names)):
    a1[names[i]] = numbers[i]
print a1
```

    {'Four': 4, 'Five': 5, 'Three': 3, 'Two': 2, 'One': 1}


**values( )** function returns a list with all the assigned values in the dictionary.


```python
a1.values()
```




    [4, 5, 3, 2, 1]



**keys( )** function returns all the index or the keys to which contains the values that it was assigned to.


```python
a1.keys()
```




    ['Four', 'Five', 'Three', 'Two', 'One']



**items( )** is returns a list containing both the list but each element in the dictionary is inside a tuple. This is same as the result that was obtained when zip function was used.


```python
a1.items()
```




    [('Four', 4), ('Five', 5), ('Three', 3), ('Two', 2), ('One', 1)]



**pop( )** function is used to get the remove that particular element and this removed element can be assigned to a new variable. But remember only the value is stored and not the key. Because the is just a index value.


```python
a2 = a1.pop('Four')
print a1
print a2
```

    {'Five': 5, 'Three': 3, 'Two': 2, 'One': 1}
    4
