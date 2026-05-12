- **Trees** : Collection of Nodes and Edges
- 1 Node is taken as *Root* and rest are in Disjoint Subsets (*Subtrees*)
- **Parent / Child** : only for Nodes having only 1 edge in between
- **Siblings** : Children of same Parent
- **Descendants / Ancestors** : All nodes upto root / leaf , who is parent / child of the selected node
- **Degree of Node** : No. of Children of a Node
- **Degree of Tree** : Every Node can have maximum that degree.
- **Internal / External Nodes** : (aka *Non Leaf / Leaf*) Leaf / Terminal : Degree = 0
- **Levels** : Root = Level 1, It's children = Level 2 and so on...
- **Height** : (*no. of edges from root*) Root = Height 0, It's children = Height 1 and so on...
- **Forest** : Collection of Trees

## Binary Tree
- degree of tree = 2
- left child / right child
- children = {0,1,2}

##### No. of Binary Trees using n Nodes

1. Unlabelled Nodes
	 $T(n)$ = $\binom{2n}{n}/(n+1)$ *catalan number* / $\sum^{n}_{i=1}T(i-1)*T(n-i)$
	 no. of trees with max. height = $2^{n-1}$
2. Labelled Nodes
	 $T(n)$ = $\binom{2n}{n}/(n+1) * n!$

##### Height vs Nodes
**Height given**
min no. of nodes : n = h+1
max no. of nodes : n = $2^{h+1}-1$

**Nodes given**
min height : h = $\log_{2}{(n+1)}-1$
max height : h = n-1

##### Leaf vs Non Leaf Nodes
deg(0) = deg(2) + 1

#### Strict Binary Tree
children = {0,2}

min no. of nodes : n = 2h+1
max no. of nodes : n = $2^{h+1}-1$

min height : h = $\log_{2}{(n+1)}-1$
max height : h = (n-1)/2

e = i +1 (*e* = external nodes, *i* = internal nodes)


