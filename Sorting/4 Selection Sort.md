select position -> find element for that position (min using 2ptr)

no. of comparisons = O($n^2$)
no. of swaps = O(n) 

algo with min. no. of swaps

not adaptive, not stable

```cpp
void SelectionSort(int A[], int n){
	int i,j,k;
	
	for(i=0; i<n-1; i++){
		for(j=k=i; j<n; j++){
			if(A[j]<A[k]) k=j;
			swap(A[i],A[k])
		}
	}
}
```