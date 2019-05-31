---
layout: post
title: Chewing - ZCO 2015 (Dynamic Programming)
---

[Question Link](https://www.codechef.com/INOIPRAC/problems/INOI1201)

### Overview

<div style="text-align: justify">
This question came in ZCO in the year 2013 and 
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
