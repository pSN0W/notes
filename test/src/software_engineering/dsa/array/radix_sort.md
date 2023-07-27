# radix_sort
## 🔨Complexity
- T.C = 
- S.C = 
## 📘Abstract
```ad-abstract
It is an extension of [[counting_sort]]. The main drawback of count sort was that you had to create an array as big as mx-mn. This solves the problem by soting the numbers bits wise. You intially consider the least significant bit then sort on basis of that and then slowly increase the bit precedence.
```
[[counting_sort]]
## 🏃 Algorithm Run
- Initial array ![[Pasted image 20230714145202.png]]
- Perform count sort on the basis of least significant bit ![[Pasted image 20230714145125.png]]
- Then use the second index ![[Pasted image 20230714145232.png]]
- Then finally the most significant bit ![[Pasted image 20230714145255.png]]
- If you have negative number in your array too. Then divide the array in two parts and then take absolute value of the numbers. Sort both of the part and then join them by reversing the negative numbers. This is done to avoid mod complications fro negative numbers ![[Pasted image 20230714145509.png]]
## 🤓 Further Optimization
- 
## 💻 Code
```python
def radix_sort(arr):
	def countSort(exp, nums):
		freq = [0]*10
		for num in nums:
			freq[(num/exp)%10]+=1
		# create a prefix sum
		for i in range(1,10):
			freq[i] += freq[i-1]
		output = [0]*len(nums)
		for num in nums:
			new_idx = freq[(num/exp)%10] - 1
			output[new_idx] = num
			freq[(num/exp)%10] -= 1
		arr = output
	def radix(nums):
		mx = max(nums)
		exp = 1
		while mx/exp>0:
			countSort(exp, nums)
			exp *= 10
		return nums
	negs = [abs(x) for x in arr if x<0]
	pos = [x for x in arr if x>=0]
	pos_sort = radix(pos)
	neg_sort = [-1*x for x in radix(negs)[::-1]]
	return neg_sort + pos_sort
```