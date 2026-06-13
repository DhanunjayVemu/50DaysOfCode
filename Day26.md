# Day 26-50 Days of Code

 Date: 13-06-2026

---

##  DSA Questions Solved
- [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)
- [Find Kth Rotation (in logN)](https://www.geeksforgeeks.org/problems/rotation4723/1)

####  C++ Code
[Find Minimum in Rotated Sorted ArrayI]

```cpp
int findMin(vector<int>& nums) {
        
        int n = nums.size();
        int low=0,  high=n-1;
        int mini=INT_MAX ;

        while(low<=high){
            int mid=(low+high)/2;
            if(nums[mid]>=nums[low]){
                mini=min(mini, nums[low]);
                low=mid+1;
            }
            else{
                mini=min(mini, nums[mid]);
                high=mid-1;
            }
        }
        return mini;
    }
```

[Find Kth Rotation (in logN)] Same as finding minimum but we have to return the index cause that gives the roation count;
```cpp
int findKRotation(vector<int> &arr) {
        // Code Here
        
        int n =arr.size();
        int low=0, high = n-1;
        int ans=0; int mini=INT_MAX;
        while(low<=high){
            int mid=(low+high)/2;
            if(arr[low]<=arr[mid]){
                if(arr[low]<mini) {
                    mini=arr[low];
                    ans=low;
                }
                low=mid+1;
            }
            else {
                if(arr[mid]<mini){
                    mini=arr[mid];
                    ans=mid;
                }
                high=mid-1;
            }
        }
        return ans;
    }
```