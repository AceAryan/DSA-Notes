**rear** helps to enqueue in constant time

**empty** : if ( front == NULL )
**full** : `Node *t = new Node; if (t == NULL);`

#### Operations

#### 1. Enqueue ()
```cpp
void enqueue (Queue *q, int x){
	Node *t = new Node;
	if (t==NULL)
		printf("Queue is Full");
	else{
		t->data = x;
		t->next = NULL;
		if(front==NULL) front = rear = t;
		else{
			rear->next = t;
			rear = t;
		}
	}
}
```
==time comp== = O($1$) 
#### 2. Dequeue ()
```cpp
void dequeue (Queue *q){
	int x = -1;
	Node *p;
	if (front==NULL)
		printf("Queue is Empty");
	else{
		p = front;
		front = front->next;
		x = p->data;
		free(p);
	}
	return x; 
}
```
==time comp== = O($1$) 