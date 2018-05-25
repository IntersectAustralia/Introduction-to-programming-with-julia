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

Let's create now a function that converts Celsius to Kelvin. 
```matlab
function celcius_to_kelvin(temperature_c)
    temperature_c += 273.15
end
```
{: .source}





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

## **map** function
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

## **broadcast** function
The broadcast function is another "higher-order" function like map. broadcast is a generilisation of map, so it can do every thing map can do and more. The syntax for calling broadcast is teh same as for calling map
```matlab
broadcast(function_name, [item1, item2, item3])
```
{: .source}

Some syntactic sugar for calling broadcast is to place a dot (.) between the name of the function you want to broadcast and its input arguments. For example
```matlab
broadcast(function_name, [item1, item2, item3])
```
{: .source}
is the same as
```matlab
function_name.([1, 2, 3])
```
{: .source}

Let's do an example to better understand the broadcast function. 
```matlab
broadcast(x->x^3, [1,4,7])
```
{: .source}
```matlab
3-element Array{Int64,1}:
   1
  64
 343
```
{: .output}

We can do the same now using the dot after the calling the function
```matlab
f(x) =x^3
f.([1,4,7])
```
{: .source}
```matlab
3-element Array{Int64,1}:
   1
  64
 343
```
{: .output}

Another example. Let's create a 3x3 array using the compact way for nested loops in Julia
```matlab
A = [i + 3*j for j in 0:2, i in 1:3]
```
{: .source}
```matlab
3×3 Array{Int64,2}:
 1  2  3
 4  5  6
 7  8  9
```
{: .output}

If we run the f function we created before on the A array, we will have
```matlab
f(A)
```
{: .source}
```matlab
3×3 Array{Int64,2}:
  468   576   684
 1062  1305  1548
 1656  2034  2412
```
{: .output}
so we will have the cube of all the numbers of the A array.

Now let's try to apply the broadcast function on f using the dot syntax. This syntax for broadcasting allows us to write relatively complex compound elementwise expressions in a way that looks natural/closer to mathematical notation.
```matlab
f.(A)
```
{: .source}
```matlab
3×3 Array{Int64,2}:
   1    8   27
  64  125  216
 343  512  729
```
{: .output}
or a more complex example
```matlab
A .+ 2 .* f.(A) ./ A
```
{: .source}
```matlab
3×3 Array{Float64,2}:
   3.0   10.0   21.0
  36.0   55.0   78.0
 105.0  136.0  171.0
```
{: .output}


[Go to the next module]({{ site.baseurl }}/modules/06-wrapping-up)
{: .next-link}
