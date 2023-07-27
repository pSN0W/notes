# Abstract
```ad-abstract
When you want duplicates it is really easy you can choose one of the possible way and then proceed down that path but things complicate when you want to avoid duplicates. Then one thing that becomes improtant is that if in a subtree you are skipping a number you will skip it throughout.
```

# Example Problem
You have [2,3] find total combination that sums up to 7.

# With Duplicates
To generate the solution it is really easy. You just choose all the possible choice at each index.
![[Pasted image 20230717200736.png]]
Can you see the problem with this. The problem of duplicates appear because you chose 2 in a subtree that you skipped earlier.

# Without Duplicates
If we use indexing and say that if you skipped the ith element in this branch then you can't choose ith again. You will need to find the target using i+1 index
![[Pasted image 20230717201209.png]]