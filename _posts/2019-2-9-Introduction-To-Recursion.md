---
title: Introduction to Recursion
---

<div style="text-align: justify">
  <b>Recursion</b> is an important concept and has can be used to solve hard questions efficiently. <b>Recursion</b> is defined as that process when a function calls itself <b><em>while it's getting executed</em></b>. It is pretty simple to understand so let's take a trivial example to understand this concept vividly.
<br>
<br>
  Let's consider a question which asks us to mke a program to find the <b>factorial,</b> of a number. Pretty simple huh!! Yes we can <b>directly use loops</b> and make the program like this. 
</div>

```cpp
#include<bits/stdc++.h>
using namespace std;

int main()
{
	int fact = 1;
	int n;
	cin >> n;
	for(int i = 1; i <= n; i++)
	{
		fact = fact*i;
	}
	cout << fact << endl;
}
```

<div style="text-align: justify">
  The above implementation is pretty straightforward and simple. Now let's think a about a <b><em>recursive</e></b> way to solve this very same question. <b>Remember</b> resursion means <b><em>"calling the same function within itself"</em></b>.
</div>

```cpp
#include<bits/stdc++.h>
using namespace std;

int fact(int n)
{
  //return 1 for base cases
	if(n == 1 || n == 0)
	{
		return 1;
	}//use mathematical definition to reach the solution
	else
	{
		return n*fact(n-1);
	}
}

int main()
{
	int n;
	cin >> n;
	cout << fact(n) << endl;
}
```

<div style="text-align: justify">
  Try to think how the above funtion works. Let's think <b>mathematically</b>. To find the factorial of a function what we do is <em>multiply every number from one through that number</em>. Let's take a number 4 and we have to find the factorial of it. In <b>mathematical</b> terms we can say it equal to <b>4*3*2*1</b>. Notice that factorial of 4 and can be written as 4*(factorial of 3). Using <b>this definition</b> we have defined our funtion above. We know for sure that if the number is 1 or 0 then it is 1. For all other numbers we use the <b>mathematical definition</b> to reach our answer. 
<br>
<br>
  One important thing to notice, however, is that any function <b>never returns the value until and unless it has calculated all the values</b>. So in our recursive function that the values won't start getting returned <b>till we reach our base case(which is n==1 || n==0)</b>. The function actually <b>waits</b> for the <b>succesive function</b> to return its value before the <b>original function returns anything</b>. And in the memory it looks like follows.
</div>
