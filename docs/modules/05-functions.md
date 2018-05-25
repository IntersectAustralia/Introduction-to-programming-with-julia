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

# Functions
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

In Julia, there is an alternative and more compact way to declare the function in a single line
```matlab
fahr_to_celsius2(temperature) = (temperature-32)*(5/9)
```
{: .source}
And if we convert 32 Fahrenheit to Celsius using the latter function, we will have the same answer
```matlab
println("Freezing point of water: ", fahr_to_celsius2(32), " C")
```
{: .source}
```matlab
Freezing point of water: 0.0 C
```
{: .output}

Another way to declare the function would be using the so called "anonymous" function
```matlab
fahr_to_celsius3 = temperature -> (temperature-32)*(5/9)
```
{: .source}
and then if we would like to use the anonymous function, it would be the same way as before
```matlab
println("Freezing point of water: ", fahr_to_celsius3(32), " C")
```
{: .source}
```matlab
Freezing point of water: 0.0 C
```
{: .output}

# Mutating vs non-mutating functions
By convention, functions followed by the exclamation mark symbol (!) after their contents and functions lacking ! do not. 

For example let's use the sort function to sort a list of values
```matlab
v = [3,5,2]
sort(v)
```
{: .source}
```matlab
3-element Array{Int64,1}:
 2
 3
 5
```
{: .output}
However, list v hasn't changed
```matlab
v
```
{: .source}
```matlab
3-element Array{Int64,1}:
 3
 5
 2
```
{: .output}

Now if we run the sort function but with the ! then
```matlab
sort!(v)
```
{: .source}
```matlab
3-element Array{Int64,1}:
 2
 3
 5
```
{: .output}
and the list will retain the sorted format because we used the ! after sort
```matlab
v
```
{: .source}
```matlab
3-element Array{Int64,1}:
 2
 3
 5
```
{: .output}

# Higher order functions

## map
The map function is a "higher-order" function in Julia that takes a function as one of its input arguments. map then applies that function to every element of the data structure you pass it. For example, executing 
```matlab
map(f, [1, 2, 3])
```
{: .source}
will give you an output array where the function f has been applied to all elements of [1,2,3], i.e. [f(1),f(2),f(3)].

Here is an example. We have a function that calculates the cube of a number and we would like to apply this calculation to a list of numbers. We are going to use map to do that
```matlab
map(x->x^3, [1,4,7])
```
{: .source}
```matlab
3-element Array{Int64,1}:
   1
  64
 343
```
{: .output}




[Go to the next module]({{ site.baseurl }}/modules/06-wrapping-up)
{: .next-link}
