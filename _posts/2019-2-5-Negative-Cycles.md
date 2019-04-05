---
title: Detecting Negative Cycles
---

<div style="text-align: justify">
This concept is going to be fairly easy if you know the <b><a href="https://vaibhav2001.github.io/Bellman/">Bellman Ford Algorithm</a></b>. We already know that we run the Bellman Ford Algorithm it is confirmed that we have the shortest path from the source to every other vertex given that we dont have a negative edge. However, if we do have a <b>negative edge</b> the <b>Bellman Ford Algorithm</b> will cease to work correctly but at the same time it will give us an <b>interesting conclusion</b>: if we run try to <em><b>update</b></em> all of the value of the shortest distnace of each nodes one more time we will have a different answer because there is bound to be a shorter path along the <b>negative cycle</b>. This will happen indefinitely but we only need to run it one more time and if any value is changed in the <b>Vth</b> iteration then we can safely conclude that we indeed have a negative cycle.
<br>
<br>
The code is pretty straightforward too. Here is my code.
</div>
  
```cpp
//this has to be run after the Bellman Ford Algorithm
//this is the Vth iteration
for(int i = 0; i < V; i++)
{
	if(dist[i] == INT_MAX)
	{
		continue;
	}
	for(auto it = adj[i].begin(); it != adj[i].end(); it++)
	{
		v = it->first;
		w = it->second;
		//cheching if there is any change
		if(dist[v] > dist[i] + w)
		{
			flag = 0;
			break;
		}
	}
}
if(flag)
{
	//if there is no negative cycle then print the solution
	cout << "Vertex Distance from Source" << endl;
	for (int i = 0; i < V; i++)
	{
	    cout << i << " " << dist[i];
	}
}
else
{
	cout << "Negative Cycle" << endl;;
}
```
