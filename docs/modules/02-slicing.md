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




<details><summary>Collapsed Block\n</summary>\n\n## Header\n</details>" | kramdown --parse-block-html


[Go to the next module]({{ site.baseurl }}/modules/03-loops)
{: .next-link}

