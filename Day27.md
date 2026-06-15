# Day 27-50 Days of Code

 Date: 15-06-2026

---

##  DSA Questions Solved
(Binary search on answers)
- [Single Element in a Sorted Array](https://leetcode.com/problems/single-element-in-a-sorted-array/)
- [Find Peak Element](https://leetcode.com/problems/find-peak-element/)
- [Square Root(in logN)](https://www.geeksforgeeks.org/problems/square-root/1)
- [nth root of a number](https://www.geeksforgeeks.org/problems/find-nth-root-of-m5843/1)

####  C++ Code
[Single Element in a Sorted Array]
O(logN)
```cpp
int singleNonDuplicate(vector<int>& nums) {
        
        int n = nums.size();
        int low=1, high= n-2;
        if(n==1) return nums[0];
        if(nums[0]!=nums[1]) return nums[0];
        if(nums[n-1]!=nums[n-2]) return nums[n-1];
        while(low<=high){
            int mid=(low+high)/2;
            if(nums[mid-1]!=nums[mid] && nums[mid+1]!=nums[mid]) return nums[mid];
            if(mid%2==0 && nums[mid+1]==nums[mid]) low=mid+1;
            else if(mid%2==0 && nums[mid-1]==nums[mid]) high=mid-1;
            else if(mid%2!=0 && nums[mid+1]==nums[mid]) high=mid-1;
            else if(mid%2!=0 && nums[mid-1]==nums[mid]) low=mid+1;
        }
        return -1;
    }
```
or simpler: 

```cpp
int singleNonDuplicate(vector<int>& nums) {
        int n = nums.size();
        int low=1, high= n-2;
        if(n==1) return nums[0];
        if(nums[0]!=nums[1]) return nums[0];
        if(nums[n-1]!=nums[n-2]) return nums[n-1];
        while(low<=high){
            int mid=(low+high)/2;
            if(nums[mid-1]!=nums[mid] && nums[mid+1]!=nums[mid]) return nums[mid];
            if((mid%2==0 && nums[mid+1]==nums[mid]) || (mid%2!=0 && nums[mid-1]==nums[mid])) low=mid+1;
            else high=mid-1;
        }
        return -1;
    }
```

[Find Peak Element]

```cpp
int findPeakElement(vector<int>& nums) {
        
        int n = nums.size();
        int low =1, high=n-2;

        if(n==1) return 0;
        if(nums[1]<nums[0]) return 0;
        if(nums[n-2]<nums[n-1]) return n-1;

        while(low<=high){
            int mid = (low+high)/2;
            if(nums[mid]>nums[mid-1] && nums[mid]>nums[mid+1]) return mid;
            if(nums[mid-1]<nums[mid]){
                    low=mid+1;
            } 
            else high=mid-1;
        }
        return -1;
    }
```

[Square Root(in logN)] - also asked as "Maximum number whose square is <= n".
```cpp
int floorSqrt(int n) {
        // code here
        int ans;
        int low=0, high=n;
        
        while(low<=high){
            int mid=(low+high)/2;
            if(mid*mid<=n) {
                ans=mid;
                low=mid+1;
            }
            else high=mid-1;
        }
        return ans;
    }
```

[nth root of a number]

```cpp
    int funcc(int mid, int n, int m){
        int ans=1;
        for(int i=0;i<n;i++){
            ans*=mid;
            if(ans>m) return 2;
        }
        if(ans==m) return 1;
        else return 0;
    }
    int nthRoot(int n, int m) {
        // Code here
        int low =0, high=m;
        while(low<=high){
            int mid=(low+high)/2;
            if(funcc(mid, n , m)==1) return mid;
            else if(funcc(mid, n , m)==0) low=mid+1;
            else high=mid-1;
        }
        return -1;
    }
```