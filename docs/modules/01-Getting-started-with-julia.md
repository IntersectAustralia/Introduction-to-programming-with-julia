---
layout: page
title: "Getting started with Julia"
short-title: "Mod. 1" # This will appear in the Nav bar in the header
show-in-nav-bar: true
---

> Learning objectives:
> - Introduction to basic elements of programming
> - Variable types
> - Data structures
> - Useful built-in functions
{: .objective}

In the first module, you will learn the basic concepts of programming. We will start with basic operations in Julia, followed by the different types of variables in programming. This module also covers the different data structures in Julia, such as tuples, dictionaries and arrays, and also some useful built-in functions.

# Basics

Below is an example of basic operations in Julia, such as addition, multiplication, division, etc.
```python
1+1
2-3
20*5
100/10
10^2
101%2
```
{: .source}

If you would like to suppress the output, you can use the semicolon at the end of the command:
```python
2+2;
```
{: .source}

If you don't know what a particular function does and you would like to check its documentation, you can use the question mark as below:
```python
?println
```
{: .source}

In Julia, you can also use Unix Shell commands by using the ; in front of the command:
```python
;pwd
```
{: .source}
or
```python
;ls
```
{: .source}

To print the output of a command, we will use the **println** method and not the **print** one because the println("...") method prints the string "..." and moves the cursor to a new line (adds a new line at the end of the output). The print("...") method instead prints just the string "...", but does not move the cursor to a new line.
```python
println("I am excited to learn Julia!")
```
{: .source}


# Variables

There are several types of variables in programming, with the main types being:
* Integer: Number without a decimal point, for example, 152
* Floating point number: Precise number with decimal point, for example, 15.26 or 105.0
* String: String of characters within quotes ("), for example, "This is a string"

To assign a new variable, you have to use the equal sign after the name of the variable. In the example below, we assign the number 42 to a new variable called my_answer. This new variable is an integer.
```python
my_answer = 42
```
{: .source}

If you would like to check the type of variable you defined, you can use the typeof command:
```python
typeof(my_answer)
```
{: .source}
```python
Int64
```
{: .output}

Please note that to use comments in Julia, you need to use the # symbol in the beginning of the line or use #=  *text*  =# for multiple line comments.
{: .note}

> # Exercise
>
> A) Assign the number 365 to a variable named days. What is the type of this variable?
>
> B) Convert days to a floating point number
{: .inset}


# Strings

As we mentioned before, you need to use quotes "*string*" or triple quotes """*string*""" to define a string. 
The difference between the single vs triple quotes is that, in the latter, you can use quotation marks within your string.

Be careful! You cannot use single quotation marks (') for strings in Julia!
{: .note}

Below is an example of a string:
```python
"This is my first string."
```
{: .source}
```python
"This is my first string."
```
{: .output}
Another example using the triple quotes:
```python
"""This is a string with "special" characters, such as !-@"""
```
{: .source}
```python
"This is a string with "special" characters, such as !-@"
```
{: .output}

The following example is using a wrong syntax for a string in Julia:
```python
'This is a wrong string'
```
{: .source}
```python
syntax: Invalid character literal
```
{: .output}


## Print strings and other types of variables

Let's explore more things about printing strings. In the following example, we create two new variables called *name* and *age*, which is a string and an integer, respectively. If we would like to print a string including the values of these two variables, we need to use the $ symbol before the variable name. For example, if we add $name within the string, we will print the value of the *name* variable. In this example, we print two strings with the values of the two variables indluded in the outputs: 
```python
name = "John"
age = 25

println("Hello $name")
println("You are $age years old")
```
{: .source}
which gives the following output:
```python
Hello John
You are 25 years old
```
{: .output}

Another example printing the values of both variables in a single command:
```python
println("Hello $name. You are $age years old")
```
{: .source}
```python
Hello John. You are 25 years old
```
{: .output}

You can also do calculations within the println command. Note that the calculation should be within parenthesis after the $ symbol:
```python
println("You are $(2*age+10) years old")
```
{: .source}
```python
You are 60 years old
```
{: .output}

You can also concatenate strings:
```python
s1 = "String 1";
s2 = "String 2";

string(s1," ",s2, " Another string")
```
{: .source}
```python
"String 1 String 2 Another string"
```
{: .output}

Another way to concatenate two strings is by using the * symbol:
```python
s1*s2
```
{: .source}
```python
"String 1String 2"
```
{: .output}

> # Exercise
>
> Define two variables, a=3 and b=4, and use them to create two strings
>
> A) "3 + 4"
>
> B) "7"
{: .inset}


# Data Structures

Once we start working with many pieces of data at once, it will be convenient for us to store data in structures like arrays or dictionaries (rather than just relying on variables).

The types of data structures that we are going to cover here are:
* Tuples
* Dictionaries
* Arrays


## Tuples
We can create a tuple by enclosing an ordered collection of elements in ( ). For example, we can create a tuple called animals including three elements, namely "dogs", "cats" and "penguins".
```python
animals = ("dogs", "cats", "penguins")
```
{: .source}
```python
("dogs", "cats", "penguins")
```
{: .output}

We can index into the tuple using the square brackets [ ]:
```python
animals[1]
```
{: .source}
```python
"dogs"
```
{: .output}

But tupples are immutable, which means that we can't update its elements:
```python
animals[1] = "lions"
```
{: .source}
```python
MethodError: no method matching setindex!(::Tuple{String,String,String}, ::String, ::Int64)
```
{: .output}


## Dictionaries
If we have sets of data related to one another, we may choose to store that data in a dictionary. We can create a dictionary using the Dict() function, which we can initialise as an empty dictionary or one storing key, value pairs.

The syntax of a dictionary is: Dict(key1 => value1, key2 => value2, ...).

Here is an example of a dictionary. We create a dictionary called *phonebook*, with the keys being the names, and the values being the phone numbers. 
```python
phonebook = Dict("Jenny" => "823-231", "John" => "842-475")
```
{: .source}
```python
Dict{String,String} with 2 entries:
  "Jenny" => "823-231"
  "John"  => "842-475"
```
{: .output}

In this example, each name and number is a "key" and "value" pair. We can get Jenny's number (a value) using the associated key:
```python
phonebook["Jenny"]
```
{: .source}
```python
"823-231"
```
{: .output}

We can add another entry to this dictionary using the following syntax:
```python
phonebook["Isabel"] = "736-283";
phonebook
```
{: .source}
```python
Dict{String,String} with 3 entries:
  "Jenny"  => "823-231"
  "John"   => "842-475"
  "Isabel" => "736-283"
```
{: .output}

We can also delete entries from our dictionary using **pop!**
```python
pop!(phonebook, "John");
phonebook
```
{: .source}
```python
Dict{String,String} with 2 entries:
  "Jenny"  => "823-231"
  "Isabel" => "736-283"
```
{: .output}

Unlike tuples and arrays, dictionaries are not ordered. So, we can't index into them using numbers (except if the keys are these numbers). If we try to access *phonebook[1]*, we will get an error saying that key 1 has not found. 
```python
phonebook[1]
```
{: .source}
```python
KeyError: key 1 not found
```
{: .output}

> # Exercise
>
> Try to add "Emergency" as key to the phonebook dictionary with the value 911 using the following syntax:
>
> phonebook["Emergency"]=911
>
> Why doesn't this work?
{: .inset}


## Arrays
Unlike tuples, arrays are mutable, and unlike dictionaries, arrays contain ordered collections. We can create an array by enclosing this collection in [ ].

The syntax to create an array is: [item1, item2, ...].

For example, let's create an array called *fibonachi* with the first few fibonacci numbers (https://en.wikipedia.org/wiki/Fibonacci_number). 
```python
fibonacci = [1,1,2,3,5,8,13]
```
{: .source}
```python
7-element Array{Int64,1}:
  1
  1
  2
  3
  5
  8
 13
```
{: .output}

The elements in an array can be a mix of variable types. In the example below, we have an array including integers and strings:
```python
mix = [1, 2, 3, "Jenny", "John"]
```
{: .source}
```python
5-element Array{Any,1}:
 1       
 2       
 3       
  "Jenny"
  "John"
```
{: .output}

To select an element of an array, you need to use the index inside square brackets:
```python
mix[3]
```
{: .source}
```python
3
```
{: .output}

We can also update the value of an element:
```python
mix[3] = "Jack"
mix
```
{: .source}
```python
5-element Array{Any,1}:
 1       
 2       
  "Jack" 
  "Jenny"
  "John" 
```
{: .output}

We are also able to add more elements in the array using **push!**
```python
push!(fibonacci, 21)
fibonacci
```
{: .source}
```python
8-element Array{Int64,1}:
  1
  1
  2
  3
  5
  8
 13
 21
```
{: .output}

We can remove an element from an array using **pop!** similar to dictionaries:
```python
pop!(fibonacci)
fibonacci
```
{: .source}
```python
6-element Array{Int64,1}:
 1
 1
 2
 3
 5
 8
```
{: .output}

> # Exercise
>
> Create an array called a_array with the following code:
>
> a_array = [1,2,3]
>
> Add the number 4 to the end of this array and then remove it
{: .inset}

# Useful functions in Julia
There are several built-in functions in Julia that are very useful and practical for our coding. Here is a list of some useful function in Julia for basic operations.

|Function|&nbsp;&nbsp;&nbsp;&nbsp;Description|
|:--- |:--- |
|round(x, N)|&nbsp;&nbsp;&nbsp;&nbsp;round x to the nearest integer using N decimal points|
|floor(x, N)|&nbsp;&nbsp;&nbsp;&nbsp;round x to the nearest lower integer using N decimal points|
|ceil(x, N)|&nbsp;&nbsp;&nbsp;&nbsp;round x to the nearest upper integer using N decimal points|
|abs(x)|&nbsp;&nbsp;&nbsp;&nbsp;the absolute value of x|
|sign(x)|&nbsp;&nbsp;&nbsp;&nbsp;indicates the sign of x|
|sqrt(x)|&nbsp;&nbsp;&nbsp;&nbsp;square root of x|
|exp(x)|&nbsp;&nbsp;&nbsp;&nbsp;natural exponential function at x|
|log(x)|&nbsp;&nbsp;&nbsp;&nbsp;natural logarithm of x|
|log(b, x)|&nbsp;&nbsp;&nbsp;&nbsp;base b logarithm of x|
|log10(x)|&nbsp;&nbsp;&nbsp;&nbsp;base 10 logarithm of x|
|A'|&nbsp;&nbsp;&nbsp;&nbsp;transpose of matrix/array A|

## Trigonometric and hyperbolic functions
These functions are all single-argument, except for **atan2**, which gives the angle in radians between the x-axis and the point specified by its arguments, interpreted as x and y coordinates. Additionally, **sinpi(x)** and **cospi(x)** are provided for more accurate computations of sin(pi*x) and cos(pi*x), respectively.

sin    cos    tan    cot    sec    csc
sinh   cosh   tanh   coth   sech   csch
asin   acos   atan   acot   asec   acsc
asinh  acosh  atanh  acoth  asech  acsch
sinc   cosc   atan2

To compute trigonometric functions with degrees instead of radians, suffix the function with d, as shown below. For example, sind(x) computes the sin of x with x specified in degrees. The complete list of trigonometric functions with degree variants is:

sind   cosd   tand   cotd   secd   cscd
asind  acosd  atand  acotd  asecd  acscd


[Go to Module 2 (Slicing)]({{ site.baseurl }}/modules/02-slicing){: .next-link}
