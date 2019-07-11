---
layout: page
title: Python Intro
subtitle: Practice makes Expert
---



# Variables

A name that is used to denote something or a value is called a variable. In python, variables can be declared and values can be assigned to it as follows,


```python
x = 2
y = 5
xy = 'Hey'
```


```python
print x+y, xy
```

    7 Hey


Multiple variables can be assigned with the same value.


```python
x = y = 1
```


```python
print x,y
```

    1 1


# Operators

##Arithmetic Operators

| Symbol | Task Performed |
|----|---|
| +  | Addition |
| -  | Subtraction |
| /  | division |
| %  | mod |
| *  | multiplication |
| //  | floor division |
| **  | to the power of |


```python
1+2
```




    3




```python
2-1
```




    1




```python
1*2
```




    2




```python
1/2
```




    0



0? This is because both the numerator and denominator are integers but the result is a float value hence an integer value is returned. By changing either the numerator or the denominator to float, correct answer can be obtained.


```python
1/2.0
```




    0.5




```python
15%10
```




    5



Floor division is nothing but converting the result so obtained to the nearest integer.


```python
2.8//2.0
```




    1.0



##Relational Operators

| Symbol | Task Performed |
|----|---|
| == | True, if it is equal |
| !=  | True, if not equal to |
| < | less than |
| > | greater than |
| <=  | less than or equal to |
| >=  | greater than or equal to |


```python
z = 1
```


```python
z == 1
```




    True




```python
z > 1
```




    False



##Bitwise Operators

| Symbol | Task Performed |
|----|---|
| &  | Logical And |
| l  | Logical OR |
| ^  | XOR |
| ~  | Negate |
| >>  | Right shift |
| <<  | Left shift |


```python
a = 2 #10
b = 3 #11
```


```python
print a & b
print bin(a&b)
```

    2
    0b10



```python
5 >> 1
```




    2



0000 0101 -> 5

Shifting the digits by 1 to the right and zero padding

0000 0010 -> 2


```python
5 << 1
```




    10



0000 0101 -> 5

Shifting the digits by 1 to the left and zero padding

0000 1010 -> 10

#Built-in Functions

Python comes loaded with pre-built functions

##Conversion from one system to another

Conversion from hexadecimal to decimal is done by adding prefix **0x** to the hexadecimal value or vice versa by using built in **hex( )**, Octal to decimal by adding prefix **0** to the octal value or vice versa by using built in function **oct( )**.


```python
hex(170)
```




    '0xaa'




```python
0xAA
```




    170




```python
oct(8)
```




    '010'




```python
010
```




    8



**int( )** accepts two values when used for conversion, one is the value in a different number system and the other is its base. Note that input number in the different number system should be of string type.


```python
print int('010',8)
print int('0xaa',16)
print int('1010',2)
```

    8
    170
    10


**int( )** can also be used to get only the integer value of a float number or can be used to convert a number which is of type string to integer format. Similarly, the function **str( )** can be used to convert the integer back to string format


```python
print int(7.7)
print int('7')
```

    7
    7


Also note that function **bin( )** is used for binary and **float( )** for decimal/float values. **chr( )** is used for converting ASCII to its alphabet equivalent, **ord( )** is used for the other way round.


```python
chr(98)
```




    'b'




```python
ord('b')
```




    98



##Simplifying Arithmetic Operations

**round( )** function rounds the input value to a specified number of places or to the nearest integer.


```python
print round(5.6231)
print round(4.55892, 2)
```

    6.0
    4.56


**complex( )** is used to define a complex number and **abs( )** outputs the absolute value of the same.


```python
c =complex('5+2j')
print abs(c)
```

    5.38516480713


**divmod(x,y)** outputs the quotient and the remainder in a tuple(you will be learning about it in the further chapters) in the format (quotient, remainder).


```python
divmod(9,2)
```




    (4, 1)



**isinstance( )** returns True, if the first argument is an instance of that class. Multiple classes can also be checked at once.


```python
print isinstance(1, int)
print isinstance(1.0,int)
print isinstance(1.0,(int,float))
```

    True
    False
    True


**cmp(x,y)**

|x ? y|Output|
|---|---|
| x < y | -1 |
| x == y | 0 |
| x > y | 1 |


```python
print cmp(1,2)
print cmp(2,1)
print cmp(2,2)
```

    -1
    1
    0


**pow(x,y,z)** can be used to find the power $x^y$ also the mod of the resulting value with the third specified number can be found i.e. : ($x^y$ % z).


```python
print pow(3,3)
print pow(3,3,5)
```

    27
    2


**range( )** function outputs the integers of the specified range. It can also be used to generate a series by specifying the difference between the two numbers within a particular range. The elements are returned in a list (will be discussing in detail later.)


```python
print range(3)
print range(2,9)
print range(2,27,8)
```

    [0, 1, 2]
    [2, 3, 4, 5, 6, 7, 8]
    [2, 10, 18, 26]


##Accepting User Inputs

**raw_input( )** accepts input and stores it as a string. Hence, if the user inputs a integer, the code should convert the string to an integer and then proceed.


```python
abc = raw_input("Type something here and it will be stored in variable abc \t")
```

    Type something here and it will be stored in variable abc 	Hey



```python
type(abc)
```




    str



**input( )**, this is used only for accepting only integer inputs.


```python
abc1 =  input("Only integer can be stored in variable abc \t")
```

    Only integer can be stored in variable abc 	275



```python
type(abc1)
```




    int



Note that **type( )** returns the format or the type of a variable or a number
