---
layout: page
title: "Making Choices with Conditionals"
short-title: "Mod. 4" # This will appear in the Nav bar in the header
show-in-nav-bar: true
---

> Learning objectives:
> - ...
> - ...
> - ...
{: .objective}


In our last section, according to the inflammation study, there is something suspicious in our inflammation data by looking at the plots. In this section you will learn how you can use Python to automatically recognize the different features we saw, and take a different action for each, i.e. you will learn how to write code that runs only when certain conditions are true.

# Conditionals
Generic syntax for conditionals
```matlab
if condition1
  option 1
elseif condition2
  option 2
else
  option 3
end
```
{: .source}

For example, let's check if the number is greater than 100 and print greater if the number is greater than 100 or print not greater if the number is less or equal to 100.
```matlab
number = 37

if number > 100
    println("greater")
else
    println("not greater")
end

print("Done")
```
{: .source}
```matlab
not greater
Done
```
{: .output}

Only the if part is compulsory to run a conditional
```matlab
number = 37

if number > 100
    println("greater")
else
    println("not greater")
end

print("Done")
```
{: .source}
```matlab
before conditional...
...after conditional
```
{: .output}

You can add additional conditions using the elseif part (you can add as many you want)
```matlab
number = -3

if number > 0
    println(number, " is positive")
elseif num == 0
    println(number, " is zero")
else
    println(number, " is negative")
end
```
{: .source}
```matlab
-3 is negative
```
{: .output}

You can also combine conditions using the and (&) symbol, if you would like both conditions to be true
```matlab
number = 53

if (number > 0) & (number < 100)
    println("both parts are true")
else
    println("at least one part is false")
end
```
{: .source}
```matlab
both parts are true
```
{: .output}

or you can combine conditions with the or (|) symbol (Shift+\ buttons in the keyboard), if you would like one or the other condition to be true
```matlab
number = 53

if (number < 0) | (number > 100)
    println("both parts are true")
else
    println("at least one part is false")
end
```
{: .source}
```matlab
at least one part is false
```
{: .output}

> # Exercise
> 
> You have the following code
>
> ```matlab
> if 4>5
>   println("A")
> elseif 4 == 5
>   println("B")
> elseif 4<5
>   println("C")
> end
> ```
>{: .source}
>
> Which of the following would be printed if you were to run this code? Why did you pick this answer?
>
> 1. A
> 2. B
> 3. C
> 4. B and C
{: .inset}

# Additional things with Julia Conditionals
In Julia, we can write conditionals in a more compact way, such as
```matlab
a?b:c
```
{: .source}
which equates to
```matlab
if a
    b
else
    c
end
```
{: .source}

For example, we have the following conditional
```matlab
x=3
y=5

if x>y
    println(x)
else
    println(y)
end
```
{: .source}
which gives an output
```matlab
5
```
{: .output}

We could write the previous conditional using Julia's compact way
```matlab
(x>y) ? println(x) : println(y)
```
{: .source}
which gives the exact same output
```matlab
5
```
{: .output}

In this compact format, if we replace & with &&, as in a && b, we get short-circuit evaluation, i.e. b is only evaluated if a is true, which can help us out if evaluating b is expensive (time consuming). For example
```matlab
(x > y) && println(x)
```
{: .source}
```matlab
false
```
{: .output}


```matlab
(x < y) && println(y)
```
{: .source}
```matlab
5
```
{: .output}

Similarly with the OR operator | and ||
```matlab
true | (println("hi"); true)
```
{: .source}
```matlab
hi
true
```
{: .output}
However, if we use the double OR operator
```matlab
true || (println("hi"); true)
```
{: .source}
```matlab
true
```
{: .output}

> # Exercise
>
> text text text
{: .inset}

# Inflammation datasets and conditionals
Let's say that we know that there are some rules to understand if there is a problem in our inflammation dataset, and these rules are:
1. If the maximum inflammation at Day 1 is 0 and at Day 21 is 20
2. If the minimum inflammation per Day is 0 throughout all the days

To check if each of the inflammation datasets has any of these two problems, we can use conditionals. Let's start building our conditional step by step. Let's start with the first rule about the maximum
```matlab
data = readdlm("./data/inflammation-01.csv", ',');

if (maximum(data,1)'[1]==0) & (maximum(data,1)'[21]==20)
    println("Problem detected: Suspicious looking maximum!")
end
```
{: .source}
Now let's add the second rule using the elseif command
```matlab
data = readdlm("./data/inflammation-01.csv", ',');

if (maximum(data,1)'[1]==0) & (maximum(data,1)'[21]==20)
    println("Problem detected: Suspicious looking maximum!")
elseif sum(minimum(data,1)')==0
    println("Problem detected: Minimum add up to zero!")
end
```
{: .source}
and at the end let's add a statement if the dataset is ok. 
```matlab
data = readdlm("./data/inflammation-01.csv", ',');

if (maximum(data,1)'[1]==0) & (maximum(data,1)'[21]==20)
    println("Problem detected: Suspicious looking maximum!")
elseif sum(minimum(data,1)')==0
    println("Problem detected: Minimum add up to zero!")
else
    println("The dataset is OK")
end
```
{: .source}
So if we run this conditional for the inflammation-01.csv, the output will be
```matlab
Problem detected: Suspicious looking maximum!
```
{: .output}
which means that we have detected a problem in the first dataset. Try to run this conditional to the first three dataset to check if the other two datasets also have a problem.


## Next
In the next module we're going ........................

[Go to Module 5 (Functions)]({{ site.baseurl }}/modules/05-functions){: .next-link}
