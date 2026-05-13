heaviest element drowns to bottom

no. of passes = 4 - (n-1)
no. of comparisons = O($n^2$)
no. of swaps = O($n^2$)

adaptive, stable

```cpp
void BubbleSort(int A[], int n){
	int flag;
	for(int i=0; i<n-1; i++){
		flag = 0;
		for(int j=0; j<n-1-i){
			if(A[j]>A[j+1]){
				swap(A[j], A[j+1]);
				flag = 1;
			}
			if(flag==0) break; // array already sorted
		}
	}
}
```

