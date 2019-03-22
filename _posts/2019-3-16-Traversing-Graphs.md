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
  Before moving onto these <b>techniques</b>, we shall first look towards some <em><b>general terminology</b></em> associated with graphs that will be referred to again and again in the next section. <b>Every node</b> from which it is possible to move to another node which is <b>adjacent</b> to it <em><b>through only one edge</b></em> is known as the <b>parent node</b> of that adjacent node, and that adjacent node is known as the <b>child node</b>. Looking at the above graph we can say that the <b>green vertex is a parent of yellow node <em>ONLY</em></b> and the <em><b>pink vertex has no child</b></em>.
<br>
<br>
  Now let's get into more <em>detail</em> about out search techniques which are essential componet in learning an understanding graphs.
</div>

### Breath First Search(BFS) 

<div style="text-justify">
  <em><b>Breadth First Search</b></em> is the traversing technique in graphs in which we first <b>visit<em> (reach)</em></b> <b>all the children</b> of a particular node and then <b>visit all the children of the first node</b> in the list. The way in whcih we develop the list is that of a queue. We can using <b>any particular node</b> and <b>BFS</b> will tell us if it is possible to <b>reach a <em>particular node</em> from that node</b>.
</div>

![Airline Network](/images/Graph_1.png "Airline Network")

<div style="text-justify">
  Let's take our original example of the airline network to understand this concept more vividly. Suppose, we want to know if it is possible to reach the <b>YELLOW node from our RED node</b>. So here our <b>source vertex</b> is the red node. So according to our discussion above we have to take an empty queue and visit all the clidren of the red node. First thing that we have to do is to store that <b>we have already visited the source node <em>(red node)</em></b>. Red node has two  children and we visit them and <b>push</b> them node into our queue. After this our queue and visited array will look like this.
</div>

![BFS 1](/images/BFS_1.png "BFS 1")

<div style="text-justify">
  
</div>
