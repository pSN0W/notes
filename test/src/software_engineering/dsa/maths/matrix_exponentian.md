# Abstract
```ad-abstract
The idea with matrix exponentiation is to reduce the complexity of the problem by expresiing the recurrence as a product of multiplication

```

# Example 1
Le's say we want to calculate solution of recurrence `f(n) = f(n-1)*f(n-2)`
Defibe F(n+1) = [f(n+1), f(n)]. Guess a matrix such that T.F(n) = F(n+1)
![[Pasted image 20230717013654.png]]
Now T^(n-2) can be calculates in lg(n) time using binary exponentian. We will just have to take res as identity matrix in [[power]]

# Example 2
Lets say you are given the recurrence
`f(n) = a*f(n-1) + b*f(n-2) + c*f(n-3) + d` you can exponentiate that too
![[Pasted image 20230717014347.png]]

# Matrix Class is really helpful
```cpp
struct Mat {
	vector<vector<int>> m;
	int n;
	Mat(int n){
		this->n = n;
		m.resize(n,vector<int>(n,0));
	}
	void identity(){
		for(int i=0;i<n;i++){
			m[i][i] = 1;
		}
	}
	Mat operator*(Mat a){
		Mat res = Mat(a.size());
		for(int i=0;i<n;i++){
			for(int j=0;j<n;j++){
				for(int k=0;k<n;k++){
					res.m[i][j] += m[i][k]*a.m[k][j];
				}
			}
		}
		return res;
	}
}
```