---
layout: post
title: Triathalon - INOI 2012
---

[Question Link](https://www.codechef.com/INOIPRAC/problems/INOI1201)

### Overview

This question came in INOI in the year 2012 and was a basic question with a simple twist. Any experienced programmer could just take one look at this question and get to the solution immediately. However, when I first saw this question(starting as a beginner in competetive coding) the solution didn't come to me so easily. So, if you are beginner or even if you have a bit of an experience with coding and you dont get the solution after putting in your brains, chill. One important thing that you will, however, learn from this question is how to use your mind to _think systematically_.

### Understanding The Question

So the question tells us that there is some competition taking place in some town and the mayor of the town wants the competition to end **as soon as possible**. There are three parts to the competition: COBOL, pole vault, and donut-eating. We are told that only one person at a time can participate in **COBOL(which is the first event)** and there no limits for the latter ones. We already know beforehand the time required by each participant in each event. That is all there is in the question and now we need to find a way to solve it.

### Approaching The Solution

_**I highly recommend you to try to find your own approach before reading mine**_

The first thing that we notice is that in the last two events any number of participants can take part at the same time. So, we dont need to take care of those two times for each participant as **separate values** we can directly add them and store them as one. We now just have to take care of the time for the COBOL event. We can start by sorting the values of the times of the participant in the descending order of time taken to get thorugh the first event. And now most of our work is almost done. You might think, **"WE ARE DONE!!"** but actually we cannot just add on these values together just yet to get to the solution. Why?? Because we have sorted the values not actually took advantage of this organisation. We just need to *think systematically*. So the thing we need to observe is that after adding the time of the first participant _(in our sorted list)_ to the total time _(intialised as 0)_, when we move on the next participant simply adding the values won't do any good because the time _**may overlap**_ with the preceding participant(this is true for any _ith_ participant). We need to add the time taken for the first event for the first event for every participant while _iterating over them in our sorted list_. The thing we _need to check_ before adding the time for the **last event(second + third)** is whether it is overlapping, and we do that by storing the **higher value of the sum till the last participant** and the **sum of all the times for the first event till that participant** plus the time taken by that participant in fininshing the last event. Think about it. This is a nice (one migth say classic) example of _Dynamic Programming_. 

If you need help with the code then here is mine-

```cpp
#include<bits/stdc++.h>
using namespace std;

// helper function for sorting in descending order
bool myfunc(pair<int, int> a, pair<int, int> b)
{
	return a.second > b.second;
}

int main()
{
	int n;
	cin >> n;
	int f = 2;
	pair<int, int> a[n];

	//taking the input
	for(int i = 0; i < n; i++)
	{
		int b, c;
		cin >> a[i].first >> b >> c;
		a[i].second = b+c;
	}
	//sorting according to the first event in descending order
	sort(a, a+n, myfunc);
	int m = 0;
	int x = 0;
	// applying our dynamic rule for this question
	for(int i = 0; i < n; i++)
	{
		x += a[i].first;
		m = max(x + a[i].second, m);
	}
	cout << m;
}
```
