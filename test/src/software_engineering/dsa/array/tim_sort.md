# tim_sort
## 🔨Complexity
- T.C = 
- S.C = 
## 📘Abstract
```ad-abstract
This is used buy default in python and for objects in Java. The way Tim sort works is it divides the array into various parts known as run and then for each run it sorts the array using [[insertion_sort]] as it is very good for small chunks and then it chooses two runs and then merges them based on merge of [[merge_sort]]
```
[[insertion_sort]][[merge_sort]]
## 🏃 Algorithm Run
- 
## 🤓 Further Optimization
- 
## 💻 Code
```python
def insertion_sort(arr, left=0, right=None):
    if right is None:
        right = len(arr) - 1

    for i in range(left + 1, right + 1):
        key = arr[i]
        j = i - 1
        while j >= left and arr[j] > key:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key

def merge(arr, left, mid, right):
    left_size = mid - left + 1
    right_size = right - mid
    left_arr = arr[left:mid + 1]
    right_arr = arr[mid + 1:right + 1]

    i = j = 0
    k = left

    while i < left_size and j < right_size:
        if left_arr[i] <= right_arr[j]:
            arr[k] = left_arr[i]
            i += 1
        else:
            arr[k] = right_arr[j]
            j += 1
        k += 1

    while i < left_size:
        arr[k] = left_arr[i]
        i += 1
        k += 1

    while j < right_size:
        arr[k] = right_arr[j]
        j += 1
        k += 1

def tim_sort(arr):
    min_run = 32
    n = len(arr)

    # Perform insertion sort on small subarrays
    for i in range(0, n, min_run):
        insertion_sort(arr, i, min((i + min_run - 1), n - 1))

    size = min_run
    while size < n:
        for start in range(0, n, size * 2):
            mid = min(start + size - 1, n - 1)
            end = min(start + size * 2 - 1, n - 1)
            merge(arr, start, mid, end)
        size *= 2

    return arr

```