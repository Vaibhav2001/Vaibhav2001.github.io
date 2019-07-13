---
layout: post
title: The 0-1 Knapsack Problem
---

### Question

You are thief. WOOH!! You need to steal some things from a house. You already know the amount of weight that your knapsack can carry. Let's say it's <b>W</b>. Now you have <b>N items</b> in front of you and you know the weight of all of these. All of these have different monetary values.
<br>
<br>
Now your job is to is to steal the things which will give you give you the maximum value without exceeding the capacity of the knapsack.

### Overview

<div style="text-align: justify">
This is one of the classic questions that require <b>DP (Dynamic Prgramming) or Recursion</b>, so I thought that it is important to discuss it. This question is a very popular one and is genrally one of the first questions of DP that many people encounter. I am going to discuss <b>recursive method</b> to solve the question and also give a hint about the DP method.
</div>

### Approaching The Solution

_**I highly recommend you to try to find your own approach before reading mine**_

<div style="text-align: justify">
The first thing you should do is keep the <b>computer aside</b> and take out your <b>pen and a piece of paper</b>. Because many of us will be tempted to make an if-else construct to solve this question if we are not aware of DP. If you <b>make some examples</b> and try solving some questions you might get some idea of what the question requires you to do. 
<br>
<br>
Remember from <b>"The Coin Change Problem"</b> that the solution in these types of questions is never greedy so you have to think of an optimal solution. I will discuss in the future that how <b>DP and recursion are essentially the same thing</b> but for now let's debunk the question and start working towards our solution. 
<br>
<br>
So what is <b>recursion</b>? If you recall recursion is one <b>function calling itself while its running</b>. So now that's a big hint. It tells us that we have to do something again and again and that will help us reach our answer.  
<br>
<br>
Recursion requires us to make <b>base cases</b>. So we need to first find our base cases. Before that let's talk about the variables that we might need. The <b>first variable</b> is obviously the <b>amount of weight that our knapsack can still carry</b> and the other one is an <b>iterator</b>. You can also use a size variable (although it's unecessary). The base case would be when the number of <b>remainig elements(size) is 0 (or the iterator is at the end)</b> or when the <b>remaining capacity of the knapsack is 0</b>. If this happens the we can smply return 0 <b>(as nothing more is to be added)</b>.
<br>
<br>
Now comes the last part (and the one which actually makes changes to our answer). 
<br>
<br>
This might seem like a lot of work but later you will realise that it's the first step in a long flight of stairs.
</div>

If you need help with the code then here is mine-

```cpp
#include<bits/stdc++.h>
using namespace std;
int main()
{
    //input
    int s, n;
    cin >> s >> n;
    int a[n];
    for(int i = 0; i < n; i++)
    {
        cin >> a[i];
    }
    int m[s+1];

    //intialise to max 
    for(int i = 0; i < s+1; i++)
    {
        m[i] = numeric_limits<int>::max();
    }

    //Dyamic Programming
    m[0] = 0;
    for(int i = 1; i <= s; i++)
    {
        for(int j = 0;j < n; j++)
        {
            if(a[j] <= i)
            {
                if(m[i-a[j]]+1 < m[i] && m[i-a[j]] != INT_MAX)
                {
                    m[i] = m[i-a[j]]+1;
                }
            }
        }
    }
    cout << m[s];
    return 0;
}
```
