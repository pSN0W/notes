# 🧩 Que
- [Link](https://leetcode.com/problems/count-all-valid-pickup-and-delivery-options/)
Given n order each order consist of pickup and delivery. Count all valid pickup/delivery possible sequences such that delivery(i) is always after of pickup(i)
```ad-question
title: Test Case
**Input:** n = 2
**Output:** 6
**Explanation:** All possible orders: 
(P1,P2,D1,D2), (P1,P2,D2,D1), (P1,D1,P2,D2), (P2,P1,D1,D2), (P2,P1,D2,D1) and (P2,D2,P1,D1).
This is an invalid order (P1,D2,P2,D1) because Pickup 2 is after of Delivery 2.
```

---
# Abstract
```ad-abstract
This looks pretty similar to [[valid_parenthesis]] and this can be solved in the same way too. Initially assume that you are solving for valid paranthesis problem only where ( => Pickup and ) => Delivery. Everytime you make a pickup you will have option to choose between total-num_pickup_made and every time you make a delivery you can have num_pickup-num_delivered option to choose from.
```

- Tags #unsolved #revise 
--- 
# 🕵️‍♂️ Main Logic
- Everything is same as [[valid_parenthesis]]. You don't put a closing bracket before an opening bracket and shit.
- Now if your num_open is 0. Then you can choose to make any of the pickup P1,P2..Pn.
- If your num_close is 2 and num_open is 4 then you have option to choose any of the two non delivered item to deliver
---
# ☠️ My thought process
- Initially you were doing something like generate all the valid parenthesis and then multiply them by n! to rearrange the pickup but that resulted in the delivery being in the same order as pickup
---

# 💻 Code
```python
class Solution:
    def countOrders(self, n: int) -> int:
        @lru_cache(None)
        def get_val_paranthesis(num_open,num_close):
            if num_open==n and num_close==n:
                return 1
            ans = 0
            if num_open<n:
                ans += ((n-num_open)*get_val_paranthesis(num_open+1,num_close))
            if num_close < num_open:
                ans += ((num_open-num_close)*get_val_paranthesis(num_open,num_close+1))
            return ans%int(1e9+7)
        ans = get_val_paranthesis(0,0)
        return ans
```
---
