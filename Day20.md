# Day 20-50 Days of Code

 Date: 04-02-2026

---

##  DSA Questions Solved
- [Binary Search](https://leetcode.com/problems/binary-search/)

####  C++ Code
[Iterative]

```cpp
int search(vector<int>& nums, int target) {
        int n = nums.size();
        int front=0, back=n-1;
        int mid;
        while(front<=back){
            mid=(front+back)/2;
            if(nums[mid]==target) return mid;
            if(nums[mid]<target) {
                front=mid+1;
            }
            else{
                back=mid-1;
            }
        }
        return -1;
    }
```

[Recursive]

```cpp
    int bs(vector<int> &nums, int low, int high, int target){
        if(low>high) return -1;
        int mid=(low+high)/2;
        if(nums[mid]==target) return mid;
        else if(nums[mid]>target) return bs(nums, low, mid-1, target);
        return bs(nums, mid+1, high, target);
    }
    int search(vector<int>& nums, int target) {
       return bs(nums, 0, nums.size()-1, target);
    }
```