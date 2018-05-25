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

# For loops
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

# While loops
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

# Nested loops and prefilled lists/arrays/matrices
It is useful to know that a common technique when you would like to calculate or update the values of a list, it is better to create the list/array/matric and fill it with zeros and then update the values of the elements instead of changing the size of the list/array/matrix in every iteration of the loop.
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
> Using the range function (if you don't know how to use it, run the help on the range function), write a loop that uses range to print the first 5 natural numbers:
{: .inset}


[Go to the next module]({{ site.baseurl }}/modules/04-conditionals)
{: .next-link}
