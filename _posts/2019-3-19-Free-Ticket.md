---
layout: post
title: Free Ticket
---

[Question Link](https://www.codechef.com/INOIPRAC/problems/INOI1402)

### Overview

This question came in INOI in the year 2014 and was regarded by many as a pretty basic question. In fact, it was a trivial question if one had the basic knowledge of graphs. This question, however, is a nice example for beginner and introduces them to one of the most important graph concept: *Djikstra's Algorithm.*

### Understanding The Question

The first thing we need to observe is that it is a graph question. We are told that Nikhil has won some competetion and is entitled to a free ticket. There is one twist, however; for any two cities that nikhil choose, he would have to travel between them by the cheapest route. Now Nikhil, wants to **maximise** his prize. Here, the format of the question and the input strongly suggests that this is a graph problem. Here, the tak at our hand is to find the **most expensive** flight sequence connecting two pair of cities while remaining cheapest for that pair. This all seems confusing but you will see soon how **simple** this is.

### Approaching the Solution

_**I higly reccomend you to try finding your own approach before reading mine**_

By now we know what is to be done(more or less). We can start by developing a simple **bi-directional** graph using an **adjacency list**(I personally prefer this over the matrix because of all the simplicity). After this step we can store all the connected cities in our graph. Now comes the thinking part. We are supposed to find *"the **most expensive** flight sequence connecting two pair of cities while remaining cheapest for that pair"* which seems confusing but let's go step by step. We can firstly find the cheapest route between **all** of the pairs of cities in a city. For this we can use *Djikstra's Algorithm*(we can use Belman Ford or Flloyd Warshall too!!!.... but our time constraints do not restrict the use of brute force). Once we accomplish this task we are through with the problem. But **WAIT** we are supposed to find the most expensive fligth sequence. What can we do now?? Think. Try to think the answer now before going forward. I assume you have done that. We now just need to find that most expensixe flight sequence from our already computed cheapest routes between all pairs which can be accomplishes by a basic *linear search*(or use binary search if you are a perfectionist).

Hurray!! We are done. Easy was'nt it. All we needed was a basic knowledge of graph and a clear thought pattern.
