---
layout: page
title: "Selecting Elements from an Array"
short-title: "Mod. 2" # This will appear in the Nav bar in the header
show-in-nav-bar: true
---

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

First add the javascript to toggle boxes(remember to indent it)

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

and then we have some R code with the toggle button wrapped around (also indented):

  <a id="displayText" href="javascript:toggle(1);">Show underlying code</a>
  <div id="toggleText1" style="display: none">

```{r}
x <- sample(100)
mean.x <- mean(x)
```

  </div>

The mean is `r mean.x`. Please click the link to see the source code.

  <a id="displayText" href="javascript:toggle(2);">Show underlying code</a>
  <div id="toggleText2" style="display: none">

```{r}
median.x <- median(x)
```

  </div>

And the median is `r median.x`. Please click the link to see the source code.


[Go to the next module]({{ site.baseurl }}/modules/03-loops)
{: .next-link}

