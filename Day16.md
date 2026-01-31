# Day 16-50 Days of Code

 Date: 31-01-2026

---

##  DSA Questions Solved
- [Set matrix zeroes](https://leetcode.com/problems/set-matrix-zeroes/)

####  C++ Code
[Brute approach]
I changed the values of elements in the same row and column of existing zeroes to -1. So, they dont mix with the existing zeroes, and later on changed the -1s to 0s.
TC: O(n^3)
SC: O(1) 
```cpp
 void setZeroes(vector<vector<int>>& matrix) {
        int m, n;
        if (matrix.empty() || matrix[0].empty())
            return;
            m=matrix.size();                                             
             n=matrix[0].size();
 
        for(int i=0;i<m; i++){
            for(int j=0;j<n;j++){
                if(matrix[i][j]==0){
                    for(int k=0;k<m;k++){
                        if(matrix[k][j]!=0)
                        matrix[k][j]=-1;
                    }
                    for(int k=0;k<n;k++){
                        if(matrix[i][k]!=0)
                        matrix[i][k]=-1;
                    }
                }
            }
        }
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(matrix[i][j]==-1) matrix[i][j]=0;
            }
        }

    }
```

[Better approach]
Stored column and row indices, where the values should be zero in two new arrays, and replaced them with zero later on.
TC: O(2mn)
SC: O(m+n)
```cpp
    void setZeroes(vector<vector<int>>& matrix) {
        int m=matrix.size();
        int n=matrix[0].size();
        vector<int> rows(m,0);
        vector<int> cols(n,0);

        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(matrix[i][j]==0){
                   cols[j]=1;
                   rows[i]=1;
                }
            }
        }

        for(int i=0;i <m;i++){
            for(int j=0; j<n;j++ ){
                if(rows[i]==1 || cols[j]==1){
                    matrix[i][j]=0;
                }
            }
        }


    }
```

Optimal 

```cpp
 void setZeroes(vector<vector<int>>& matrix) {
        if(matrix.empty() || matrix[0].empty()) return;

        int m =matrix.size();
        int n=matrix[0].size();

        int col0=1;

        for(int i=0;i<m;i++){
            for(int j=0;j<n; j++){
                if(matrix[i][j]==0){
                    matrix[i][0]=0;
                    if(j!=0)
                    matrix[0][j]=0;
                    else col0=0;
                }

            }
        }

        for(int i=1;i<m;i++){
            for(int j=1;j<n;j++){
                if(matrix[i][j]!=0){
                if(matrix[i][0]==0 || matrix[0][j]==0){
                    matrix[i][j]=0;
                }
                }
            }
        }

        if(matrix[0][0]==0){
            for(int j=0;j<n;j++){
                matrix[0][j]=0;
            }
        }

        if(col0==0){
            for(int i=0;i<m;i++){
                matrix[i][0]=0;
            }
        }

    }

```
