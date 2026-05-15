binSort with less bins, size of array = 0 to 9 (if array has decimal number system)

mth pass: drop no. in mth digit bin - `A[i]%(10^m)`
extract in FIFO

time = O(dn) = O(d) , d = max no. of digits
space = O(n)
