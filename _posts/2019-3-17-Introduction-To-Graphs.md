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
<br>
<br>
The general terminology of graphs is as follows: each element is know as a <b>vertex or a node </b><em>(in this case each element is a city)</em>, and the arrow connecting the two vertices is known as an <b>edge</b> <b><em>(It is very important to note that the direction of the edge is very crucial in determining the whether it is possible to go from one edge to another or not).</em></b> We can see that there is no limit in the number of edges that can enter into a vertex.
</div> 
