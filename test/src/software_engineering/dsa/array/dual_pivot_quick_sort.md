# dual_pivot_quick_sort
## 🔨Complexity
- T.C = 
- S.C = 
## 📘Abstract
```ad-abstract
It is an extension of quick sort here we use two pivots by default. the first pivot should be smaller then second if its not then swap them. Break the array into three parts <first pivot >second pivot and >first pivot but <second pivot and then recursively sort these too.
Used in java by default
```
## 🏃 Algorithm Run
- Choose two pivots one at left end of the array and another at right end of the array ![[Pasted image 20230714203531.png]]
- Swap them if first pivot is smaller then second ![[Pasted image 20230714203552.png]]
- Break the array into three parts. One that is smaller then first pivot another greater then first but less then second and last greater then second ![[Pasted image 20230714203704.png]]
- Move the pivots to their actual position and recursively sort the tree parts![[Pasted image 20230714203749.png]]
- 
## 🤓 Further Optimization
- 
## 💻 Code
```python
def double_pivot_sort(arr, low, high):
    if low < high:
        if arr[low] > arr[high]:
            arr[low], arr[high] = arr[high], arr[low]

        left_pivot = arr[low]
        right_pivot = arr[high]

        i = low + 1
        k = low + 1
        j = high - 1

        while k <= j:
            if arr[k] < left_pivot:
                arr[k], arr[i] = arr[i], arr[k]
                i += 1
            elif arr[k] >= right_pivot:
                while arr[j] > right_pivot and k < j:
                    j -= 1
                arr[k], arr[j] = arr[j], arr[k]
                j -= 1
                if arr[k] < left_pivot:
                    arr[k], arr[i] = arr[i], arr[k]
                    i += 1
            k += 1

        i -= 1
        j += 1
        arr[low], arr[i] = arr[i], arr[low]
        arr[high], arr[j] = arr[j], arr[high]

        double_pivot_sort(arr, low, i - 1)
        double_pivot_sort(arr, i + 1, j - 1)
        double_pivot_sort(arr, j + 1, high)

def double_pivot_quick_sort(arr):
    double_pivot_sort(arr, 0, len(arr) - 1)
    return arr

```