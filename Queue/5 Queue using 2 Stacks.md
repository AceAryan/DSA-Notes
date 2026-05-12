2 Stacks : S1 and S2

Enqueue in S1
Want to Delete? : If (S2 Empty), Transfer all Elements of S1 to S2, delete from S2

```cpp
void enqueue (int x){
	push(&s1,x);
}
```

```cpp
int dequeue(){
	int x = -1;
	if (isEmpty(s2)){
		if (isEmpty(s1)){
			printf("Queue Empty");
			return x;
		}
		else{
			while(!isEmpty(s1)){
				push(&s2,pop(&s1));
			}
		}
	}
	return pop(&s2);
}
```