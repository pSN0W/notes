# Abstract
```ad-abstract
Once you have build the pascal triangle you can query for nCr in O(1) time.
```

# Pascal Triangle

| n   | nC0 | nC1 | nC2 | nC3 | nC4 | nC5 | nC6 | nC7 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0   | 1   |     |     |     |     |     |     |     |
| 1   | 1   | 1   |     |     |     |     |     |     |
| 2   | 1   | 2   | 1   |     |     |     |     |     |
| 3   | 1   | 3   | 3   | 1   |     |     |     |     |
| 4   | 1   | 4   | 6   | 4   | 1   |     |     |     |
| 5   | 1   | 5   | 10  | 10  | 5   | 1   |     |     |
| 6   | 1   | 6   | 15  | 20  | 15  | 6   | 1   |     |
| 7   | 1   | 7   | 21  | 35  | 35  | 21  | 7   | 1   | 

# To Build Pascal
- Append 1 at the begining and end of the row
- then for `arr[i][j] = arr[i][j] + arr[i][j-1]`

