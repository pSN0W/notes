# Selection Sort
## 🔨Complexity
- T.C = O(n * n)
- S.C = O(1)
## 📘Abstract
```ad-abstract
The whole array is divided into two parts. The sorted part and the unsorted part. In each iteration you find the minimum from the unsorted part and then move it to the sorted part.
```
## 🏃 Algorithm Run
The red denote the partition between sorted and unsorted part
![[Pasted image 20230630013314.png]]
## 🤓 Further Optimization
- Swap only when the index is different
## 💻 Code
```cpp
void selection_sort(vector<int> &arr){
	for(int i=0; i<arr.size() - 1; i++){
		int min_index = i;
		for(int j = i+1;j<arr.size();j++){
			if(arr[j]<arr[min_index]){
				min_index = j;
			}
		}
		if(min_index!=i){
			swap(arr[i],arr[min_index]);
		}
	}
}
```