works kinda like Hashing

time = O(n)
space = O(n) larger space used = max element

```cpp
void countSort(int A[], int n){
	int max, i,j;
	int *c;
	max = findMax(A,n);
	c = new int[max+1];
	
	for(i=0; i<max+1; i++){
		c[i]=0;
	}
	for(i=0; i<n; i++){
		c[A[i]+1]++;
	}
	i=0; j=0;
	while(i<max+1){
		if(c[i]>0){
			A[j++]=i;
			c[i]--;
		}
		else i++;
	}	
}
```

