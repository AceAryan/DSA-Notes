Queue is a *Logical Data structure*
based on **FIFO**

-  **Data**:
	1. Space for storing elements
	2. Front - for Deletion
	3. Rear - for Insertion

- **Operations**:
	1. enqueue (x)
	2. dequeue ()
	3. isEmpty ()
	4. isFull ()
	5. first ()
	6. last ()


## Queue using Array

1. Queue using Single Pointer
2. Queue using Front and Rear
3. Drawbacks of Queue using Array

#### 1. using Single Pointer
Insert - O($1$)
Delete - O($n$)
#### 2. using Two Pointers
enqueue - O($1$)
dequeue - O($1$)

front and rear are **index pointers** not **address pointers**

**initially** : front = rear = -1
**empty** : if (front == rear) *assuming front points one block behind first element*
**full** : rear == size -1


```cpp
struct Queue {
	int size;
	int front;
	int rear;
	int *Q;
};
```

```cpp
int main(){
	struct Queue q;
	printf ("Enter size");
	scanf ("%d",&q.size);
	q.Q = (int*)malloc(q.size*sizeof(int));
	q.front = q.rear = -1;
}
```

#### Operations

#### 1. Enqueue ()
```cpp
void enqueue (Queue *q, int x){
	if (q->rear == q->size-1)
		printf ("Queue is Full");
	else {
		q->rear++;
		q->Q[q->rear] = x;
	}
}
```

#### 2. Dequeue ()
```cpp
void dequeue (Queue *q){
	int x = -1;
	if (q->front == q->rear){
		printf ("Queue is empty");
	}
	else {
		q->front++;
		x = q->Q[q->front];
	}
	return x;
}
```

##### Drawbacks of Queue using Arrays
queue becomes empty then useless

**Solutions**: 
1. *Resetting Pointers* : Whenever queue becomes empty, reset front and rear to -1
2. *Circular Queue* : Uses the entire array, keep the block to which front is pointing to empty.
   `ptr = (ptr+1) % size` for Circular.

#### Operations on Circular Queue

```cpp
void enqueue (struct Queue *q, int x){
	if ((q->rear+1)%q->size==q->front)
		printf("Queue is full");
	else{
		q->rear = (q->rear+1)%q->size;
		q->Q[q->rear]=x;
	}
}
```

```cpp
void dequeue (struct Queue *q){
	int x = -1;
	if (q->front == q->rear)
		printf("Queue is Empty");
	else{
		q->front = (q->front + 1)%q->size;
		x = q->Q[q->front];
	}
	return x;
}
```
