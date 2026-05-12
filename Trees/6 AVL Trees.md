balance factor = height of left subtree - height of right subtree
bf = $h_l - h_r$ = ${-1,0,1}$

if bf = $|{h_l - h_r}| <= 1$ : **node balanced**
if bf > 1 then  : **node imbalanced**

1 Node Imbalanced => Tree Imbalanced

### Rotations for Insertion

1. LL Rotation 
![[Pasted image 20260303202509.png|508]]
2. RR Rotation
![[Pasted image 20260303202450.png|506]]
3. LR Rotation
 ![[Pasted image 20260303202527.png|503]]
4. RL Rotation
![[Pasted image 20260303202540.png|509]]

LL RR - single rotations
LR RL - double rotations (not = 2 rotations)

assume like a thread moves

LL mai pl ka rchild p ka lchild banjayega
LR mai plr ka lchild pl ka rchild banega aur plr ka rchild p ka lchild banege


```cpp
int NodeHeight (struct Node* p) {
	int hl,hr;
	hl=p && p->lchild?p->lchild->height:0;
	hr=p && p->rchild?p->rchild->height:0;
	
	return hl>hr?hl+1:hr+1;
}
```

```cpp
int BalanceFactor (struct Node* p) {
	int hl,hr;
	hl=p && p->lchild?p->lchild->height:0;
	hr=p && p->rchild?p->rchild->height:0;
	
	return hl-hr;
}
```

```cpp
struct Node* LLrotation (struct Node* p) {
	struct Node* pl = p->lchild;
	struct Node* plr = pl->rchild;
	
	pl->rchild = p;
	p->lchild = plr;
	p->height = NodeHeight(p);
	pl->height = NodeHeight(pl);
	
	if (root==p) {
		root = pl;
	}
	return pl;
}
```

```cpp
struct Node* LRrotation (struct Node* p) {
	struct Node* pl = p->lchild;
	struct Node* plr = pl->rchild;
	
	pl->rchild = plr->lchild;
	p->lchild = plr->rchild;
	
	plr->lchild = pl;
	plr->rchild = p;
	
	pl->height = NodeHeight(pl);
	p->height = NodeHeight(p);
	plr->height = NodeHeight(plr);
	
	if(root==p) 
		root = plr;
	
	return plr;
}
```

### Creating AVL Tree

Balance on every insertion
Start with the 1st Ancestor that became Imbalanced

### Delete

 1. L 1 Rotation
 2. L -1 Rotation
 3. L 0 Rotation
 4. R 1 Rotation
 5. R -1 Rotation
 6. R 0 Rotation

### Height vs Nodes

if height h given :
min. nodes n => $N(h) = 0 / 1/ N(h-2)+N(h-1) otherwise$
max nodes n = $2^{h+1}-1$

if n nodes given :
min. height h = $log_2 {(n+1)}$
max. height h = do from min. nodes n

