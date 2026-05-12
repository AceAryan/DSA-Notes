- **PreOrder** : visit (Node) , PreOrder (Left SubTree), PreOrder (Right SubTree)
- **InOrder** :  InOrder (Left SubTree), visit (Node) , InOrder (Right SubTree)
- **PostOrder** : PostOrder (Left), PostOrder (Right), visit (Node)
- **LevelOrder** :  Level by Level

#### Creating Binary Tree

```cpp
void create (){
	Node *p, *t;
	int x;
	Queue q;
	printf("Enter Root Value");
	scanf("%d",&x);
	root = malloc();
	root->data = x;
	root->lchild = root->rchild = 0;
	enqueue(root);
	while(!isEmpty(q)){
		p = dequeue(&q);
		printf("Enter Left Child of %d", p->data);
		scanf("%d",&x);
		if(x!=-1){
			t = malloc();
			t->data = x;
			t->lchild = t->rchild = 0;
			p->lchild = t;
			enqueue(t);
		}
		printf("Enter Right Child of %d", p->data);
		scanf("%d",&x);
		if(x!=-1){
			t = malloc();
			t->data = x;
			t->lchild = t->rchild = 0;
			p->rchild = t;
			enqueue(t);
		}
	}
}
```

#### Recursive Tree Traversals

```cpp
void Preorder (struct Node *p){
	if(p){
		printf("%d", p->data);
		Preorder(p->lchild);
		Preorder(p->rchild);
	}
}
```
Total Calls = $2n+1$
size of system stackdepends on height of tree

```cpp
void Inorder (struct Node *p){
	if(p){
		Inorder(p->lchild);
		printf("%d", p->data);
		Inorder(p->rchild);
	}
}
```
Total Calls = $2n+1$
==Time Comp== : O($n$) *mostly for all operations upon binary tree*

#### Iterative Tree Traversals

```cpp
void Preorder (struct Node *t){
	struct stack st;
	while (t!=NULL || isEmpty(st)) {
		if (t!=NULL){
			printf("%d",t->data);
			push(&st,t);
			t=t->lchild;
		}
		else{
			t=pop(&st);
			t=t->rchild;
		}
	}
}
```

```cpp
void Inorder (Node *t){
	struct stack st;
	long int temp;
	while (t!=NULL || isEmpty(st)) {
		if (t!=NULL) {
			push(&st,t);
			t=t->lchild;	
		}
		else{
			temp = pop(&st);
			if (temp>0) {
				push(&st,-temp);
				t=((Node*)temp)->rchild;
			}
			else {
				printf ("%d", ((Node*)temp)->data);
				t = NULL;
			}
		}
	}
}
```

#### Level Order Traversal

```cpp
void Levelorder (struct Node *p){
	struct Queue q; // Queue ka datatype Node hona chahiye
	printf("%d", p->data);
	enqueue(&q, p);
	while (!isEmpty(q)) {
		p = dequeue(&q);
		if (p->lchild) {
			printf("%d",p->lchild->data);
			enqueue(&q, p->lchild);
		}
		if (p->rchild) {
			printf("%d",p->rchild->data);
			enqueue(&q, p->rchild);
		}
	}
}
```

#### Generating Tree from Traversals

alone preorder / postorder / inorder = $\binom{2n}{n}/n+1$ trees are possible

**individual tree** = pre + in / post + in
==time== : O($n^2$)

#### Height and Count of BT

```cpp
int Count (node *p) {
	int x,y;
	if (p!=NULL) {
		x = count(p->lchild);
		y = count(p->rchild);
		// can insert condition here to count different types of nodes
		return x+y+1; // working like PostOrder
	}
	return 0;
}
```

Usually *Postorder* is used for processing on BT

```cpp
int Height (node *p) {
	int x,y = 0;
	if (p==NULL) {
		return 0;
	}
	x = height(p->lchild);
	y = height(p->rchild);
	if (x>y) 
		return x+1;
	else
		return y+1;
}
```

Counting different types of nodes conditions :
 1. Leaf deg 0 `if(!p->lchild && !p->rchild)`
 2. Node deg 2 `if(p->lchild && p->rchild)`
 3. Node deg 1 or 2 `if(p->lchild || p->rchild)`
 4. Node deg 1 `if((p->lchild!=NULL && p->rchild==NULL) || (p->lchild==NULL && p->rchild!=NULL))`