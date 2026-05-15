extension of Insertion Sort
adaptive, in-place

gap = $\lfloor n/2\rfloor$ (do /2 every pass till gap=1)

time = O($n\log{n}$)

```cpp
void shellSort(int A[], int n){
	int gap, i, j;
	
	for(gap=n/2; gap>1; gap/=2){
		for(i=gap;i<n;i++{
			temp=A[i];
			j=i-gap;
			while(j>0 && A[j]>temp){
				A[j+gap]=A[j];
				j-=gap;
			}
			A[j+gap]=temp;
		}
	}
}
```