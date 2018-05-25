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


[Go to the next module]({{ site.baseurl }}/modules/04-conditionals)
{: .next-link}
