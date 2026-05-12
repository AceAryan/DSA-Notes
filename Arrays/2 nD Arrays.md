## 2D Arrays
***memory 1D array ki tarah hi allocate hogi, compiler hume row aur columns ke terms mai access karne dega***

**3 ways :**

| `int A[3][4]` | `int *A[3]`                                | `int **A` |
| ------------- | ------------------------------------------ | --------- |
| stack         | pehle array stack,<br>baaki saare heap mai | heap      |
*Access* karne ke liye 2 nested For loops

## Array Representation by Compiler

$$
Logical/ Relative Address (A[i]) = (Base Address) + i*(Size of Datatype)
$$

*Logical Address* = compile time ke wakt
*Base Address* = runtime ke wakt
###### Calculations For **2D Arrays** (`A[m][n]`) :

$Lo$ = Base Adress
$w$ = size of datatype

*Row Major* ( $a00 a01 a02 a10 a11$ )
$$
A[i][j] = Lo + (i*n + j)*w
$$
*Column Major* ( $a00 a10 a20 a01 a11$ )
$$
A[i][j] = Lo + (i + j*m)*w
$$

###### *Row Major* For **nD Arrays** :
( Left to Right )
**Array** = `A[d1][d2]...[dn]`
$$
A[i1][i2]...[in] = Lo + \Sigma_{p=1}^{n}[ i_{p} + \Pi_{q=p+1}^{n}d_{q}] * w
$$

==time complexity== = O($n^2$)

taking common and simplifying : ( *Horner's Rule* ) = O($n$)