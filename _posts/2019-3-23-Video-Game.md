---
layout: post
title: Video Game - ZCO 2014 (Implementation)
---

[Question Link](https://www.codechef.com/ZCOPRAC/problems/ZCO14001)

### Overview

<div style="text-align: justify">
	This question came in <b>ZCO 2014</b> and was purely based on <b>implementation</b>. The only <b>prerequisite</b> according to me for this particular question is a <b>basic knowledge of the essentials of programming</b>. This question falls into that rare category of questions, which only require you to follow every line bit by bit without applying brains. So the question basically tells us that we are playing a game in which we are given the <b>initial arrangements</b> of the blocks. Now, all we have to do is to tell the final state of the blocks after <b>executing a list of commands</b>. 
</div>

### Approaching The Solution

_**I highly recommend you to try to find your own approach before reading mine**_

<div style="text-align: justify">
	The first thing that we can see is that there is no need of storing the blocks in stack data type. On the contrary, all we need is a <b><em>single-dimension array</em></b> and that would be enough to meet our requirements. We need a simple <b>loop</b> that will keep taking the inputs till the 0 is inputted. We just to follow the commands and <b>NOT</b> apply our brains and this can be achieved with <b>two</b> variables: <b>an integer variable</b> which will keep track of its <b><em>position</em></b> and <b>a boolean variable</b> which will store whether the crane is <b>loaded</b> or not. By doing this our work will be done!!
</div>

If you need help with the code then here is mine-

```cpp
#include<bits/stdc++.h>
using namespace std;
int main()
{
	int n, h;
	cin >> n >> h;
	int a[n];
	for(int i = 0; i < n; i++)
	{
		cin >> a[i];
	}
	int b;
	int x = 0;
	bool pick = false;
	while(true)
	{
		cin >> b;
		if(b == 0)
		{
			break;
		}
		else if(b == 1 && x != 0)
		{
			x = x-1;
		}
		else if(b == 2 && x != n-1)
		{
			x = x+1;
		}
		else if(b == 3 && !pick && a[x] != 0)
		{
			pick = true;
			a[x]--;
		}
		else if(b == 4 && pick && a[x] != h)
		{
			pick = false;
			a[x]++;
		}
	}
	for(int i = 0; i < n; i++)
	{
		cout << a[i] << " ";
	}
}
```
