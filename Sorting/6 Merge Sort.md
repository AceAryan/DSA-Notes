merge time = O($m+n$)

Merge 2 Arrays:
```cpp
void Merge(int A[], int B[], int m, int n){
	int i,j,k;
	i=j=k=0;
	
	while(i<m && j<n){
		if(A[i]<B[j])
			c[k++]=A[i++];
		else 
			c[k++]=B[j++];
	}
	for(; i<m; i++){
		c[k++]=A[i];
	}
	for(; j<n; j++){
		c[k++]=B[j];
	}
}
```

Merge from Same Array:
```cpp
void Merge(int A[], int l, int mid, int h){
	int B[h+1];
	int i=l, j=mid+1, k=l;
	
	while(i<=mid && j<=h){
		if(A[i]<A[j])
			B[k++]=A[i++];
		else 
			B[k++]=A[j++];
	}
	for(; i<=mid; i++){
		B[k++]=A[i];
	}
	for(; j<=h; j++){
		B[k++]=A[j];
	}
	for(i=l; i<=h; i++) A[i] = B[i];
}
```

m-way merging: merging m sorted lists into a single list at a time

### Iterative MergeSort
2-way

time = O($n\log{n}$)

```cpp
void ImergeSort(int A[], int n){
	int p,i,l,mid,h;
	
	for(p=2; p<=n; p*=2){
		for(i=0; i+p-1<n; i=i+p){
			l=i;
			h=i+p-1;
			mid=floor(l+h/2);
			Merge(A,l,mid,h);
		}
		if(p/2<n)
			Merge(A,0,p/2,n-1);
	}	
}
```

### Recursive MergeSort

time = O($n\log{n}$)
merging done in Postorder
space = O($n$)
A=n, B=n, stack=logn => 2n+logn

```cpp
void mergeSort(int A[], int l, int h){
	if(l<h){
		mid = floor(l+h/2);
		MergeSort(A,l,mid);
		MergeSort(A,mid+1,h);
		Merge(A,l,mid,h);
	}
}
```