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




[Go to the next module]({{ site.baseurl }}/modules/05-functions)
{: .next-link}


