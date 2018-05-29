---
layout: page
title: "Selecting Elements from an Array"
short-title: "Mod. 2" # This will appear in the Nav bar in the header
show-in-nav-bar: true
---
  <script language="javascript"> 
    function toggle(num) {
      var ele = document.getElementById("toggleText" + num);
      var text = document.getElementById("displayText" + num);
      if(ele.style.display == "block") {
        ele.style.display = "none";
        text.innerHTML = "show";
      }
      else {
        ele.style.display = "block";
        text.innerHTML = "hide";
      }
   } 
  </script>

> Learning objectives:
> - ...
> - ...
> - ...
{: .objective}

Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text Text 

# Packages in Julia
Most of the times, Julia doesn't have built-in functions for more advanced things, such as plotting, data manipulation etc. However, it has more than 1700 registered packages, which are libraries that contain functions. Please find a full list of all the available packages in Julia in the following link:
https://pkg.julialang.org/

The first time you use a package on a given Julia installation, you need to explicitly add it:
```python
Pkg.add("package_name")
```
{: .source}

Every time you use Julia (start a new session at the REPL, or open a notebook for the first time, for example), you load the package with the using keyword
```python
using package_name
```
{: .source}

In our tutorial, we will start using some packages, namely "CSV" and "Dataframes" to load a csv file and the "Plots" package for our plotting. 

```python
using CSV
using DataFrames
using Plots
```
{: .source}

Let's load our CSV file:
```python
data2 = CSV.read("./data/inflammation-01.csv", delim=",",header=false)
```
{: .source}

If we check the type of the data2 variable, we will see that it is a Dataframe. We can check the dimensions of this Dataframe  using the size function:
```python
size(data2)
```
{: .source}
which gives us the number of the rows and columns. We are also able to check the number of either the rows or the columns:
```python
size(data2,1)
size(data2,2)
```
{: .source}

The scope of this introductory course doesn't cover Dataframes, which is a more complex topic, so we are going to load a csv file as a simple 2 dimensional array
```python
data=readdlm("./data/inflammation-01.csv",',')
```
{: .source}
and check the size of the data array
```python
size(data)
```
{: .source}
and its type
```python
typeof(data)
```
{: .source}

# Slicing
In this section, we are going to learn how to select elements of the array. To select an element, you need to define the name of the array followed by the square brackets and within the brackets you need to define the number of the row and column. For example, if we would like to select the element from the first row and the first column:
```python
println("First value in data: ",data[1,1])
```
{: .source}
or the item from the last row and last column
```python
println("Last value in data: ",data[end,end])
```
{: .source}
or any other element by defining the number of the row and column
```python
println("Middle value in data: ",data[30,20])
```
{: .source}

You can also select multiple rows or columns at once
```python
data[1:4,1:10]
```
{: .source}
In the previous example, we have selected all the elements from row 1 to 4 and from column 1 to 10. 

It is not necessary to slice an array starting from the beginning. We can slice using any numbers of the rows and columns
```python
data[5:10,5:10]
```
{: .source}

Another example
```python
data_small = data[1:4,36:end]
```
{: .source}

You can also slice the array by selecting the rows 1, 4, 7 and 10 (or rows 1 to 10 with a step of 3) and the columns 1 to 10 with a step of 2
```python
data[1:3:10,1:2:10]
```
{: .source}

If we would like to select all the rows or columns, we can use the : without defining anything
```python
data[:,1]
```
{: .source}
or for the columns
```python
data[1,:]
```
{: .source}

Another example
```python
data[1:4,end-2]
```
{: .source}

We can also do operations in arrays
```python
doubledata = data * 2
```
{: .source}
or
```python
tripledata = data + doubledata
```
{: .source}

We can also perform basic statistics in the array
```python
mean(data)
```
{: .source}

```python
maximum(data)
```
{: .source}

```python
minimum(data)
```
{: .source}

```python
std(data)
```
{: .source}







# Exercise
Question is ......

  <a id="displayText" href="javascript:toggle(1);">Show Solution code</a>
  <div id="toggleText1" style="display: none">
x <- sample(100) <br />
mean.x <- mean(x) <br />
  </div>




Another way:




<details>
  <summary>
    Collapsed Block
  </summary>

  <h2 id="header">Header</h2>
  
  <code>racket
  (define (sqr x)
  (* x x))
  </code>
</details>

## Next
In the next module we're going ........................

[Go to Module 3 (Loops)]({{ site.baseurl }}/modules/03-loops){: .next-link}
