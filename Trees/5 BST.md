- A Binary Tree for which all elements in left subtree less than that node, every element in right subtree greater than that node
- No duplicates
- Inorder gives sorted order
- No. of BST for ==n== nodes = $\binom{2n}{n}/n+1$

### Searching
O($log{n}$)
#### Recursive Search

```cpp
Node* Rsearch(Node *t, int key) {
	if (t==NULL){
		return NULL;
	}
	if (key==t->data){
		return t;
	}
	else if (key<t->data){
		return Rsearch(t->lchild,key);
	}
	else
		return Rsearch(t->rchild,key);
}
```
#### Iterative Search

```cpp
Node* Rsearch(Node *t, int key){
	while(t!=NULL){
		if (key==t->data)
			return t;
		else if (key<t->data)
			t=t->lchild;
		else
			t=t->rchild;
	}
	return NULL;
}
```

### Insert 
first search -> if not found -> insert
O(n)
#### Iterative Insert
```cpp
void Insert (Node *t, int key) {
	Node *r = NULL; *p;
	while (t!=NULL) {
		r=t;
		if (key==t->data)
			return
		else if (key < t->data) 
			t=t->lchild;
		else
			t=t->rchild;
	}
	p = new Node;
	p->data = key;
	p->lchild = p->rchild = NULL;
	(p->data < r->data) ? r->lchild=p : r->rchild=p;
}
```

#### Recursive Insert
```cpp
Node* Insert (Node* p, int key) {
	Node *t;
	if (p==NULL) {
		t = new Node;
		t->data = key;
		t->lchild = t->rchild = NULL;
	}
	if (key<p->data) 
		p->lchild = Insert(p->lchild, key);
	else if (key>p->data)
		p->rchild = Insert(p->rchild, key);
	return p;
}
```

### Delete
replace Node with either the Inorder predecessor or the Inorder successor, might still need to make multiple modifications

Time - O($\log{n}$) - also the no. of modfications

### Creating BST 
O($n*\log{n}$)
Insert - n
Search - log n

#### Generating BST from Preorder
In BST we already know Inorder (sorted order of elements)
 
```cpp
void createPre (int pre[], int n) {
	stack st;
	Node *t;
	int i = 0;
	root = new Node;
	root->data = pre[i+1];
	root->lchild = root->rchild = NULL;
	p = root;
	while (i<n) {
		if (pre[i] < p->data) {
			t = newNode;
			t->data = pre[i++];
			t->lchild = t->rchild = NULL;
			p->lchild = t;
			push (&st, p);
			p = t;			
		}
		else {
			if (pre[i] > p->data && pre[i] < stackTop(st)->data) {
				t = new Node;
				t->data = pre[i++];
				t->lchild = t->rchild = NULL;
				p->rchild = t; p = t;
			}
			else {
				p = pop(&st);
			}
		}
	}
}
```
==time comp== = O(n)

### Drawbacks of BST

- can't control height of BST : can go from ==logn== to ==n== depending on the order of insertions