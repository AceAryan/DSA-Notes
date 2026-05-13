start from 1 element, insert 2nd element and go on like this

no. of passes = n-1
no. of comparisons = O($n^2$)
no. of swaps = O($n^2$)

intermediate result will not give any useful result
Insertion should be done in LL not Array

adaptive, stable

```cpp
void InsertionSort(int A[], int n){
	for(i=1; i<n; i++){
		j = i-1;
		x = A[i];
		
		while(j>-1 && A[j]>x){
			A[j+1] = A[j];
			j--;
		}
		A[j+1] = x;
	}
}
```

![[Pasted image 20260513195125.png]]