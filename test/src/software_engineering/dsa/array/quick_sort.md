# quick_sort
## 🔨Complexity
- T.C = O(nlgn) If you take the pivot as first element and array is increasing the O(n^2)
- S.C = O(1) O(lgn) for stack memory
## 📘Abstract
```ad-abstract
The idea is to first choose a pivot element and then move it to its correct place and then sort the remaining two parts.
```
## 🏃 Algorithm Run
- First choose the middle element in this case 22 ![[Pasted image 20230713202111.png]]
- Swap it to get it to end of the array. ![[Pasted image 20230713202147.png]]
- Now you will need to divide the array into two parts one is greater than 22 and other less than 22. For this what you can do is have two pointers where one pointer iterates the whole array and other sits where the value is just greater than pivot. You swap when you find value less than pivot![[Pasted image 20230713202348.png]]
- You have divided the array in two parts one is bigger than 22 and other is less than that and 22 is at its correct place ![[Pasted image 20230713202445.png]]
- Perform the same operation in the two subparts
## 🤓 Further Optimization
- 
## 💻 Code
```python
# Function to find the partition position
def partition(array, low, high):
 
    # choose the rightmost element as pivot
    pivot = array[high]
 
    # pointer for greater element
    i = low - 1
 
    # traverse through all elements
    # compare each element with pivot
    for j in range(low, high):
        if array[j] <= pivot:
 
            # If element smaller than pivot is found
            # swap it with the greater element pointed by i
            i = i + 1
 
            # Swapping element at i with element at j
            (array[i], array[j]) = (array[j], array[i])
 
    # Swap the pivot element with the greater element specified by i
    (array[i + 1], array[high]) = (array[high], array[i + 1])
 
    # Return the position from where partition is done
    return i + 1
 
# function to perform quicksort
 
 
def quickSort(array, low, high):
    if low < high:
 
        # Find pivot element such that
        # element smaller than pivot are on the left
        # element greater than pivot are on the right
        pi = partition(array, low, high)
 
        # Recursive call on the left of pivot
        quickSort(array, low, pi - 1)
 
        # Recursive call on the right of pivot
        quickSort(array, pi + 1, high)

```