# merge_sort
## 🔨Complexity
- T.C = O(nlgn)
- S.C = O(n)
## 📘Abstract
```ad-abstract
The idea is to first divide the array into half and then sort the two halfs and then merge them.
```
## 🏃 Algorithm Run
- The first step is to divide. ![[Pasted image 20230713200913.png]]
- Next is to merge the divided array in the same manner ![[Pasted image 20230713201005.png]]
## 🤓 Further Optimization
- 
## 💻 Code
```python
def merge(arr, l, m, r):
	n1 = m - l + 1
    n2 = r - m
 
    # create temp arrays
    L = [0] * (n1)
    R = [0] * (n2)
 
    # Copy data to temp arrays L[] and R[]
    for i in range(0, n1):
        L[i] = arr[l + i]
 
    for j in range(0, n2):
        R[j] = arr[m + 1 + j]
 
    # Merge the temp arrays back into arr[l..r]
    i = 0     # Initial index of first subarray
    j = 0     # Initial index of second subarray
    k = l     # Initial index of merged subarray
 
    while i < n1 and j < n2:
        if L[i] <= R[j]:
            arr[k] = L[i]
            i += 1
        else:
            arr[k] = R[j]
            j += 1
        k += 1
 
    # Copy the remaining elements of L[], if there
    # are any
    while i < n1:
        arr[k] = L[i]
        i += 1
        k += 1
 
    # Copy the remaining elements of R[], if there
    # are any
    while j < n2:
        arr[k] = R[j]
        j += 1
        k += 1

def mergeSort(arr, l, r):
	if l < r:
		m = (l+r)//2
		mergeSort(arr, l, m)
		mergeSort(arr, m+1, r)
		merge(arr, l, m, r)
```