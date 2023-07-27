# bucket_sort
## 🔨Complexity
- T.C = O(nlgn)
- S.C = O(n)
## 📘Abstract
```ad-abstract
The idea is to bucket the elements of array into smaller buckets and then for each bucket you perform the sorting. The bucket sort is best when elements are uniformly distributed, then each bucket will have 1 element. If it is scattered then one of the bucket can have all the n elements and hence it boils down to O(nlgn)
```
## 🏃 Algorithm Run
- Put different elements in different buckets![[Pasted image 20230714202409.png]]
- If you are sorting floats then you can multiply by 10 and take the first index ![[Pasted image 20230714202500.png]]
- Similarly for string you can make buckets using the MSB. ![[Pasted image 20230714202535.png]]
- 
## 🤓 Further Optimization
- 
## 💻 Code
```python
def bucket_sort(arr):
    # Find the maximum value in the array
    max_value = max(arr)
    # Create empty buckets
    num_buckets = len(arr)
    buckets = [[] for _ in range(num_buckets)]

    # Assign elements to buckets
    for value in arr:
        index = int(value * num_buckets / (max_value + 1))
        buckets[index].append(value)

    # Sort each bucket and concatenate the results
    sorted_arr = []
    for bucket in buckets:
        sorted_arr.extend(sorted(bucket))

    return sorted_arr

```