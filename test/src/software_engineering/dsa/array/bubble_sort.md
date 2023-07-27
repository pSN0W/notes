# Bubble Sort
## 🔨Complexity
- T.C = O(n* n)
- S.C = O(1)
## 📘Abstract
```ad-abstract
The whole idea is to perform swap between adjacent elements. At each iteration the algorithm takes the max element to the right most side of the array. This process continues for n iteration until the whole array is sorted

```
## 🏃 Algorithm Run
- For each iteration swap adjacent incorrect order element
	- [10, 4, 30, 22, 28, 17]
	- [4, 10, 30, 22, 28, 17]
	- [4, 10, 30, 22, 28, 17]
	- [4, 10, 22, 30, 28, 17]
	- [4, 10, 22, 28, 30, 17]
	- [4, 10, 22, 28, 17, 30]
## 🤓 Further Optimization
- You don't need to run the inner loop from 0 to n - 1. You can just go up to n - i - 1 because after that they are in the correct order.
- Stop the outer loop when no more swaps are performed
## 💻 Code
```c++
void bubble_sort(vector<int> &arr){
	for(int i=0; i<arr.size() - 1; i++){
		bool didSwap = false;
		for(int j=0; j<arr.size() - i - 1; j++){
			if(arr[i]>arr[i+1]){
				swap(arr[i],arr[i+1]);
				didSwap = true;
			}
		}
		if (!didSwap){
			break;
		}
	}
}
```