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

Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text 

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
> if 4>5
>   println("A")
> elseif 4 == 5
>   println("B")
> elseif 4<5
>   println("C")
>
> Which of the following would be printed if you were to run this code? Why did you pick this answer?
>
> 1. A
> 2. B
> 3. C
> 4. B and C
{: .inset}



[Go to the next module]({{ site.baseurl }}/modules/05-functions)
{: .next-link}
