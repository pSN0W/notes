# Insertion Sort
## 🔨Complexity
- T.C = O(n * n)
- S.C = O(1)
## 📘Abstract
```ad-abstract
The idea is similar to selection sort. You can divide the array into two parts. Left side is sorted and right side is unsorted. You go left to right and for each incorrect element you put it in its correct position in sorted array.
```
## 🏃 Algorithm Run
![[Pasted image 20230630021856.png]]
## 🤓 Further Optimization
- For moving to correct position you can stop when the previous is less than current
## 💻 Code
```cpp
void insertion_sort(vector<int> &arr){
	for(int i=1; i<arr.size(); i++){
		for(int j=i-1;j>=0 and arr[j]>arr[j+1];j--){
			swap(arr[j],arr[j+1]);
		}
	}
}
```