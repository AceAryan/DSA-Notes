aka Selection Exchange Sort, Partition Exchange Sort

select pivot, 2 ptr : i>pivot and j<=pivot, when i>j swap pivot with j, array partitioned into 2 -> quicksort recursively

time comp worst(already sorted) =  O($n^2$) -> swap pivot with mid (make pivot as mid)
time comp best (partitioning only in middle) = O($n\log_2{n}$)
avg = O($n\log_2{n}$)

```cpp
int Partition(int A[], int l, int h){
	int Pivot = A[l];
	int i=l, j=h;
	
	do{
		do{i++;}while(A[i]<=Pivot);
		do{j--;}while(A[j]>Pivot);
		if(i<j){
			swap(A[i],A[j]);
		}
	}while(i<j);
	swap(A[l],A[j]);
	return j;
}
```

selection sort - find position then element
quick sort - find element then position