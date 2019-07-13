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
Now comes the last part (and the one which actually makes changes to our answer). Intially, in the main function we can call our function with the remaining weight as the total capacity and the iterator at 0. Then if none of the base cases are met we would first check if the weight of the element is greater than the remaining weight. If it is then we can skip that element. If not then we have two conditions: either we have to choose the element or we don't. If we choose it the our ultimate answer will be the sum of the original value, the value of the item and the value that we might get from other elements. If we do not choose this element then we can just skip it. If we store the max of these values and keep sending it to the next call of the function we will have our answer.
<br>
<br>
This might seem like a hoax but believe me it works. Take a smal example, use your pen and paper and try to solve the question using this approach. You will see that we are checking for all possible cases in a smart way by avoiding obvious wrong answers. How?? By using our base cases.
<br>
<br>
</div>

If you need help with the code then here is mine-

```cpp
#include<bits/stdc++.h>
using namespace std;

typedef long long ll;
ll n, w;
ll val[1000];
ll wt[1000];

ll knap(int w, int size, int i)
{
    if(size == 0)
    {
        return 0;
    }
    if(w == 0)
    {
        return 0;
    }
    if(wt[i] > w)
    {
        return knap(w, size-1, i+1);
    }
    ll exc = knap(w, size-1, i+1);
    ll inc = val[i] + knap(w-wt[i], size-1, i+1);
    return max(exc, inc);
}

int main()
{
    cin >> n >> w;
    for(int i = 0; i < n; i++)
    {
        cin >> val[i];
    }
    for(int i = 0; i < n; i++)
    {
        cin >> wt[i];
    }
    ll dp[n+1][w+1];
    for(int i = 0; i <= n; i++)
    {
        dp[i][0] = 0;
    }
    for(int j = 1; j <= w; j++)
    {
        dp[0][j] = 0;
    }
    for(int i = 1; i <= n; i++)
    {
        for(int j = 1; j <= w; j++)
        {
            if(wt[i-1] <= j)
            {
                dp[i][j] = max(val[i-1] + dp[i-1][j-wt[i-1]], dp[i-1][j]);
            }
            else
            {
                dp[i][j] = dp[i-1][j];
            }
        }
    }
    cout << dp[n][w] << endl;
    cout << knap(w, n, 0) << endl;
}
```
