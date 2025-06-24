

# Breadth First Search 

#22aug24


```
# Knight movement
rectangular m x n grid
chess knight starts at (sx,sy)
can it reach a target square (tx,ty)?
movement explored with all permutations of its move
	some move out and come back to same place
	some moves overlap over other moves

systematic exploration
	x1 - all the squares reachable in one move from (sx,sy)
	X2 - all squares reachable from X1 in one move
	...
	dont explore already marked square
	stopping when target square is reached
	if not reachable, when to stop? this can be solved by using queue
```
## An example of BFS
```
> Maintain a queue Q of cells to be explored
> Initially Q contains only start node (sx,sy)
	> Remove (ax,ay) from head of queue
	> mark all squares reachable in one step from (ax,ay) without going out
	> add all newly marked squares to the queue,
	> remove the first one, ignore already marked ones
	> similarly removing the next one, adding unexplored ones
	> at a point no new nodes are added, queue becomes empty
> When the queue is empty, we have finished
```

```python
# pseudocode

def explore( (sx,sy),(tx,ty) ):
	marked = [ [0 for i in range(n)]  for j in range(m)]   # n x m
	marked[sx][sy] = 1   # marking the start node
	queue = [(sx,sy)]   # insert starting node to the queue
	
	while queue != []:      # if queue is not empty, pop one from queue
		(ax,ay) = queue.pop()
		for (nx,ny) in in neighbours ( (ax,ay) ):  # find its nodes
			if !marked[nx][ny]:    # check if it is marked 
				marked[nx][ny] = 1  # if not marked, mark it
				queue.insert(0,(nx,ny))  # insert it into the queue
	return(marked[tx][ty])   # returns True or False
```

