BFS is the short of Breadth-first Search. It use a graph search, in order to find the best path between two points.

Each node should have a reference to the previous node ( Like a list ). This reference is used only by the algorithm in order to retrieve path from the last node (Potentially the destination). The algorithm has `frontierNodes` and `exploderNodes`.  

The function should take as parameters: 
the grid, the **_starting node_** and the **_ending node_**. Note: you can always substitute this nodes with (x, y) that represents its position in grid. 
In our pseudocode he call it `start` and `end`.

Each node have a value inside, it represents the distance between starting node and itself. Everytime we see a node we should ask if our distance + 1 is minus the distance of the cell.  

At start, each node has `distance` equals to infinity and `start` distance is 0.

```cpp
#pseudocode

Node
{
	d = MAX_INT,   // Distance from start node
	x, y // Coordinates
}

// Start and end are used only for coordinates
Pathfinding(Node** grid,  Node start, Node end)
{
	vector<Node> frontierNodes;
	vector<Node> exploredNodes; 

	// Init distances
	initDistances(start); // Each cell grid cell has infinity, start cell has 0.
	
	// Add start node to the frontierNodes
	frontierNodes.add(grid[start.x][start.y]);
	
	while(Node node : frontierNodes)
	{
		// For each node check neghbors
		// Validate node x and y.
		// for each cells are up, left, right, down. 
			// Check directionalCell.d > node.d + 1
				// Assign previousNode = node
				// assign d = node.d + 1 if node.d + 1
		// Add this node to the exploredNodes
	}
}
```