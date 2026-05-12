- create Heap - root to leaf transition ( comparison with parent )
- Heapify - root to leaf ( comparison with children )
- fastest method to create Heap 

```cpp
void heapifyDown(int A[], int n, int i) {
    int largest = i;
    int left = 2*i + 1;
    int right = 2*i + 2;

    if (left < n && A[left] > A[largest])
        largest = left;
    if (right < n && A[right] > A[largest])
        largest = right;
    if (largest != i) {
        swap(A[i], A[largest]);
        heapifyDown(A, n, largest);
    }
}

void Heapify(int A[], int n) {
    for (int i = n/2 - 1; i >= 0; i--) {
        heapifyDown(A, n, i); // 1-based indexing
    }
}
```
==O(n)== (we don't process half of the elements - leaves)