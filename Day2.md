# Day 2 – 50 Days of Code

 Date: 08-01-2026

---

##  DSA Questions Solved
- [Check if Array Is Sorted and Rotated](https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/description/)
- [Remove Duplicates from sorted array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)

####  C++ Code

[Check if array is sorted and rotated]
Here, I counted the number of times there is a drop in order in the given array. If it is greater than 1, then the array is not sorted and rotated.
```cpp
bool check(vector<int>& nums) {
        int n=nums.size();
        int cnt=0;
        for(int i=0;i<n;i++){
            if(nums[(i+1)%n]<nums[i]) cnt++;
        }
        return (cnt<=1);
    }
```


[Remove Duplicates from sorted array]
I kept a slow pointer to only move when there is a number changed in the array. The second pointer moves across the array comparing with the slow pointer, if it's not equal then the next value of the slow pointer is changed to the fast pointer's value.
```cpp
int removeDuplicates(vector<int>& nums) {
       int n=nums.size();
        int pt1=0;
        for(int i=1;i<n;i++){
            if(nums[pt1]!=nums[i])
                nums[++pt1]=nums[i];
        }
        return pt1+1;
    }
```