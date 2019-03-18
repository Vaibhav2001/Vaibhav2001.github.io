---
title: Traversing Graphs
---

### What is Traversal?

<div style="text-justify">
<b>Traversal</b> in a graph can be defined as moving from one <b>node</b> of the graph to any other node along its <b>edges</b>. It can be understood by looking at our <em><b>earlier example</b></em> of the airline network.
</div>

![Airline Network](/images/Graph_1.png "Airline Network")

<div style="text-justify">
We can see it is possible for us to move from green to red by follwing the edges. We first move from <em><b>green to yellow</b></em> and then from <em><b>yellow to red</b></em>. We can move from red to yellow in two ways if you see clearly. Thus, we can say that <b>traversal through graphs</b> is nothing but following the <em><b>paths</b></em> in the graph made by the <b>edges</b>. There are two ways of traversal in a graph: <em><b>Breadth First Search(BFS)</b></em> and <em><b>Depth First Search(DFS)</b></em>. 
<br>
<br>
  Before moving onto these <b>techniques</b>, we shall first look towards some <em><b>general terminology</b></em> associated with graphs that will be referred to again and again in the next section. <b>Every node</b> from which it is possible to move to another node which is <b>adjacent</b> to it <em><b>through only one edge</b></em> is known as the <b>parent node</b> of that adjacent node, and that adjacent node is known as the <b>child node</b>. Looking at the above graph we can say that the <b>green vertex is a parent for yellow node <em>ONLY</em></b> and the <em><b>pink vertex has no child</b></em>.
<br>
<br>
  Now let's get into more <em>detail</em> about out search techniques which are essential componet in learning an understanding graphs.
</div>

### Breath First Search(BFS)

