# Project-Route-Planner--ADARSH


The Algorithm
The algorithm written will be responsible for generating a path like the one passed into show_map above. 
In fact, when called with the same map, start and goal, as above you algorithm will produce the path [5, 16, 37, 12, 34]. 
Following Functions are necessary to produce the accurate path.

``create_closedSet`` -Creates and returns a data structure suitable to hold the set of nodes already evaluated
``create_openSet`` -

``create_openSet``- Creates and returns a data structure suitable to hold the set of currently discovered nodes
    that are not evaluated yet. Initially, only the start node is known."""
``create_cameFrom`` -Creates and returns a data structure that shows which node can most efficiently be reached from another,
    for each node.
``create_gScore`` -Creates and returns a data structure that holds the cost of getting from the start node to that node, 
    for each node. The cost of going from start to start is zero.
``create_fScore`` -Creates and returns a data structure that holds the total cost of getting from the start node to the goal
    by passing by that node, for each node. That value is partly known, partly heuristic.
    For the first node, that value is completely heuristic.

**Set certain variables**
The below functions help set certain variables if they weren't a part of initializating our PathPlanner class, or if they need to be changed for anothe reason.

``set_map(self, M)`` -Method used to set map attribute 
``set_start(self, start)``-Method used to set start attribute 
``set_goal(self, goal)`` -Method used to set goal attribute 
Get node information
The below functions concern grabbing certain node information. In is_open_empty, you are checking whether there are still nodes on the frontier to explore. In get_current_node(), you'll want to come up with a way to find the lowest fScore of the nodes on the frontier. In get_neighbors, you'll need to gather information from the map to find the neighbors of the current node.

``is_open_empty(self)``-returns True if the open set is empty. False otherwise. """

``get_current_node(self)``-Returns the node in the open set with the lowest value of f(node)."""

`` get_neighbors(self, node)`` -Returns the neighbors of a node

``get_gScore(self, node)`` -Returns the g Score of a node

``distance(self, node_1, node_2)`` -Computes the Euclidean L2 Distance


    x=self.map.intersections[node_2][0]-self.map.intersections[node_1][0]
    y=self.map.intersections[node_2][1]-self.map.intersections[node_1][1]
    dist=math.sqrt(x**2+y**2)
    return dist

`` get_tentative_gScore(self, current, neighbor)``-returns the tentative g Score of a node


    return ( self.get_gScore(current) + self.distance(current,neighbor) )

    
``heuristic_cost_estimate(self, node)``-Returns the heuristic cost estimate of a node 


    return self.distance(node, self.goal)


``calculate_fscore(self, node)`` -Calculate the f score of a node.


    f=self.get_gScore(node) + self.heuristic_cost_estimate(node)
    return f

    
Recording the best path
Now that you've implemented the various functions on scoring, you can record the best path to a given neighbor node from the current node!


`` record_best_path_to(self, current, neighbor)``-Record the best path to a node


    self.cameFrom[neighbor] = current
    self.gScore[neighbor]=self.get_tentative_gScore(current,neighbor)
    self.fScore[current]=self.calculate_fscore(current)
