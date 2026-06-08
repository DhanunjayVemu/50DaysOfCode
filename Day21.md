# Day 21-50 Days of Code

 Date: 07-06-2026

---

##  DSA Questions Solved
- [Lower bound](https://www.geeksforgeeks.org/problems/implement-lower-bound/1)
- [Upper bound](https://www.geeksforgeeks.org/problems/implement-upper-bound/1)
- [Search insert position](https://leetcode.com/problems/search-insert-position/submissions/2025258677/)

####  C++ Code
[Lower bound] - Lowest index number which is >= target. 

```cpp

    int lowerBound(vector<int>& arr, int target) {
        // code here
        int n =arr.size();
        int low=0, high=n-1;
        int ans=n;
        
        while(low<=high){
            int mid=(low+high)/2;
            if(arr[mid]>=target){
                ans=mid;
                high=mid-1;
            }
            else{
                low=mid+1;
            }
        }
            return ans;
    }

```

[Upper bound] - Lowest index number which is > target. 

```cpp
int upperBound(vector<int>& arr, int target) {
        // code here
        int n =arr.size();
        int low=0, high=n-1;
        int ans=n;
        
        while(low<=high){
            int mid=(low+high)/2;
            if(arr[mid]>target){
                ans=mid;
                high=mid-1;
            }
            else{
                low=mid+1;
            }
        }
        
            return ans;
    }

```
[Search insert position]

```cpp
int searchInsert(vector<int>& nums, int target) {
        int lb=lower_bound(nums.begin(), nums.end(), target)-nums.begin();
        return lb;
    }
```