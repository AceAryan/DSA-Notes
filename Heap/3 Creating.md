Inplace Heap Creation
using [[2 Insert]]

```cpp
void createHeap (int A[], int n) {
	int i;
	for (i=2; i<=n; i++) {
		Insert(A,i);
	}
}
```
O($n\log{n}$)