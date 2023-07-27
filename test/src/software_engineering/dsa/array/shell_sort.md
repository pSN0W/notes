# shell_sort
## 🔨Complexity
- T.C = O(n^1.25)
- S.C = O(1)
## 📘Abstract
```ad-abstract
It is an extension of [[insertion_sort]]. Where in insertion sort you compare adjacent elements, here you compare elements at a distance of gap and then you gradually reduce the gap until it reaches 1.
```
[[insertion_sort]]
## 🏃 Algorithm Run
- If you have n array element then initially you will have a gap of ceil(n/2).
- ![[Pasted image 20230713195731.png]]
- In next iteration you reduce the gap by half
- ![[Pasted image 20230713195808.png]]
- And then half again
- ![[Pasted image 20230713195836.png]]
## 🤓 Further Optimization
- 
## 💻 Code
```python
def shellSort(arr):
	n = len(arr)
	gap = n
	while True:
		gap = gap//2 + gap%2
		for i in range(gap,n):
			j = i
			tmp = arr[i]
			while j>=gap and arr[j-gap] > tmp:
				arr[j] = arr[j-gap]
				j -= gap
			arr[j] = tmp
		if gap == 1:
			break
```