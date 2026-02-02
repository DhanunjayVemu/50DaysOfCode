# Day 18-50 Days of Code

 Date: 02-02-2026

---

##  DSA Questions Solved
- [Spiral Matrix](https://leetcode.com/problems/spiral-matrix/)

####  C++ Code

Optimal approach (The only approach to this question)


```cpp
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
            vector<int> result;
            int m = matrix.size();
            int n=matrix[0].size();

            int top=0,bottom=m-1;
            int left=0, right=n-1;

            while(top<=bottom && left<=right){

                for(int i=left;i<=right;i++){
                    result.push_back(matrix[top][i]);
                }
                top++;

                for(int i=top;i<=bottom;i++){
                    result.push_back(matrix[i][right]);
                }
                right--;

                if(top<=bottom){
                for(int i=right;i>=left;i--){
                    result.push_back(matrix[bottom][i]);
                }
                bottom--;
                }

                if(left<=right){
                for(int i=bottom; i>=top; i--){
                    result.push_back(matrix[i][left]);
                }
                left++;
                }
            }

        return result;
    }
};
```