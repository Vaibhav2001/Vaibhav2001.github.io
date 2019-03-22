---
title: Traversing Graphs
---

### What is Traversal?

<div style="text-justify">
<b>Traversal</b> in a graph can be defined as moving from one <b>node</b> of the graph to any other node along its <b>edges</b>(If you do not know the basics of graphs first <a href="https://vaibhav2001.github.io/Introduction-To-Graphs/">click here</a>. It can be understood by looking at our <em><b>earlier example</b></em> of the airline network.
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
  Here, the arrow indicates that the blue node is at the front. We see that we have already visited three nodes and we have to <b>process two nodes</b>. The front node is the <b>blue node</b> and we make it our <b>source vertex</b>. We now have to repeat the process and visit all of its children. After this our queue and visited array will look like this.
</div>

![BFS 2](/images/BFS_2.png "BFS 2")

<div style="text-justify">
  Note that green node is not there twice in our queue because it is already visited. Now we have to repeat the above process with the node in the front i.e. <b>the green node</b>. After this our queue and visited array will look like this.
</div>

![BFS 3](/images/BFS_3.png "BFS 3")

<div style="text-justify">
  Now we have visited the yellow node and we can <b>break out of the loop</b> and <b>print yes</b>.
  <br>
  <br>
  So, we see BFS is a simple algorithm with not much complexity. If you need help with the code you can see my code.
</div>

```cpp
//BFS
//s is the current node
void BFS(vector<int> adj[], int s, int N)
{
    // Mark all the vertices as not visited
    vector<bool> visited(N, false);

    // Create a queue for BFS
    list<int> queue;
 
    // Mark the current node as visited and enqueue it
    visited[s] = true;
    queue.push_back(s);
 
    while(!queue.empty())
    {
        // Dequeue a vertex from queue and print it
        s = queue.front();
        cout << s << " ";
        queue.pop_front();
 
        // Get all adjacent vertices of the dequeued
        // vertex s. If a adjacent has not been visited, 
        // then mark it visited and enqueue it
        for (int i = 0; i < adj[s].size(); ++i)
        {
            if (!visited[adj[s][i]])
            {
                visited[adj[s][i]] = true;
                queue.push_back(adj[s][i]);
            }
        }
    }
}
```

### Depth First Search(DFS) 

<div style="text-justify">
  <em><b>Depth First Search</b></em> is the traversing technique in graphs can be described as a <em><b>recursive technique</b></em> in which we <em><b>first visit the first child of the current node and then change the current node to the first child</b></em>. When this <b>cycle ends</b> then we visit the second node of the last visited node <em>(if it does not exist we keep <b>moving backwards</b>)</em> This all seems wordy and complicated but will be pretty <b>simple</b> when you start getting the essence of it. Let's look at ur previous example.
</div>

![Airline Network](/images/Graph_1re.png "Airline Network")

<div style="text-justify">
  "HEY!!! This is not same as the previous example", one might think. Think again. Recall the last lesson. Just changing the orientation of nodes won't change the meaning of the graph. So now let's see if it is possible to reach the <b>YELLOW node from the RED node</b>. So firstly we go to the first child of the red node <em>(let's consider it to be the <b>green one</b>)</em> and then we move to the first child of the green node and which is the yellow one. Yippee we are done. You should notice that we did not even come back to the blue node <em><b>(the second child of our first source node)</b></em> because we didn't need to, however, if we were <b>searching for the blue or the pink node</b> we would be compelled to return back.
  <br>
  <br>
Here is the code for DFS.
</div>

```cpp
void DFSUtil(int u, vector<int> adj[], vector<bool> &visited)
{
    visited[u] = true;
    cout << u << " ";
    for (int i=0; i<adj[u].size(); i++)
    {
        if (visited[adj[u][i]] == false)
        {
            DFSUtil(adj[u][i], adj, visited);
        }
    }
}
 
// This function does DFSUtil() for all 
// unvisited vertices.
void DFS(vector<int> adj[], int N)
{
    vector<bool> visited(N, false);
    for (int u=0; u<N; u++)
    {
        if (visited[u] == false)
        {
            DFSUtil(u, adj, visited);
        }
    }
}
```
