---
layout: post
title: Chewing - ZCO 2015 (Sorting and Maths)
---

[Question Link](https://www.codechef.com/ZCOPRAC/problems/ZCO13003)

### Overview

<div style="text-align: justify">
This question came in ZCO in the year 2013 and was based on logic and simple maths. The question basically requires you to think and that's all you need honestly. We are introduced to two kids: Hobbes and Calvin. Now Calvin has received a challenge to chew gums (I know weird). Calvin has to chew as many combinations of the available gums as possible. However, he knows that he cannot chew two gums whose hardness quotient is more than <b>"K"</b>. We can easily do brute force to find the answer, but the time contsrants restrict that. So, we just have to think logically. and i guess it will all be straightforward after that.
</div>

### Approaching The Solution

_**I highly recommend you to try to find your own approach before reading mine**_

<div style="text-align: justify">

</div>

If you need help with the code then here is mine-

```cpp
#include <bits/stdc++.h>
using namespace std;
 
int main() {
     long long int n,k;
     cin >> n >> k;
     long long int a[n];
     for(int i = 0;i < n;i++)cin >> a[i];
     sort(a,a+n);
     long long int i = 0,j = n-1,ans = 0;
     while(i < j){
         if(a[i] + a[j] < k){
             ans += j-i;
             i++;
         }
         else j--;
     }
     cout << ans;
     
	return 0;
}
```
