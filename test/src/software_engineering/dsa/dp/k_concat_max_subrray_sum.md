# 🧩 Que
- [Link](https://leetcode.com/problems/k-concatenation-maximum-sum/?envType=list&envId=50wroh7h)
Given an integer array `arr` and an integer `k`, modify the array by repeating it `k` times.

For example, if `arr = [1, 2]` and `k = 3` then the modified array will be `[1, 2, 1, 2, 1, 2]`.

Return the maximum sub-array sum in the modified array. Note that the length of the sub-array can be `0` and its sum in that case is `0`.
```ad-question
title: Test Case
**Input:** arr = [1,2], k = 3
**Output:** 9
```

---
# Abstract
```ad-abstract
There are few cases look at main explaination
```

- Tags #unsolved 
--- 
# 🕵️‍♂️ Main Logic
- ![[Pasted image 20230712025752.png]]
- Case 1 -> ans = maximumSuffixSum + arraySum*(k-2) + maximumPrefixSum
- Case 2 -> ans = KadensAlgoSum
- Case 3 -> ans = maximumSuffixSum + maximumPrefixSum

---
# ☠️ My thought process
- You didn't consider the first case correctly you just thought `sum*k` for that case
---

# 💻 Code
```cpp
int kConcatenationMaxSum(vector<int>& arr, int k) {
	int n = arr.size(),gsum = 0,sum = 0,gMax = 0,cMaxSum = 0,mod = 1e9+7;
	gsum = accumulate(arr.begin(),arr.end(),gsum);
	int maxSuf = gsum,maxPre = 0;
	for(int i = 0 ; i < n ; i++){
		sum += arr[i];
		maxSuf = max(maxSuf,gsum-sum);
		maxPre = max(sum,maxPre);
		cMaxSum = max(cMaxSum+arr[i],arr[i]);
		gMax = max(gMax,cMaxSum);
	}

	if(k == 1) return gMax;
	return (max(max(0ll,(long long)(k-2)*sum)+maxSuf+maxPre,(long long)gMax))%mod;
}
```
---
