# Day 2 – 50 Days of Code

 Date: 09-01-2026

---

##  DSA Questions Solved
- [Rotate Array](https://leetcode.com/problems/rotate-array/description/)
- [Move Zeros](https://leetcode.com/problems/move-zeroes/)

####  C++ Code
[Rotate array by k elements to the right]
Instead of burte forcing by storing the right most k elements in an array and shifting rest, I noticed a pattern in the examples. On reversing the entire array once, then reversing the first k elements, then reversing the rest n-k elements gives the same effect as rotating the array to the right.

```cpp
void rotate(vector<int>& nums, int k) {
        int n =nums.size();
        k=k%n;
            reverse(nums.begin(),nums.end());
            reverse(nums.begin(),nums.begin()+k);
            reverse(nums.begin()+k,nums.end());
    }
```

[Move Zeroes]
Used one pointer to hold on the index to swap when a non zero value appears in the second index's value
```cpp
void moveZeroes(vector<int>& nums) {
        int nonzeroindex=0;
        for(int i=0;i<nums.size();i++){
            if(nums[i]!=0){ 
                swap(nums[nonzeroindex],nums[i]);
                nonzeroindex++;
            }
        }
     }
```