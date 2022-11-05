## Leading Question 


Question: What is the most important airport in the world?

## Dataset Acquisition

We will acquire the data from https://openflights.org/data.html, specifically routes.dat.

## Data Format

We are using route data, which is a comma delimited dat file. This data contains 67663 routes. We will be using the source airport, the source airport ID, and the number of stops. We will also gather a list of all airports in this data.

## Data Correction

The data contains some null and invalid values for data that had not been collected at that point. Some of this data can be otherwise obtained, such as source airport ID. This can be done through https://openflights.org/html/apsearch. We will collect each airport which does not show an ID in the data, and put it through the search to find the correct ID, then include it in the data. Only 920 instances of null data exists in this set, very little of it is in the subset we have selected, so this will be handled by hand.

## Data Storage

We are going to store each row (one route) as an edge in our graph. Each node will represent an airport. Therefore, the graph will be a directed weighted graph, though it is hardly weighted. The weights in this instance is the number of stops, which is zero for almost every route. Because we are storing each route, each airport, and data about each, and are not storing anything in particular about every airport's relationship with every other, or every route's relationship with every other, or anything like that, this will take linear storage of O(n + m) with n being routes and m being airports.

## Algorithm 

To answer our main question, we will use the page rank algorithm. Then, we will do two more things using the data, first we will do a breadth first search to find the number of flights you would need to take from the most important airport to any other airport. Then, we will use the data to make a layered graph drawing of each other airport in relation to the one we found "most important".

As stated previously, we will be using a directed graph with airport nodes and route edges. The functions would take this input in. Our page rank algorithm will find the importance of each airport (Pr(a)), and we will also go through each of these to find the largest. The breadth first search will result in a tree made up of the nodes in the order they were traversed to. Our final graphical representation will visualize that tree. We estimate that making the graph will be O(n * m) for n routes, and m airports. Page rank algorithm is typically shown as O(n + m). Breadth first search is O(m)

## Timeline

Alternate:

11/6-11/10: Complete graph structure and data parsing

11/11-11/19: Complete Page Rank Algorithm

Work over Fall break is optional

11/27-12/1 Complete breadth-first search

12/1-12/8 Complete visualization.