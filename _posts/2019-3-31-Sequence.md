---
layout: post
title: Sequence Land - INOI 2013 (Graphs)
---

[Question Link](https://www.codechef.com/INOIPRAC/problems/INOI1302)

### Overview

<div style="text-align: justify">
This question came in <b>INOI</b> in the year 2013 and was a bit <b>complicated</b>. The question needs a <b>proper understanding of traversal techniques of graphs</b>. That's the main thing that you will need. Apart from this its pretty straightforward. So we are told that there is this place where <b>"N"</b> people live and they are identified with an <b>array of unique integers</b>. Now someone is a relative of someone else if they have <b>at least "K" common integers</b> in their id. Using this we are supposed to determine the number of people in the <b>extended family</b> of the <b><em>President</em></b> of Sequence Land. 
</div>

### Approaching The Solution

_**I highly recommend you to try to find your own approach before reading mine**_

<div style="text-align: justify">
As discussed, this question will use <em><b>BFS or DFS</b></em>. I am using BFS in my solution but <b>either is fine</b>. So let's just look at the question. It's obvious that we have to check if the President is in a <b>direct relationship with any of the residents</b>. We can do that by comparing each elemnt of the President to that of all the residents <em><b>(We can use binary search variation too but the time constraints don't actually require it)</b></em>. So we can just count all the direct relatives and then keep their track in an array so that we don't recount them. The last thing is we have to check if any <b>remaining residents</b> is a direct relative of any of the members of extended family of the President. Once we complete doing this we will have our answer. Now to actually make this happen, we will treat all of these <b>residents as nodes in a graph</b>. Then all the residents who are actually in the <b>extended family</b> of the President <em><b>(or of any of the other members who are in the direct or extended family of the President)</b></em> can be pushed into in a queue <b>(BFS approach!!)</b> and their relatives can be found out too. When the queue is empty then we will get our answer.
</div>

If you need help with the code then here is mine-

```cpp
#include<bits/stdc++.h>
using namespace std;

typedef long long ll;
ll n, k;
ll M = -123456789876;

int main()
{
    ios_base::sync_with_stdio(false);
    cout.tie(NULL);
    cin.tie(NULL);
    cin >> n >> k;
    map<ll, ll> m[n];
    vector<ll> a[n];
    for(int i = 0; i < n; i++)
    {
        ll x;
        cin >> x;
        for(int j = 0; j < x; j++)
        {   
            ll y;
            cin >> y;
            a[i].push_back(y);
            m[i][y] = M;
        }
    }
    bool visited[n];
    memset(visited, false, sizeof(visited));
    queue<ll> q;
    q.push(0);
    ll count = 1;
    visited[0] = true;
    while(!q.empty())
    {
        ll src = q.front();
        q.pop();
        for(int  i = 0; i < n; i++)
        {
            if(!visited[i])
            {
                ll c = 0;
                for(auto it = a[src].begin(); it != a[src].end(); it++)
                {
                    if(m[i].find(*it) != m[i].end())
                    {
                        c++;
                        if(c == k)
                        {
                            // cout << i << " ";
                            q.push(i);
                            visited[i] = true;
                            count++;
                            break;
                        }
                    }
                }
            }
        }
    }
    cout << count << endl;
}
```
