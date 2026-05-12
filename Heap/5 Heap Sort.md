1. Create Heap of ==n== elements
2. Delete ==n== elements 1 by 1
3. Remaining array is the Heap Sort

$n\log{n} + n\log{n} => O(n\log{n})$

```cpp
int Delete (int A[], int n) {
	int x,i,j,val;
	val = A[1];
	x = A[n];
	A[1] = A[n];
	A[n] = val; // storing element at last place
	i = 1; j = 2*i;
	
	while (j < n-1) {
		if (A[j+1] > A[j]) 
			j=j+1;
		if (A[i] < A[j]) {
			swap (A[i], A[j]);
			i = j;
			j = 2*j;
		}
		else
			break;
	}
	return val;
}

int main () {
	int H[n]; // H is the Heap, assume created
	for (i=n; i>1; i--) {
		Delete (H,i);
	}
	print(H);
}

// remaining array is the heap sort
```