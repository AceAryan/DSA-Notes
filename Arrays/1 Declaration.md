array = consecutive memory blocks mai data stored
## Traversal

jab bhi array ko traverse karna ho :
```cpp
for (int i=0; i<Length; i++){
	array[i];
}
```

## Static vs Dynamic Arrays

|                       | ==Where== | ==Size==     |
| --------------------- | --------- | ------------ |
| `int A[5]`            | Stack     | compile time |
| `int *p = new int[5]` | Heap      | runtime      |
ye hai for arrays declared in stack `int A[5]` aise types ( static ) ke liye
inka size change nahi kar sakte
#### Dynamic

```cpp
int *ptr = new int[5];
```
c++ mai aise allocate karsakte hai warna c mai 
```cpp
ptr = (int*) malloc (5*sizeof(int));
```
## Increasing Array Size

```cpp
int *p = new int[5];
int *q = new int[10]; 

for (int i=0; i<5; i++){
	q[i]=p[i]; 
} // p ka data transfer karne se pehle q mai daal diya

p = q; // original ptr ko iska address pakda diya to wo ab 10 size ke array ko store karega
q = NULL;

delete []p;
```

***raw pointers don't store size, size must be tracked manually***