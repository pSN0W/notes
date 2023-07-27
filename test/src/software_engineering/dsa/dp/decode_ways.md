# 🧩 Que
- [Link](https://leetcode.com/problems/decode-ways/)
You are given an encoding where encoding is done in this way:
- A -> "1"
- B -> "2"
- ....
- Z -> "26"
Given the encoded string you have to decode it. Remember that "06" != "6" hence won't be mapped to F. You have to find out the number of possible decodings.
```ad-question
title: Test Case
**Input:** s = "226"<br>
**Output:** 3<br>
**Explanation:** "226" could be decoded as "BZ" (2 26), "VF" (22 6), or "BBF" (2 2 6).

```

---
```ad-abstract
Recurrence <br>
ans[idx] = ans[idx+1] + (ans[idx+2] if ans[idx:idx+2]<"26") <br>
Base Case <br>
if idx >=  len(s) -> 1 <br>
if s[idx] == "0" -> 0
```

- Tags #solved
--- 
# 🕵️‍♂️ Main Logic
 - You can just consider the current index and tell the next index to find all the possible decoding ways. You can consider the current idx along with idx+1 and ask the number of possible ways from idx+2.<br>
---
# ☠️ My thought process

-  Same as main logic
---

# 💻 Code

```cpp
class Solution {

public:

	string s;
	vector<int> dp;

	int solve(int idx){
		if(idx>=s.size()) return 1;
		if(dp[idx]!=-1) return dp[idx];
		
		// since 0 can not be mapped to any and 06 is not allowed
		if(s[idx]=='0') return 0;
		
		int ans = 0;
		ans += solve(idx+1);
		if(idx+1<s.size() and s.substr(idx,2)< "27") ans += solve(idx+2);
		return dp[idx] = ans;
	}

	int numDecodings(string s_) {
		s = s_;
		dp.resize(s.size()+1,-1);
		return solve(0);
	}

};
```
---
