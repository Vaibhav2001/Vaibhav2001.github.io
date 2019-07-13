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
Remember from <b>"The Coin Change Problem"</b> that the solution in these types of questions is never greedy so you have to think of an optimal solution. I will discuss in the future that how DP and recursion are essentially the same thing but for now let's debunk the question and start working towards our solution. 
<br>
<br>
So what is <b>recursion</b>? If you recall recursion is one function calling itself while its running. So now that's a big hint. It tells us that we have to do something again and again and that will help us reach our answer.  
<br>
<br>
Recursion requires us to make base cases 
<br>
<br>
Now comes the last part (and the most trickiest). We can now start <b>traversing our grid in top to down and left to right manner</b>. For all values of <b>j which are less than ith coin's value we can copy the value of the position i-1</b>, j. WHY?? Because it is like we are not even using that coin so the answer that we have obtained so far <b>won't change even if we have this new coin</b>. Now for all other values where j is greater than ith coin's denomination we have two choices: <b>either we don't use this coin, which would require us to do what we did in the above scenario, and the other choice that we have is that we use that use this coin.</b> So, to make a decision we would compare the value from the above cell to the value of <b>grid[i-1][j-c[i]] + 1 (we compare with this value because what we are doing is that subtracting the value of the coin from the change as that is already given and then using the best value that is avaiable for the left over change)</b>. We choose the lesser of the two values and in the end our answer is in <b>grid[N-1][C] (this position represnts that position where j is equal to our change and all the coins are take into account)</b>.
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
