aka Bucket Sort
similar to Count Sort, Array of LL 

time = O(n) 
space =  O(n)

```cpp
void binSort(int A[], int n){
	int max, i,j;
	Node** bins;
	max = findMax(A,n);
	bins = new Node*[max+1];
	
	for(i=0; i<max+1; i++){
		bins[i]=NULL;
	}
	for(i=0; i<n; i++){
		Insert(bins[A[i]],A[i]);
	}
	i=0; j=0;
	while(i<max+1){
		while(bins[i]!=NULL){
			A[j++]=Delete(bins[i]);
		}
		i++;
	}	
}
```
