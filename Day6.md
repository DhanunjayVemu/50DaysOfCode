# Day6 – 50 Days of Code

 Date: 12-01-2026

---

##  DSA Questions Solved
- [Single Number](https://leetcode.com/problems/single-number/)


####  C++ Code
[Single Number]

```cpp
    int singleNumber(vector<int>& nums) {
        int val=0;
        for(int i=0;i<nums.size();i++){
            val=val^nums[i];
        }
        return val;
    }
```