---
layout: post
title: Smart Phone - ZC0 2014 (Based on Sorting)
---

[Question Link]((https://www.codechef.com/ZCOPRAC/problems/ZCO14003))

### Overview

<div style="text-align: justify">
	This question came in <b>ZCO 2014</b> and was a bit of a easy question, however, for starters these problems can be <em><b>new and overwhelming</b></em>. So we are the budget for N people and we are actually designing a new smart phone app. <b>How exciting is that!!!</b>. Now we are supposed to also find out the <b>maximum revenue</b> that we can earn. So that's really not that difficult if you have the <b>right</b> tools with you. This question is based on <em><b>simple sorting and traversal</b></em> of the array but it might be a bit weird for newbies so <b>first think of a solution</b> in your head using all the hints that I already gave you and then move forward.
</div>

### Approaching The Solution

_**I highly recommend you to try to find your own approach before reading mine**_

<div style="text-align: justify">
	The first thing that we can see is that obviously we have to <b>sort</b>, and after sorting half our work is already done for us. We can sort in <b>increasing order or decreasing order</b> as it doesn't matter which way you do it. I chose the former one. After doing that all you need to do is to start from the 1st postion and traverse all the way upto the end. Now whenever we land at the <em><b>ith</b></em> budget then there are <em><b>(n-i+1)</b></em> people who can afford it, so all we have to do is to check which gives the <b>maximum value</b> after multiplication by the number of consumers who can afford it. By doing this we will get our answer efficiently.
</div>

If you need help with the code then here is mine-

```cpp
#include<bits/stdc++.h>
using namespace std;
int main()
{
	int n;
	cin >> n;
	int a[n];
	for(int i = 0; i< n; i++)
	{
		cin >> a[i];
	}
	sort(a, a+n);
	long long max = 0;
	for(int i = 0; i < n; i++)
	{
		long long c = (long long)a[i]*(n-i);
		if(max < c)
		{
			max = c;
		}		
	}
	cout << max;	
	return 0;
}
```
