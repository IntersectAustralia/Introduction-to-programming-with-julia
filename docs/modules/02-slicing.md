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

Text Text Text Text Text 
Text Text Text Text Text 
Text Text Text Text Text 
Text Text Text Text Text 


# Exercise
Question is ......

  <a id="displayText" href="javascript:toggle(1);">Show Solution code</a>
  <div id="toggleText1" style="display: none">
x <- sample(100) <br />
mean.x <- mean(x) <br />
  </div>




Another way:





<details>
 <summary>Solution</summary>

```python
const x = 1
```
</details>




<details>
  <summary>stuff with *mark* **down**</summary>
  <p>
<!-- the above p cannot start right at the beginning of the line and is mandatory for everything else to work -->
##*formatted* **heading** with [a](link)
```java
code block
```

  <details>
    <summary><small>nested</small> stuff</summary><p>
<!-- alternative placement of p shown above -->

* list
* with

 1. nested
 1. items

    ```java
    // including code
    ```
 1. blocks

  </p></details>
</p></details>




[Go to the next module]({{ site.baseurl }}/modules/03-loops)
{: .next-link}

