---
layout: page
title: "Repeating Actions with Loops"
short-title: "Mod. 3" # This will appear in the Nav bar in the header
show-in-nav-bar: true
---

> Learning objectives:
> - Explain what a for and while loop does.
> - Correctly write for and while loops to repeat simple calculations.
> - Trace changes to a loop variable as the loop runs.
> - Trace changes to other variables as they are updated by a for loop
{: .objective}

Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text 

Let's create a variable called word
```matlab
word = "lead"
```
{: .source}

If we would like to print each letter of the variable word, we should do:
```matlab
println(word[1])
println(word[2])
println(word[3])
println(word[4])
```
{: .source}

However, this is a not a good practise because:
1. text text
2. text text 

```matlab
word = "tin";
println(word[1])
println(word[2])
println(word[3])
println(word[4])
```
{: .source}

```matlab
t
i
n
BoundsError: attempt to access "tin"
  at index [4]
```
{: .output}

# for loops
Here is a better example of how to do repetitive actions in programming using loops
```matlab
word = "lead";
for char in word
    println(char)
end
```
{: .source}

```matlab
l
e
a
d
```
{: .output}

Now, if we change the variable word, we will have an error message
```matlab
word = "oxygen";
for char in word
    println(char)
end
```
{: .source}

```matlab
o
x
y
g
e
n
```
{: .output}

The generic syntax of a **for** loop
```matlab
for variable in collection
    do things
end
```
{: .source}

The name of the variable in the loop can be whatever, however, note that it is always useful to give meaningful names to the variables
```matlab
word = "oxygen";
for banana in word
    println(banana)
end
```
{: .source}
```matlab
o
x
y
g
e
n
```
{: .output}

Let's try now to calculate the number of elements in a list, or if you prefer, how many times the loop will run
```matlab
len = 0;
for vowel in "aeiou"
    len = len + 1
end

println("There are $len vowels in the collection")
```
{: .source}
```
There are 5 vowels in the collection
```
{: .output}

Of course, there is a built-in function to calculate the length
```matlab
println("The length is of the collection is: ", length("aeiou"))
```
{: .source}
```
The length is of the collection is: 5
```
{: .output}

Let's explore a few more things about loops. 
```matlab
letter = "z"
for letter in "abc"
    println(letter)
end

println("After the loop, letter is: $letter")
```
{: .source}
```
a
b
c
After the loop, letter is: c
```
{: .output}

# while loops
Another type of loops are the while loops. The difference ....

Here is an example of a while lopp that prints a number until the number is less or equal to 10
```matlab
number=1

while number<=10
    println("The number is: $number")
    number = number + 1
end
```
{: .source}
```
The number is: 1
The number is: 2
The number is: 3
The number is: 4
The number is: 5
The number is: 6
The number is: 7
The number is: 8
The number is: 9
The number is: 10
```
{: .output}

**Be careful** though with the location of the increment in the while loops because it can lead to wrong results
```matlab
number=1

while number<=10
    number = number + 1
    println("The number is: $number")
end
```
{: .source}
```
The number is: 2
The number is: 3
The number is: 4
The number is: 5
The number is: 6
The number is: 7
The number is: 8
The number is: 9
The number is: 10
The number is: 11
```
{: .output}

The generic sytnax of a while loop is
```matlab
while condition
    operations within the loop
    increment
end
```
{: .source}

Another example of a while loop
```matlab
names = ["Ted", "Robyn", "Barney", "Lily", "Marshall"]

i = 1
while i<=length(names)
    selected_name = names[i]
    println("Hi $selected_name. How are you?")
    i += 1
end
```
{: .source}
```
Hi Ted. How are you?
Hi Robyn. How are you?
Hi Barney. How are you?
Hi Lily. How are you?
Hi Marshall. How are you?
```
{: .output}

# Nested loops and prefilled arrays
It is useful to know that a common technique when you would like to calculate or update the values of a list, it is better to create the array and fill it with zeros and then update the values of the elements instead of changing the size of the array in every iteration of the loop.
```matlab
m,n = 3,3
A = fill(0, (m,n))

for i in 1:m
    for j in 1:n
        A[i,j] = i+j
    end
end

A
```
{: .source}
```
3×3 Array{Int64,2}:
 2  3  4
 3  4  5
 4  5  6
```
{: .output}

In Julia, a nested loop can be also written as
```matlab
m,n = 3,3
B = fill(0, (m,n))

for i in 1:m, j in 1:n
        B[i,j] = i+j
end

B
```
{: .source}
```
3×3 Array{Int64,2}:
 2  3  4
 3  4  5
 4  5  6
```
{: .output}
or in a much compact way 
```matlab
C = [i+j for i in 1:m, j in 1:n]
```
{: .source}
```
3×3 Array{Int64,2}:
 2  3  4
 3  4  5
 4  5  6
```
{: .output}

> # Exercise
>
> Using the range function (if you don't know how to use it, run the help on the range function), write a loop that uses range to print the first 5 natural numbers.
{: .inset}

> # Exercise
>
> Exponentiation is built into Julia:
>
> 5^3
>
> Write a loop that calculates the same result (5^3)
{: .inset}

> # Exercise
>
> Use an array comprehension to create an create an array that stores the squares for all integers between 1 and 10
{: .inset}

# Inflammation datasets and loops
Now we can analyse multiple inflammation datasets using a for loop
Before that let's explore the "Glob" package, which will help us create a list of all the filenames. 
The glob function takes two arguments, a pattern and the path where to look for the pattern. 
```matlab
glob(pattern,path)
```
{: .source}
In our case, the pattern we are looking is "infl*" (this is only one out of many patterns we can use) because all our files are in the form inflammation-two digit number.csv
The * symbol is called wildcard and it means that we are looking for a pattern in the filenames that includes the characters "infl" and then 0 or more other characters after.
```matlab
namelist=glob("infl*","./data/")
```
{: .source}
```matlab
12-element Array{String,1}:
 "./data/inflammation-01.csv"
 "./data/inflammation-02.csv"
 "./data/inflammation-03.csv"
 "./data/inflammation-04.csv"
 "./data/inflammation-05.csv"
 "./data/inflammation-06.csv"
 "./data/inflammation-07.csv"
 "./data/inflammation-08.csv"
 "./data/inflammation-09.csv"
 "./data/inflammation-10.csv"
 "./data/inflammation-11.csv"
 "./data/inflammation-12.csv"
```
{: .output}
If we would like to make sure that the output array is also sorted, we can use the sort function
```matlab
namelist=sort(glob("infl*","./data/"), rev=false)
```
{: .source}
```matlab
12-element Array{String,1}:
 "./data/inflammation-01.csv"
 "./data/inflammation-02.csv"
 "./data/inflammation-03.csv"
 "./data/inflammation-04.csv"
 "./data/inflammation-05.csv"
 "./data/inflammation-06.csv"
 "./data/inflammation-07.csv"
 "./data/inflammation-08.csv"
 "./data/inflammation-09.csv"
 "./data/inflammation-10.csv"
 "./data/inflammation-11.csv"
 "./data/inflammation-12.csv"
```
{: .output}

So let's try now to apply everything we know to analyse the first 3 datasets and let's do it as it should be from the scratch. 
```matlab
using Glob
using Plots

filenames = sort(glob("infl*","./data/"), rev=false);
days=1:40;

for f in filenames[1:3]
    
    println("Processing dataset: ",f)
    
    sleep(0.5)
    
    data = readdlm(f, ',');
    
    p1=plot(days,mean(data,1)', ylabel="Average", label="Mean", color="blue", xlims=(-2,45), ylims=(0,14))
    p2=plot(days,maximum(data,1)', ylabel="Maximum", label="Max", c="green",alpha=0.5, fill=(0,"gray"))
    p3=plot(days,maximum(data,1)', seriestype=:scatter, ylabel="Minimum", label="Min", marker=(:white,2,:o,stroke(1,:black)))

    p=plot(p1,p2,p3,layout=(1,3), legend=false, xlabel="Day", lw=2,size=(1000,300), grid=true)
    display(p)
end
```
{: .source}

![loops image 1](../images/julia7.png)

## Next
In the next module we're going ........................

[Go to Module 4 (Conditionals)]({{ site.baseurl }}/modules/04-conditionals){: .next-link}
