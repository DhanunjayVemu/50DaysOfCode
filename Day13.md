# Day 13-50 Days of Code

 Date: 24-01-2026

---

##  DSA Questions Solved
- [Permutations](https://leetcode.com/problems/permutations/)
- [Next permuatation](https://leetcode.com/problems/next-permutation/)

####  C++ Code

[Permutations]
Used recursion, first I selected each number to swap with the first element of the array pointed by idx. Then I called the recursion to fill the next values and form multiple cases and then again swapped them back for backtracking to revert back a few cases to list other cases.
``` cpp
 void permu(vector<int> &nums, int idx, vector<vector<int>> &result){
        if(idx==nums.size()){
            result.push_back(nums);
            return;
        }
        for(int i=idx;i<nums.size();i++){
            swap(nums[idx], nums[i]);
            permu(nums,idx+1,result);
            swap(nums[idx],nums[i]);
        }
    }

    vector<vector<int>> permute(vector<int>& nums) {
        vector<vector<int>> result;
        permu(nums,0,result);
        return result;
    }
```

[Next permutation]
I checked for a dip of order from the end of the array and took it as idx. Then I serached for the smallest number present to the right of idx that is greater than nums[idx] and swapped them both. Finally I reversed the subarray from idx+1 to the end cause that would get the smallest set greater than the original set, i.e., the next permutation.
```cpp
 void nextPermutation(vector<int>& nums) {
        int n=nums.size();
        int idx=-1;
        for(int i=n-2;i>=0;i--){
            if(nums[i]<nums[i+1]){
                idx=i; break;
            }
        }
        if(idx==-1){
                reverse(nums.begin(),nums.end());
                return;
            }
        for(int i=n-1;i>idx;i--){
            if(nums[i]>nums[idx]){
                swap(nums[i],nums[idx]);
                break;
            }
        }
        reverse(nums.begin()+idx+1,nums.end());
        return ;
    }
```