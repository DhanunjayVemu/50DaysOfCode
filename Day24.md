
# Day 24-50 Days of Code

 Date: 11-06-2026

---

##  DSA Questions Solved
- [Search in rotated sorted array](https://leetcode.com/problems/search-in-rotated-sorted-array/)

####  C++ Code
[Search in rotated sorted array]

```cpp

int search(vector<int>& nums, int target) {
         int n = nums.size();
         int low=0;
         int high= n-1;

         while(low<=high){
            int mid = (low+high)/2;
            if(nums[mid]==target) return mid;
            if(nums[mid]>=nums[low]){
                if(target>=nums[low] && target<=nums[mid]){
                    high=mid-1;
                }
                else{
                    low=mid+1;
                }              
            }
             else{
                if(target>=nums[mid] && target<=nums[high]){
                    low=mid+1;
                }
                else{
                    high=mid-1;
                }              
            }    
         }
            return -1;
    }
```
