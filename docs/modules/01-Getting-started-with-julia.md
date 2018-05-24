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

## Basics

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

## Variables
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

Please note that if you would like to use comments, you need to use the # symbol in the beginning of the line or use #= comments =# for multiple line comments
{: .note}








After which you can show the output, like this:
```shell
What a wonderful world
```
{: .output}

