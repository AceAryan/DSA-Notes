Complete se Incomplete banjayega to usko jo bhi last element hai usse replace kardo aur fir poore heap ko adjust karna padega, us node ko niche bhejo by swapping with the bigger child

```cpp
void Delete (int A[], int n) {
	int x,i,j;
	x = A[n];
	A[1] = A[n];
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
	A[n] = x;
}
```

deleted elements ko heap ke bahar store karsakte ho, array ka size utna hi hai to vacant space bachi hui hai - this is **Heapsort**

