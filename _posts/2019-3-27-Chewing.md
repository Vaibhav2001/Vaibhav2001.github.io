---
layout: post
title: Chewing - ZCO 2015 (Sorting and Maths)
---

[Question Link](https://www.codechef.com/ZCOPRAC/problems/ZCO13003)

### Overview

<div style="text-align: justify">
This question came in <b>ZCO</b> in the year 2013 and was based on <b>logic and simple maths</b>. The question basically requires you to <b>think</b>and that's all you need honestly. We are introduced to two kids: Hobbes and Calvin. Now Calvin has received a challenge to chew two gums at the same time(I know weird). Calvin has to chew <b>as many combinations</b> of the available gums as possible. However, he knows that he cannot chew two gums whose <b>"hardness quotient"</b> is more than <b>"K"</b>. We can easily do <b>brute force</b> to find the answer, but the <b>time contsrants restrict that</b>. So, we just have to <b>think logically</b>, and i guess it will all be straightforward after that.
</div>

### Approaching The Solution

_**I highly recommend you to try to find your own approach before reading mine**_

<div style="text-align: justify">
Now, the <b>first thing</b> that we need to take care of in these types of questions is that we have to <b>observe what is happening</b> and generally it's easy to spot. So, we know that we have to check whether the <b>sum of two numbers is greater than a particular number</b>. Here is where the <b><em>sorting</em></b> will help us. It will be much easier to accomplish that task once the array is sorted. Now all we have to do is <b>count</b>. However, if we follow our conventional way it can be tricky and time consuming <b><em>(as we would have to use two loops)</em></b>. So, we need to notice something simple: <b><em>if the sum of the lower number with the higher number meets our condition then the combination of that lower number with all of the numbers in between those two nunmbers will also satisfy the condition</em></b>. The other thing is that <b><em>if the sum with the larger number is exceeding K then we can choose the number which is lower than that</em></b>. Combine these two logics and there you have it.
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
