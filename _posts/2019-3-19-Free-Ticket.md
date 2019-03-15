---
layout: post
title: Free Ticket
---

[Question Link](https://www.codechef.com/INOIPRAC/problems/INOI1402)

### Overview

This question came in INOI in the year 2014 and was regarded by many as a pretty basic question. In fact, it was a trivial question if one had the basic knowledge of graphs. This question, however, is a nice example for beginner and introduces them to one of the most important graph concept: Djikstra's Algorithm.

### Understanding The Question

The first thing we need to observe is that it is a graph question. We are told that Nikhil has won some competetion and is entitled to a free ticket. There is one twist, however; for any two cities that nikhil choose, he would have to travel between them by the cheapest route. Now Nikhil, wants to **maximise** his prize. Here, the format of the question and the input strongly suggests that this is a graph problem. Here, the tak at our hand is to find the **most expensive** flight sequence connecting two pair of cities while remaining cheapest for that pair. This all seems confusing but you will see soon how **simple** this is.

### Approaching the Solution

