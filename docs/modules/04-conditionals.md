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


According to the inflammation study, there is something suspicious in our inflammation data by looking at the plots. In this section you will learn how you can use Julia to automatically recognize the different features we saw, and take a different action for each, i.e. you will learn how to write code that runs only when certain conditions are true.

# Conditionals

The generic syntax for conditionals in Julia is:
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

For example, let's check if a number is greater than 100. If yes, print "greater", otherwise print "not greater".
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

Note that only the **if** part of the conditional is compulsory. The **elseif** and **else** parts are optional. 
```matlab
number = 37

if number > 100
    println("greater")
end

print("Done")
```
{: .source}
```matlab
```
{: .output}

You can add additional conditions using the **elseif** part (you can add as many you want). For example, let's check if a number is positive, negative or equal to zero:
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

You can also combine conditions using the and (&) symbol, indicating that the condition is only true if both parts are true:
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
In this example, we print "both parts are true" only if the number is greater than 0 and at the same time number is less than 100. 

You can also combine conditions using the or (|) symbol (Shift+\ buttons in the keyboard), if you would like one or the other condition to be true
```matlab
number = 53

if (number < 0) | (number > 100)
    println("at least one part is true")
else
    println("at least one part is false")
end
```
{: .source}
```matlab
at least one part is true
```
{: .output}
In this case, if one of the two conditions is true, then we will print "at least one part is true".


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

Similarly, we can do the same as before with the OR operator, i.e. you can use the single OR operator if you would like to evaluate the whole conditionals
```matlab
true | (println("hi"); true)
```
{: .source}
```matlab
hi
true
```
{: .output}
or you can use the double OR operator || for short-circuit evaluation
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

Let's go back to the inflammation dataset to apply the conditional to find out if our dataset is OK for analysis or if there are any problems. We know that there is something suspicious in the inflammation data: 
1. If the maximum inflammation at Day 1 is 0 and at Day 21 is 20
2. If the minimum inflammation per Day is 0 throughout all the days

To check if each of the inflammation datasets has any of these two problems, we can use conditionals. Let's start building our conditional step by step. Let's start with the first rule about the maximum inflammation:
```matlab
data = readdlm("./data/inflammation-01.csv", ',');

if (maximum(data,1)'[1]==0) & (maximum(data,1)'[21]==20)
    println("Problem detected: Suspicious looking maximum!")
end
```
{: .source}
Now, let's add the second rule using the elseif command:
```matlab
data = readdlm("./data/inflammation-01.csv", ',');

if (maximum(data,1)'[1]==0) & (maximum(data,1)'[21]==20)
    println("Problem detected: Suspicious looking maximum!")
elseif sum(minimum(data,1)')==0
    println("Problem detected: Minimum add up to zero!")
end
```
{: .source}
and at the end let's add a statement if the dataset is OK:
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

So, if we run this conditional for the *inflammation-01.csv* dataset, the output will be
```matlab
Problem detected: Suspicious looking maximum!
```
{: .output}
which means that we have detected a problem in the first dataset. Try to run this conditional on the first three dataset to check if the other two datasets also have a problem.


[Go to Module 5 (Functions)]({{ site.baseurl }}/modules/05-functions){: .next-link}
