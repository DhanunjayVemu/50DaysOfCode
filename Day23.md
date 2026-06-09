# Day 23-50 Days of Code

 Date: 09-06-2026

---

##  DSA Questions Solved
- [First and Last position of element (in logN TC)](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)
- [Count occurences of a number (in logN TC)](https://www.geeksforgeeks.org/problems/number-of-occurrence2259/1)

####  C++ Code
[First and Last position of element (in logN TC)] 

```cpp

    vector<int> searchRange(vector<int>& nums, int target) {
        
        int lb = lower_bound(nums.begin(), nums.end(), target)-nums.begin();
        int ub = upper_bound(nums.begin(), nums.end(), target)-nums.begin();

        if(lb==nums.size() || nums[lb]!=target) return {-1,-1};
        
        return {lb, ub-1};
    }

```

[Count occurences of a number (in logN TC)]

```cpp
int countFreq(vector<int>& arr, int target) {
        // code here
        int n=arr.size();
        int lb = lower_bound(arr.begin(), arr.end(), target) -arr.begin();
        int ub = upper_bound(arr.begin(), arr.end(), target) -arr.begin();
        
        if(lb==n || arr[lb]!=target) return 0;
        
        return ub-lb;
    }
```