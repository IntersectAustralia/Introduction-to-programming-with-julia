---
layout: page
title: "Scope of Variables"
short-title: "Mod. 6" # This will appear in the Nav bar in the header
show-in-nav-bar: true
---

> Learning objectives:
> - ...
> - ...
> - ...
{: .objective}

# Scope of variables
Before we finish with this course, it would be good to learn also about another concept in programming, the scope of variables.

The scope of a variable is the region of code within which a variable is visible. Variable scoping helps avoid variable naming conflicts. The concept is intuitive: two functions can both have arguments called x without the two x's referring to the same thing. Similarly there are many other cases where different blocks of code can use the same name without referring to the same thing. The rules for when the same variable name does or doesn't refer to the same thing are called scope rules.

Certain constructs in the language introduce scope blocks, which are regions of code that are eligible to be the scope of some set of variables. The scope of a variable cannot be an arbitrary set of source lines. Instead, it will always line up with one of these blocks. There are two main types of scopes in Julia, **global** scope and **local** scope, the latter can be nested. The scope blocks are:

- Global Scope
- Local Scope: Soft Local Scope
- Local Scope: Hard Local Scope

# Global Scope
Each module introduces a new global scope, separate from the global scope of all other modules; there is no all-encompassing global scope. Modules can introduce variables of other modules into their scope through the using or import statements or through qualified access using the dot-notation, i.e. each module is a so-called namespace. Note that variable bindings can only be changed within their global scope and not from an outside module.

# Local Scope 
A new local scope is introduced by most code-blocks. A local scope usually inherits all the variables from its parent scope, both for reading and writing. There are two subtypes of local scopes, hard and soft, with slightly different rules concerning what variables are inherited. Unlike global scopes, local scopes are not namespaces, thus variables in an inner scope cannot be retrieved from the parent scope through some sort of qualified access.

The following rules and examples pertain to both hard and soft local scopes. A newly introduced variable in a local scope does not back-propagate to its parent scope. For example, here the *z* variable is not introduced into the top-level scope:
```matlab
for i = 1:10
  z = i
end

z
```
{: .source}
```matlab
ERROR: UndefVarError: z not defined
```
{: .output}

(Note, in this and all following examples it is assumed that their top-level is a global scope with a clean workspace, for instance a newly started REPL.)

Inside a local scope, a variable can be forced to be a local variable using the **local** keyword:
```matlab
x=0;

for i = 1:10
  local x
  x=i+1
end

x
```
{: .source}
```matlab
0
```
{: .output}

Inside a local scope, a new global variable can be defined using the keyword **global**:
```matlab
for i = 1:10
  global z
  z=i
end

z
```
{: .source}
```matlab
10
```
{: .output}

# Soft Local Scope
In a soft local scope, all variables are inherited from its parent scope unless a variable is specifically marked with the keyword local. 

Soft local scopes are introduced by for-loops, while-loops, comprehensions, try-catch-finally-blocks, and let-blocks. There are some extra rules for Let Blocks and for For Loops and Comprehensions.

In the following example the x and y refer always to the same variables as the soft local scope inherits both read and write variables:
```matlab
x, y = 0, 1;

for i = 1:10
  x=i+y+1
end

x
```
{: .source}
```matlab
12
```
{: .output}
Within soft scopes, the global keyword is never necessary, although allowed. 


# Hard Local Scope
Hard local scopes are introduced by function definitions (in all their forms), struct type definition blocks, and macro-definitions.

In a hard local scope, all variables are inherited from its parent scope unless:
- an assignment would result in a modified global variable, or
- a variable is specifically marked with the keyword local.

Thus global variables are only inherited for reading but not for writing:
```matlab
x, y = 1, 2;

function foo()
  x=2
  return x+y
end;
```
{: .source}

```matlab
foo()
```
{: .source}
```matlab
4
```
{: .output}

while
```matlab
x
```
{: .source}
```matlab
1
```
{: .output}

An explicit global is needed to assign to a global variable:
```matlab
x=1;

function foobar()
  global x=2
end;

x
```
{: .source}
```matlab
2
```
{: .output}

Note that nested functions can behave differently to functions defined in the global scope as they can modify their parent scope's local variables:
```matlab
x,y = 1,2;

function baz()
  x=2  # introduces a new local
  function bar()
    x=10  # modifies the parent's x
    return x+y   # y is global
  end
  return bar()+ x  # 12+10 (x is modified in call of bar())
end;

baz()
```
{: .source}
```matlab
22
```
{: .output}

while 
```matlab
x,y
```
{: .source}
```matlab
(1, 2)
```
{: .output}

The distinction between inheriting global and local variables for assignment can lead to some slight differences between functions defined in local vs global scopes. Consider the modification of the last example by moving bar to the global scope:
```matlab
x,y = 1,2;

function bar()
  x = 10  # local
  return x + y
end;

function quz()
  x = 2  # local
  return bar()+x  # 12 + 2 (x is not modified)
end;

quz()
```
{: .source}
```matlab
14
```
{: .output}
while 
```matlab
x, y
```
{: .source}
```matlab
(1, 2)
```
{: .output}
Note that above subtlety does not pertain to type and macro definitions as they can only appear at the global scope. There are special scoping rules concerning the evaluation of default and keyword function arguments.


[Go to Module 7 (Wrapping up)]({{ site.baseurl }}/modules/07-wrapping-up)
{: .next-link}
