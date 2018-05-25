---
layout: page
title: "Creating Functions"
short-title: "Mod. 5" # This will appear in the Nav bar in the header
show-in-nav-bar: true
---

> Learning objectives:
> - ...
> - ...
> - ...
{: .objective}

Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text 



The generic syntax to create a function in Julia is:
```matlab
function function_name(argument1, argument2, ...)
  do things
end
```
{: .source}

Let's create a function that converts temperature from Fahrenheit to Celsius
```matlab
function fahr_to_celsius(temperature)
   (temperature-32)*(5/9) 
end
```
{: .source}

Let's now convert a temperature of 32 Fahrenheit to Celsius
```matlab
println("Freezing point of water: ", fahr_to_celsius(32), " C")
```
{: .source}
```matlab
Freezing point of water: 0.0 C
```
{: .output}





[Go to the next module]({{ site.baseurl }}/modules/06-wrapping-up)
{: .next-link}


