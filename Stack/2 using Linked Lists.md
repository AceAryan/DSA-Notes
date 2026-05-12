## Stack using Linked Lists

```cpp
struct Node {
	int data;
	struct Node *next;
};
```

stack **empty** -> *top* == **NULL**
stack **full** -> when you are unable to create a new node ( i.e. **Heap** is full )
`Node *t = new Node; 
`if (t==NULL)`

#### Operations

**top** is a global pointer ( like Head in Linked List )
#### 1. Push ()
sabse upar ek ( stack mai only option wahi hai ) element insert karna hai

```cpp
void push (int x){
	Node *t = new Node;
	if (t==NULL)
		printf("Stack overflow");
	else
		t->data = x;
		t->next = top;
		top = t;
	}
}
```
==time comp== = O($1$) 
#### 2. Pop ()
upar wale element ki value return karke usko delete karna

```cpp
int pop (){
	Node *p;
	int x = -1;
	if (top == NULL)
		printf ("stack is empty");
	else {
		p = top;
		top = top->next;
		x = p->data;
		free(p);
	}
	return x; // agar kuch nahi hai delete karne ke liye to                    -1 return karega
}
```
==time comp== = O($1$) 
#### 3. Peek ()
hume ek specific position pe konsa element hai wo chahiye
index = top - pos + 1

```cpp
int peek (int pos){
	Node *p = top;
	for (int i=0; p!=NULL && i<pos-1; i++){
		p = p->next;
	}
	if (p! = NULL)
		return p->data;
	else 
		return -1;
}
```
==time comp== = O($1$) 
#### 4. stackTop ()
topmost element chahiye stack ka

```cpp
int stackTop (){
	if (top)
		return top->data;
	else
		return -1;
}
```
==time comp== = O($1$) 
#### 5. isEmpty ()
checks if stack is empty

```cpp
bool isEmpty (stack st){
	return top ? 0 : 1;	
}
```
==time comp== = O($1$) 
#### 6. isFull ()
check if stack is full

```cpp
bool isFull (stack st){
	Node *t = new Node;
	int r = t ? 1 : 0;
	free(t);
	return r; 
}
```
==time comp== = O($1$) 