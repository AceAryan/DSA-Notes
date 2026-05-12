based on **LIFO : Last In First Out**
**Stack** = collection of elements following this discipline

- stack ke andar kuch daalke nikaaloge to wo reverse hojayega
- recursion uses stack (automatic), usko iterative mai convert karne (programmer) stack ko use karna pad sakta hai

### ADT :

-  **Data**:
	1. Space for storing elements
	2. top pointer

- **Operations**:
	1. push (x)
	2. pop ()
	3. peek (index)
	4. stackTop ()
	5. isEmpty ()
	6. isFull ()

## Stack using Array

```cpp
struct stack {
	int size;
	int top; // top pointer
	int *s; // dynamic allocation for array
};
```

stack **empty** -> *top* = -1
stack **full** -> *top* = size - 1

#### Operations

#### 1. Push ()
sabse upar ek ( stack mai only option wahi hai ) element insert karna hai

```cpp
void push ( stack *st, int ele ){
	if (st->top == st->size-1)
		printf ("stack overflow");
	else {
		st->top++;
		st->s[st->top] = x;
	}
}
```
==time comp== = O($1$) 
#### 2. Pop ()
upar wale element ki value return karke usko delete karna

```cpp
int pop ( stack *st ){
	if (st->top == -1 )
		printf ("stack underflow");
	else {
		x = st->s[st->top];
		st->top--;
	}
	return x; // agar kuch nahi hai delete karne ke liye to                    -1 return karega
}
```
==time comp== = O($1$) 
#### 3. Peek ()
hume ek specific position pe konsa element hai wo chahiye
index = top - pos + 1

```cpp
int peek (stack st, int pos){
	int x = -1;
	if (st.top-pos+1 < 0)
		printf("Invalid Position");
	else
		x = st.s[st.top - pos + 1];
	return x;
}
```
==time comp== = O($1$) 
#### 4. stackTop ()
topmost element chahiye stack ka

```cpp
int stackTop (stack st){
	if (st.top == -1)
		return -1;
	else
		return st.s[st.top];
}
```
==time comp== = O($1$) 
#### 5. isEmpty ()
checks if stack is empty

```cpp
bool isEmpty (stack st){
	if (st.top == -1)
		return 1;
	else
		return 0;	
}
```
==time comp== = O($1$) 
#### 6. isFull ()
check if stack is full

```cpp
bool isFull (stack st){
	if (st.top == st.size-1)
		return 1;
	else
		return 0;	
}
```
==time comp== = O($1$) 



