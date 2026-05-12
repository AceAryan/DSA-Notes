## 1. Display ()
```cpp
for (int i=0; i<length; i++){
	printf("%d",A[i]);
}
```
==time comp== = O($n$)
## 2. Add / Append (x)
```cpp
A[length] = x;
Length++;
```
==time comp== = O($1$)

**Important** : `(*str).prop = str -> prop`

## 3. Insert (index, x)
```cpp
for (int i=Length; i>index; i--){
	A[i] = A[i-1];
}
A[index] = x;
Length++;
```
==time comp== = best O($1$) , worst O($n$)

## 4. Delete (index)
```cpp
x = A[index];
for (i=index; i<Length-1; i++){
	A[i] = A[i+1];

Length--;
```
==time comp== = best O($1$) , worst O($n$)

## 5. Search

#### 5.1 Linear Search
```cpp
for (i=0; i<Length; i++){
	if (key==A[i]){
		return i;
	}
}
return -1;
```
==time comp== = best O($1$) , worst O($n$), average O($n$)

**Improving Linear Search** :
(waapis same array pe same cheez search karenge to result fast aye)
###### 5.1.1. Transposition 
ek ek index aage leke aarahe hai
```cpp
for (i=0; i<Length; i++){
	if (Key == A[i]){
		swap(A[i],A[i-1]);
		return i-1;
	}
}
```

###### 5.1.2. Move to Front (Head)
```cpp
for (i=0; i<Length; i++){
	if (Key == A[i]){
		swap(A[i],A[0]);
		return 0;
	}
}
```

#### 5.2 Binary Search

```cpp
Algorithm BinSearch (l, h, key){
	while (l<=h){
		mid = (l+h)/2; // floor function 
		if (Key==A[mid])
			return mid;
		else if (Key < A[mid])
			h = mid - 1;
		else
			l = mid + 1;
	}
	return -1;
}
```

==time comp== = best O($1$) , worst O($\log(n)$), average O($\log(n)$)

## 6. Get (index , x)
O($1$)
## 7. Set (index, x)
O($1$)
## 8. Avg () , Max (), Min (), Sum ()
O($n$)
## 9. Reversing
*without auxiliary array :*
```cpp
for (i=0; j=Length-1; i<j; i++; j--){
	temp = A[i];
	A[i] = A[j];
	A[j] = temp;
}
```
==time comp== = O($n$)
## 10. Shift / Rotate
