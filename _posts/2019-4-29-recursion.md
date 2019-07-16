---
layout: post
title: Recursion

### What is Recursion??

<div style="text-align: justify">
Recursion is a useful and powerful tool. The name Recursion suggest recurring, which means repetition of something. In terms of coding it is a concept: a function calling itself during it's runtime. 
<br>
<br>
It is used in solving many questions in mathematics and coding. The only condition is that it can be used only in those places where there is an optimal structure. This optimal structure for recursion is any function which is dependent in some way or other on some value which can be computed using very same function with different paramters. Many say that recursion is basically a formatted loop but in actualiy recursion is much more powerful.
</div>

### The Fibbonaci series

<div style="text-align: justify">
It is one of the simpler questions used to demonstrate recursion. Fibbonaci series is a series that goes like this: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34.....and so on. If it is to be represented as a function then we can say-
</div>

```
f(n) = f(n-1) + f(n-2); such that n > 2
f(0) = 0
f(1) = 1
``` 
<div style="text-align: justify">
So we can clearly see that the result of the fucntion that finds our fibbonaci term is dependent on the same function with different parameters. 
<br>
<br>
Now the next most important thing in recursion is a base case. These base cases are very crucial for recursion as it tells the function when to stop recurring and return a solid numerical value. In this question we have two base cases for n = 0 and n = 1. To make a complete function for this question we can do something like this.
</div>

```cpp
#include<bits/stdc++.h>
using namespace std;

int fibbonaci(int n)
{
    if(n == 0)
    {
        return 0;
    }
    else if(n == 1)
    {
        return 1;
    }
    else
    {
        return fibbonaci(n-1) + fibbonaci(n-2);
    }
}
```

### Questions on Recursion

<div style="text-align: justify">
There are some great questions on recursion to get you started. I have solved some and I will link them down below.
</div>

[The Coin Change Problem](https://www.vaibhav.github.io/coin)

<div>
    <br>
</div>

[The 0-1 Knapsack Problem](https://www.vaibhav.github.io/knapsack)

<div>
    <br>
</div>

[Triathalon - INOI 2012](https://www.vaibhav.github.io/Triathalon)

<div>
    <br>
</div>

[Bellman Ford](https://www.vaibhav.github.io/Bellman)