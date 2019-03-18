---
title: Introduction To Graphs
---

### What Are Graphs??

<div style="text-align: justify">
It's difficult to directly explain what a graph is and what its utility is. So let's take a practical example.
</div>

![Airline Network](/images/Graph_1.png "Airline Network")

<div style="text-align: justify">
Suppose we have a network of airlines connecting a bunch of cities. Now each city may have one more airlines that stop there or depart from there. This network of airlines can be efficiently described using graphs. The above image shows a graph for our example. There are five cities. It's a pretty straightforward network. We can go almost anywhere from any city <b>except</b> the pink one. Our network is denoted by <b>arrows</b> in which the <em>head points to the destination</em> and <em>tail shows the take-off city</em>. Only the pink one has no arrow with its tail pointing towards it (the city), which signifies that we cannot fly anywhere from there. The lines may overlap as it does not diturb the meaning of our graph. Any of these cities can be set in any configuration but as long as the arrows are same the meaning won't change. For example see at the representation of the graph below. It has the <b>same meaning just a different orientation</b>. 
</div>

![Airline Network](/images/Graph_1re.png "Airline Network")

<div style="text-align: justify">
The general terminology of graphs is as follows: each element is know as a <b>vertex or a node </b><em>(in this case each element is a city)</em>, and the arrow connecting the two vertices is known as an <b>edge</b> <b><em>(It is very important to note that the direction of the edge is very crucial in determining the whether it is possible to go from one edge to another or not).</em></b> We can see that there is no limit in the number of edges that can enter into a vertex.
</div> 

### Types of Graphs

<div style="text-align: justify">
There are basically two types of graphs: <em><b>Unweighted Graph</b></em>, and <em><b>Weighted Graph</b></em>. 
<br>
<br>
An <em><b>unweighted graph</b></em>, is a graph which has vertices and edges, but the <b>edges do not have any value associated with it</b>. The above example was a perfect representation of an unweighted graph. The above graph showed a network of flights connecting 5 cities but didn't give us any other information.
<br>
<br>
A <em><b>weighted graph</b></em>, on the other hand, is a graph which has edges with <b>some meaningful value associated with it</b>. Let's just take the above example example and make a modification.
</div>

![Weighted Airline Network](/images/Graph_2.png "Weighted Airline Network")

<div style="text-align: justify">
This graph now has values associated to it. Let's say these values are the <b><em>durations of the flight</em></b>. Notice there is a <b>negative edge</b>, which seems absurd, which it technically is, however, I deliberately put it there to <b>emphasise on the fact that it is possible</b> and you might encounter such scenarios in some problems.
<br>
<br>
Graphs might be divided into two other types: <b>directed</b> and <b>undirected</b>. They are not that difficult but understanding them is <em><b>very crucial</b></em>. <b>Undirected graphs</b> are those in which if it is possible to go from <b>node A to another node B</b> then it is <b>also possible to go from node B to node A</b>. <b>Directed graphs</b> are those in which it is not necessarily true that if it is <b>possible to go from node A to node B then it is possible to go from node B to node A</b>.
<br>
<br>
So, we are now <b>DONE</b> with basics of graph and now we can move on to ways of <em><b>traversing</b></em> a graph.
<br>
<br>
</div>

<div style="text-align: justify">
Refer the code below if you don't have any idea about constructing a graph.
</div>

```cpp
//this in an unweighted graph
//where N is the number of nodes in the graph
//this is basically a array of lists or vectors where every ith location stores all the nodes connected to it.
vector<int> adj[N];

//for weighted graph
//here the pair stores the connected nodes as well as the the weight of the edge
vector<pair<int, int> adj[N];
```

<div style="text-align: justify">
And here is how you can add an edge in the graph.
</div>

```cpp
//for an unweighted garph
//note that you can move from u to v and not v to u
void addEdge(vector<int> adj[], int u, int v)
{
    adj[u].push_back(v);
}

//for a weighted graph
void addEdge(vector <pair<int, int> > adj[], int u, int v, int wt)
{
	adj[u].push_back(make_pair(v, wt));
}
```
