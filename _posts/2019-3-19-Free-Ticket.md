---
layout: post
title: Free Ticket - INOI 2014
---

[Question Link](https://www.codechef.com/INOIPRAC/problems/INOI1402)

### Overview

This question came in INOI in the year 2014 and was regarded by many as a pretty basic question. In fact, it was a trivial question if one had the basic knowledge of graphs. This question, however, is a nice example for beginners and introduces them to one of the most important graph concept: *Dijkstra's Algorithm.*

### Understanding The Question

The first thing we need to observe is that it is a graph question. We are told that Nikhil has won some competetion and is entitled to a free ticket. There is one twist, however; for any two cities that nikhil chooses, he would have to travel between them by the cheapest route. Now Nikhil, wants to **maximise** his prize. Here, the format of the question and the input strongly suggests that this is a graph problem. Here, the task at our hand is to find the **most expensive** flight sequence connecting two pair of cities while remaining cheapest for that pair. This all seems confusing but you will see soon how **simple** this is.

### Approaching the Solution

_**I higly reccomend you to try finding your own approach before reading mine**_

By now we know what is to be done(more or less). We can start by developing a simple **bi-directional** graph using an **adjacency list**(I personally prefer this over the matrix because of all the simplicity). After this step we can store all the connected cities in our graph. Now comes the thinking part. We are supposed to find *"the **most expensive** flight sequence connecting two pair of cities while remaining cheapest for that pair"* which seems confusing but let's go step by step. We can firstly find the cheapest route between **all** of the pairs of cities. For this we can use *Dijkstra's Algorithm*(we can use Belman Ford or Flloyd Warshall too!!!.... but our time constraints do not restrict the use of brute force). Once we accomplish this task we are through with the problem. But **WAIT** we are supposed to find the most expensive fligth sequence. What can we do now?? Think. Try to think the answer now before going forward. I assume you have done that. We now just need to find that most expensixe flight sequence from our already computed cheapest routes between all pairs which can be accomplishes by a basic *linear search*(or use binary search if you are a perfectionist).

Hurray!! We are done. Easy was'nt it. All we needed was a basic knowledge of graph and a clear thought pattern.

If you need help with the code, then here is my solution-

```
#include<bits/stdc++.h>
using namespace std;

// To add an edge in a bidirectional graph
void addEdge(vector <pair<int, int> > adj[], int u, int v, int wt)
{
	adj[u].push_back(make_pair(v, wt));
	adj[v].push_back(make_pair(u, wt));
}
vector<int> lis;

// A utility function to find the vertex with minimum distance value, from
// the set of vertices not yet included in shortest path tree

int minDistance(int dist[], bool sptSet[], int V)
{
   // Initialize min value
   int min = INT_MAX, min_index;
  
   for (int v = 0; v < V; v++)
     if (sptSet[v] == false && dist[v] <= min)
         min = dist[v], min_index = v;
  
   return min_index;
}

//finds the nearest vertex that has not been visited
int find_min(vector<bool> visited, int dist[], int V)
{
	int m = INT_MAX;
	int pos = -1;
	for(int i = 0; i < V; i++)
	{
		if(!visited[i] && dist[i] != INT_MAX)
		{
			if(m > dist[i])
			{
				m = dist[i];
				pos = i;
			}
		}
	}
	return pos;
}

//finds the nearest vertex that has not been visited
int find_max(int dist[], int V)
{
	int m = 0;
	int pos = 0;
	for(int i = 0; i < V; i++)
	{
		if(m < dist[i])
		{
			m = dist[i];
			pos = i;
		}
	}
	return m;
}

// print the solution
int printSolution(int dist[], int V)
{
   printf("Vertex Distance from Source\n");
   for (int i = 0; i < V; i++)
      printf("%d :: %d\n", i, dist[i]);
}

//works only for positive weights for a source
void Djikstra(vector<pair<int,int> > adj[], int src, int V)
{
    // Mark all the vertices as not visited
    vector<bool> visited(V, false);
 
 	int dist[V];     // The output array.  dist[i] will hold the shortest
                      // distance from src to i
                      
    for (int i = 0; i < V; i++)
    {
        dist[i] = INT_MAX;
    }

    dist[src] = 0;                  
    while(true)
    {
        src = find_min(visited, dist, V);
        int pos = 0, v = 0, w = 0;
        if(src == -1)
        {
        	break;
		}
		//mark the current node as visited
        visited[src] = true;
		for (auto it = adj[src].begin(); it!=adj[src].end(); it++)
		{
			v = it->first;
			w = it->second;
			if(dist[v] > dist[src] + w)
			{
				dist[v] = dist[src] + w;
			}
		}
    }
    lis.push_back(find_max(dist, V));
}
int main()
{
	int V, f;
	cin >> V >> f;
	vector<pair<int, int> > adj[V];
	for(int i = 0; i < f; i++)
	{
		int a, b, c;
		cin >> a >> b >> c;
		addEdge(adj, a-1, b-1, c);
	}
	for(int i = 0; i < V; i++)
	{
		Djikstra(adj, i, V);
	}
	int m = 0;
	for(int i = 0; i < V; i++)
	{
		m = max(m, lis[i]);
	}
	cout << m;
}
```
