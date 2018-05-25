---
layout: page
title: "Getting started with Julia"
short-title: "Mod. 1" # This will appear in the Nav bar in the header
show-in-nav-bar: true
---

> Learning objectives:
> - ...
> - ...
> - ...
{: .objective}

Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text 

Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text 

# Why Julia?
Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text 

# Basics

Excecute basic operations
```python
1+1
2-3
20*5
100/10
10^2
101%2
```
{: .source}

Suppress the output using the semicolon
```python
2+2;
```
{: .source}

You can find some help information for the functions using the question mark
```python
?println
```
{: .source}

In Julia, you are able to use Unix Shell commands by using the ; in front of the command
```python
;pwd
```
{: .source}
or
```python
;ls
```
{: .source}

To print something in Julia, we will use println and not print because the println("...") method prints the string "..." and moves the cursor to a new line (adds a new line to the end of output). The print("...") method instead prints just the string "...", but does not move the cursor to a new line.:
```python
println("I am excited to learn Julia!")
```
{: .source}

# Variables
Types of variables include:
* Integer: Number without a decimal point, for example, 152
* Floating point number: Precise number with decimal point, for example, 15.26 or 105.0
* String: String of characters within quotes ("), for example, "This is a string"

Assign variables using the equal sign
```python
my_answer = 42
```
{: .source}

Check the type of a variable
```python
typeof(my_answer)
```
{: .source}
```python
Int64
```
{: .output}

Please note that if you would like to use comments, you need to use the # symbol in the beginning of the line or use #=  *text*  =# for multiple line comments
{: .note}

> # Exercise
>
> A) Assign the number 365 to a variable named days. What is the type of this variable?
>
> B) Convert days to a floating point number
{: .inset}

# Strings
As we mentioned before, you need to use quotes "*string*" or triple quotes """*string*""" to define a string. 
One difference between the single vs triple quotes is that, in the latter case, you can use quotation marks within your string.

Be careful! You cannot use single quotation marks (') for strings in Julia.
{: .note}

This is an example of a string:
```python
"This is my first string."
```
{: .source}
```python
"This is my first string."
```
{: .output}
or
```python
"""This is a string with "special" characters, such as !-@"""
```
{: .source}
```python
"This is a string with "special" characters, such as !-@"
```
{: .output}

This is a wrong syntax for a string in Julia
```python
'This is a wrong string'
```
{: .source}
```python
syntax: Invalid character literal
```
{: .output}

## Print strings and other types of variables

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

or
```python
println("Hello $name. You are $age years old")
```
{: .source}
```python
Hello John. You are 25 years old
```
{: .output}

You can also do calculations within the println before you print the output. Note that the calculation should be within parenthesis after the $ symbol:
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
or another way to concatenate two strings:
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
> Declare two variables, a=3 and b=4, and use them to create two strings
>
> A) "3 + 4"
>
> B) "7"
{: .inset}

# Data Structures
Once we start working with many pieces of data at once, it will be convenient for us to store data in structures like arrays or dictionaries (rather than just relying on variables).

Types of data structures covered:
* Tuples
* Dictionaries
* Arrays

## Tuples
We can create a tuple by enclosing an ordered collection of elements in ( ).
```python
animals = ("dogs", "cats", "penguins")
```
{: .source}
```python
("dogs", "cats", "penguins")
```
{: .output}

Index into the tuple
```python
animals[1]
```
{: .source}
```python
"dogs"
```
{: .output}
But tupples are immutable, so we can't update it
```python
animals[1] = "lions"
```
{: .source}
```python
MethodError: no method matching setindex!(::Tuple{String,String,String}, ::String, ::Int64)
```
{: .output}

## Dictionaries
If we have sets of data related to one another, we may choose to store that data in a dictionary. We can create a dictionary using the Dict() function, which we can initialize as an empty dictionary or one storing key, value pairs.

The syntax is: Dict(key1 => value1, key2 => value2, ...)
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
In this example, each name and number is a "key" and "value" pair. 
We can grab Jenny's number (a value) using the associated key:
```python
phonebook["Jenny"]
```
{: .source}
```python
"823-231"
```
{: .output}
We can add another entry to this dictionary
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
We can also delete entries from our dictionary
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
Unlike tuples and arrays, dictionaries are not ordered. So, we can't index into them using numbers (except if the keys are these numbers).
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
> Try to add "Emergency" as key to the phonebook dictionary with the value 911 using the following code
>
> phonebook["Emergency"]=911
>
> Why doesn't this work?
{: .inset}


## Arrays
Unlike tuples, arrays are mutable. Unlike dictionaries, arrays contain ordered collections. We can create an array by enclosing this collection in [ ].

The syntax is: [item1, item2, ...]

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

The elements in an array can be of different types:
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

To select an element using indexing, you need to use the index inside square brackets
```python
mix[3]
```
{: .source}
```python
3
```
{: .output}

We can also update the value of an element
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

Add another element in the array
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

Also, we can remove an item from an array
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
> Create an array called a_ray with the following code:
>
> a_ray = [1,2,3]
>
> Add the number 4 to the end of this array and then remove it
{: .inset}


## Next
In the next module we're going ........................

[Go to Module 2 (Slicing)]({{ site.baseurl }}/modules/02-slicing){: .next-link}
