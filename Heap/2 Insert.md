using example for inserting in MaxHeap

 insert element at next available position x, check if > parent ( $\lfloor x/2 \rfloor$), swap and iterate till parent >= ele

```cpp
void Insert (int A[], int n) {
	int temp, i = n;
	temp = A[n];
	
	# 1-based indexing
	while (i>1 && temp>A[i/2]) {
		A[i] = A[i/2];
		i=i/2;
	}
	A[i] = temp;
}
```
O($log{n}$)