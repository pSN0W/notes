# counting_sort
## 🔨Complexity
- T.C = O(n)
- S.C = O(n)
## 📘Abstract
```ad-abstract
The idea is pretty simple you create an array of range min(arr) to max(arr) and for each of them you store their frequencies and then you finally overwrite the original array. These are well suited for string sorting
```
## 🏃 Algorithm Run
- Decide min and max and create a corresponding frequency map ![[Pasted image 20230714141558.png]]
- To fill the freq map you can use value-min = index ![[Pasted image 20230714141729.png]]
- You do this for all the element to get the final array
## 🤓 Further Optimization
- One optimization that you can do is calculate the prefix sum of the freq map ![[Pasted image 20230714143349.png]]
- Now you can write position of an element in the array as given in the optimized code. If the numbers are repeated then initially you give it farthest index and then you decrease the count value to give ones at lesser index. This is really useful for [[radix_sort]]
## 💻 Code
```python
def countSort(arr)
	mn,mx = len(arr)
	freq = [0]*(mx-mn+1)
	for num in arr:
		freq[num-mn]+=1
	j = 0
	for i in range(len(arr)):
		while freq[j] == 0:
			j+=1
		arr[i] = j + mn
		freq[j] -= 1
```
---
# 🔬Optimized Code
```python
def countSort(arr)
	mn,mx = len(arr)
	freq = [0]*(mx-mn+1)
	for num in arr:
		freq[num-mn]+=1
	for i in range(1,len(freq)):
		freq[i] += freq[i-1]
	output = [0]*len(arr)
	for num in arr:
		new_idx =  freq[num-mn] - 1
		output[new_idx] = num
		freq[num-mn] -= 1
	return output
```
---
