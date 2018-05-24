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

