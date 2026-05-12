#### Representation using Arrays
*assuming index starts from 1*

element : i
left child : 2i
eight child : 2i+1
parent : $\lfloor{i/2}\rfloor$

#### Representation using Linked 

```cpp
struct Node {
	struct Node *lchild;
	int data;
	struct Node *rchild;
};
```
Null Ptrs : n+1

##### Full vs Complete BTs

**Full Binary Tree** : A Tree having maximum no. of nodes possible for that height

**Complete Binary Tree** : A complete BT of height h will be a full BT upto height h-1 and at last level elements will be filled left to right without skipping.
*array rep mai beech mai koi gap nahi aana chahiye, side mai chalega*

- complete matlab suitable for array
- Full BT is always complete but not vice versa

##### Strict vs Complete BTs
complete BT more useful


