# Day12-50 Days of Code

 Date: 22-01-2026

---

##  DSA Questions Solved
- [Rearrange array elements by size](https://leetcode.com/problems/rearrange-array-elements-by-sign/description/)

####  C++ Code
[Rearrange array elements by sign] Brute approach
``` cpp
 vector<int> rearrangeArray(vector<int>& nums) {
         vector<int> pos;
         vector<int> neg;
         int n=nums.size();
         for(int i=0;i<n;i++){
            if(nums[i]>0) pos.push_back(nums[i]);
            else neg.push_back(nums[i]);
         }
         int l=0;
         for(int i=0;i<pos.size();i++){
            nums[l]=pos[i];
            l=l+2;
         }
         int m=1;
         for(int j=0;j<neg.size();j++){
            nums[m]=neg[j];
            m=m+2;
         }
         return nums;
    }
```
[Rearrange array elements by sign]-Optimal
```cpp
vector<int> rearrangeArray(vector<int>& nums) {
        int n=nums.size();
        vector<int> ans(n);
        int posidx=0, negidx=1;
        for(int i=0;i<n;i++){
            if(nums[i]>0){ ans[posidx]=nums[i]; posidx+=2;}
            else{ ans[negidx]=nums[i]; negidx+=2;}
        }
        return ans;    
    }

```