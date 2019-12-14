# A_star
A star algorithm for quad-directional movements
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
