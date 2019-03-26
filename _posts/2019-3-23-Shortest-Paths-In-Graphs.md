---
title: Shortest Paths In Graphs
---

<div style="text-align: justify">
Computing <em><b>shortest path in graphs</b></em> is an essential concept. When you encounter problems in some coding competition it will generally be a combination of <b>shortest paths and traversal</b>. There <b>three</b> algorithms that are <em><b>essential</b></em> to learn to compute shortest paths: <em><a href="#Dijkstra">Dijkstra's Algorithm</a>, Bellman Ford Algorithm and Floyd Warshall Algorithm</em>.
</div>

### Dijkstra's Algoritm

![Edsger W. Dijkstra](/images/Edsger_Wybe_Dijkstra.jpg "Edsger W. Dijkstra")

<div style="text-align: justify" id="Dijkstra">
This algorithm is named after a dutch computer scientist Edsger W. Dijkstra. This algorithm provides us with an efficient way to compute the shortest path in a graph with <b>NON NEGATIVE</b> edges. It is an interesting concept and is very useful to solve <em><b>real life problems</b></em>. Even some <b>map apps</b> that we use these days rely on it. Let's look at an example of a <b>road network</b>.
</div>

![Road Network](/images/Shortest.png "Road Network")

<div style="text-align: justify">
  The above graph shows an <b>intricate network</b> of roads in a city. Suppose we have to the find the shortest path from the <b>green node</b> to the <b>blue one</b>. Now, naturally a naive approach would be to move first towards the <em><b>yellow node since the path length is smaller</b></em> than that from <b>green to orange</b>. However, once we study the network it seems that we have to do just the opposite. Here is where <b>Dijkstra's algorithm</b> comes in. 
<br>
<br>
  The best way to imagine <b>Dijkstra's algorithm</b> running is by <b>imagining</b> that we fire up the source node and now the <em><b>fire travels along all the edges at a uniform speed</b></em>. So now let's <b>fire up</b> the green node. Our fire first reaches the <b>yellow node</b>. <b>As soon as</b> our fire reaches the yellow node our graph will look like this.
</div>

![Road Network](/images/Dijkstra_1.png "Road Network")

<div style="text-align: justify">
  The fire won't stop but keep moving further, and the next <em>useful destination</em> that it reaches is the <b>orange node</b>. It will also reach the <b>green node</b> once again <b>along the edge from yellow to green</b>. At this stage our graph will look something like this where it is halfway (5 untits) away from the <b>red node</b> along the path from yellow to red. 
</div>

![Road Network](/images/Dijkstra_2.png "Road Network")

<div style="text-align: justify">
  The fire now reaches the <b>red node</b> from the orange one and we now see that it is still one unti away from red node <b>along the path from yellow to red</b>. It starts moving along many edges now but we can focus on the ones that our <em>useful</em> to us. Now the graph looks lthe this.
</div>

![Road Network](/images/Dijkstra_3.png "Road Network")

<div style="text-align: justify">
  The fire will <em>eventually</em> reach our target node, which is the <b>blue one</b>. The graph is shown below. Notice, that in this particular example the fire has covered all the edges but it is <b>NOT necessary</b>.
</div>

![Road Network](/images/Dijkstra_4.png "Road Network")

<div style="text-align: justify">
  This was the <b>virtual analysis</b> of the <em><b>Dijskta's Algorithm</b></em>. Now all we need to do is to implement this in code.
</div>

### Developing The Code for Dijkstra 

<div style="text-align: justify">
I would suggest you to look at the code below before moving forward so that you can get an <b>essense of what follows</b>.
</div>

```cpp
//Improved and efficient Djikstra
void ImprovedDjikstravector(vector <pair<int,int > > adj[], int src, int V)
{
	//stores all unvisited vertices along with their shortest possible
	//path at the moment
	set<pair<int, int> > visdist ;

	// Create a vector for distances and initialize all 
    // distances as infinite (INF) 
    vector<int> dist(V, INT_MAX); 

    //adds the source node
    visdist.insert(make_pair(0, src));

    dist[0] = 0;
    while(!visdist.empty())
    {
    	// The first vertex in Set is the minimum distance 
        // vertex, extract it from set. 
        pair<int, int> tmp = *(visdist.begin()); 
        visdist.erase(visdist.begin()); 

        //stores the current parent vertex
        int u = tmp.second;
        for (auto i = adj[u].begin(); i != adj[u].end(); ++i) 
        { 
            // Get vertex label and weight of current adjacent 
            // of u. 
            int v = (*i).first; 
            int weight = (*i).second; 
  
            //  If there is shorter path to v through u. 
            if (dist[v] > dist[u] + weight) 
            { 
                /*  If distance of v is not INF then it must be in 
                    our set, so removing it and inserting again 
                    with updated less distance.   
                    Note : We extract only those vertices from Set 
                    for which distance is finalized. So for them,  
                    we would never reach here.  */
                if (dist[v] != INT_MAX) 
                    visdist.erase(visdist.find(make_pair(dist[v], v))); 
  
                // Updating distance of v 
                dist[v] = dist[u] + weight; 
                visdist.insert(make_pair(dist[v], v)); 
            } 
        } 
    } 
     // Print shortest distances stored in dist[] 
    printf("Vertex   Distance from Source\n"); 
    for (int i = 0; i < V; ++i) 
        printf("%d \t\t %d\n", i, dist[i]); 
}
```

<div style="text-align: justify">
Very few people use the above implementation of Dijkstra's Algorithm. However, this is <b>very efficient</b> and using this is in competitions will be a great advantage. Before moving forward there is one <b>important principle</b> of this algorithm that we should know. Whenever we move from a node for which <b>we have found the smallest value to the node which is directly connected to it through an edge and is at the shortest distance from it , the distance then computed can be believed to be the shortest distnace from the source node.</b> So now let's discuss what I did up there.
<br>
<br>
I have used a <b>set of pairs of integers</b> named <em><b>visdist</b></em>. The pair stores all the unvisited nodes with their distances. Then intialised an <b>integer vector</b> named dist to store the distances to <b>maximum possible value of an integer <em>(think why?)</em></b>. Then whatver I do from that point on is what we already discussed. I insert the minimum possible value to reach the source vertex from itslef as <b>0</b>.This would help us move forward using the <b>basic priciple</b> of this algorithm. Then all there is left to do is to iterate over <b>all of the children</b> of the current univisited node with the shortest distance <b>(The first such node will always be the source itslef)</b> and update their distance. We need to do this every node is visited. The reason we use a set here is simple: <b>it stores the values in ascending order for us</b>; so we dont have to find it using another function. The set also stores only those pairs which are currently visited by the last node <b><em>(or the ones before that if they are not explored)</em> but are yet to be explored</b>. At end we get the <b>shortest distance from the source node to all the vertices</b>.
<br>
<br>
	This wraps up our discussion of <em><b>Dijkstra's Algorithm</b></em>. Now we can move on to discuss about the other algorithms and deal with <b>negative edges</b>.
</div>

