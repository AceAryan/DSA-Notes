1. Limited Set of Priorities (used in OS)
2. Element Priority

### 1. Limited Set of Priorities

- More than 1 Queue ( each queue is for a unique priority level )
- Enqueue into the Queue acc. to the Element's priority level
- Deqeueue always from the Topmost (highest priority) queue

### 2. Element Priority

- har element ki priority alag
- let's assume : smallest no. -> highest priority

1. Insert in Same order, Delete Max Priority by Searching it
	==Insert== - O($1$), ==Delete== - O($n$)
2. Insert in Increasing order of Priority, Delete Last element of Array
	==Insert== - O($n$), ==Delete== - O($1$)