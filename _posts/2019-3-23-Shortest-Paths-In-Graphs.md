---
title: Shortest Paths In Graphs
---

<div style="text-align: justify">
Computing <em><b>shortest path in graphs</b></em> is an essential concept. When you encounter problems in some coding competition it will generally be a combination of <b>shortest paths and traversal</b>. There <b>three</b> algorithms that are <em><b>essential</b></em> to learn to compute shortest paths: <em><b>Dijkstra's Algorithm, Bellman Ford Algorithm and Floyd Warshall Algorithm</b></em>.
</div>

### Dijkstra's Algoritm

![Edsger W. Dijkstra](/images/Edsger_Wybe_Dijkstra.jpg "Edsger W. Dijkstra")

<div style="text-align: justify">
This algorithm is named after a dutch computer scientist Edsger W. Dijkstra. This algorithm provides us with an efficient way to compute the shortest path in a graph with <b>NON NEGATIVE</b> edges. It is an interesting concept and is very useful to solve <em><b>real life problems</b></em>. Even some <b>map apps</b> that we use these days rely on it. Let's look at an example of a <b>road network</b>.
</div>

![Road Network](/images/Shortest.png "Road Network")

<div style="text-align: justify">
  The above graph shows an <b>intricate network</b> of roads in a city. Suppose we have to the find the shortest path from the <b>green node</b> to the <b>blue one</b>. Now, naturally a naive approach would be to move first towards the <em><b>yellow node since the path length is smaller</b></em> than that from <b>green to orange</b>. However, once we study the network it seems that we have to do just the opposite. Here is where <b>Dijkstra's algorithm</b> comes in. 
<br>
<br>
  The best way to imagine <b>Dijkstra's algorithm</b> running is by <b>imagining</b> that we fire up the source node and now the <em><b>fire travels along all the edges at a uniform speed<b><em>.
</div>
