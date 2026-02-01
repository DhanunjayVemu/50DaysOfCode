# Day 16-50 Days of Code

 Date: 31-01-2026

---

##  DSA Questions Solved
- [Rotate Image](https://leetcode.com/problems/rotate-image/)

####  C++ Code

Brute:
used a new matrix of the same size and placed elements based on this pattern mat[j][n-1-i]=matrix[i][j] 
TC: O(n^2), SC: O(n^2) 

```cpp
    void rotate(vector<vector<int>>& matrix) {
        
        int m=matrix.size();
        int n=matrix[0].size();
        vector<vector<int>> mat(m,vector<int>(n));
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                mat[j][n-1-i]=matrix[i][j];
            }
        }
        matrix=mat;
    }
```
Optimal:
Transposed the matrix first, then reversed each row's order
TC: O(n^2), SC: O(1)

```cpp
 void rotate(vector<vector<int>>& matrix) {
        
        int n=matrix.size();

        for(int i=0;i<n-1;i++){
            for(int j=i+1;j<n;j++){
                swap(matrix[i][j],matrix[j][i]);
            }

        }
 
        for(int i=0;i<n;i++){
            reverse(matrix[i].begin(),matrix[i].end());
        }
    
    }
```