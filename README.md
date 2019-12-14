# A_star
A star algorithm for quad-directional movements
Although the code is self explanatory, this file tries to make it more clear 
The program has been implemented by using below methods:
Reconstruct method 
```
def reconstruct(child_node,came_from_list):
  child_node=child_node
  path=[]
  came_from_list=came_from_list
  for n in range(len(came_from_list)) :
    if child_node==came_from_list[n][0]:
      path.append(came_from_list[n][0])
      path.append(came_from_list[n][1])
      child_node=came_from_list[n][1]
```
This method can be used to make use of grid map utility but I have restrained to use multilevel lists
```
grid=Grid(matrix=map)

```
If it doesn't work on your system, make sure to install following utilities and library files
```
pip install pathfinding
pip install lib
```
The below method tries to calculate the safe nodes from graph where the obstacle is not present
```
def obstacle(map):
    obstacle_nodes=[]
    safe_nodes=[]
    print("i was here")
    for i in range(len(map)):
        for j in range(len(map[i])):
            temp1=i
            temp2=j
            if map[temp1][temp2]==0:
                obstacle_nodes.append([temp1,temp2])
            else:
                safe_nodes.append([temp1,temp2])
```
method calculates safe neighbor nodes to form a frontier from which the function cost of each neighbor node is calculated and minimum cost neighbor node is chosen.
Going forward if any node is encountered with lesser functional cost, ie. f = g + h where g is the total cost of parent node and h is the heuristic of neighbor nodes or child nodes. Here heuristic is  Euclidian distance which tries to focus the frontier node formation in the direction of node until an obstacle is reached.
```
def safe_neighbor_nodes(safe_nodes,node):
    safe_nodes=safe_nodes
    node=node
    direction=[[1,0],[0,1],[-1,0],[0,-1]]
    result=[]
    for dir in direction:
        print("d is",dir)
        neighbor=[node[0]+dir[0],node[1]+dir[1]]
        if neighbor in safe_nodes:
            result.append(neighbor)
    print(result) 
    return result
```
Heuristic calculation for all safe nodes with respect to goal_node
```
def heuristics(node1,goal_node):
    node1=node1
    node2=goal_node
    # Let heuristic distance weight be dependent on the euler's distance
    squared_displacement_value=(node1[0]-node2[0])**2 +(node1[1]-node2[1])**2
    print("squared_displacement_value",squared_displacement_value)
    heuristic_ = math.sqrt(squared_displacement_value)
    return heuristic_
```
In future work I would like to change the map list style to [[x,y],0] or [[x,y],1] where 1 represent safe nodes.
