
# Day 33-50 Days of Code

 Date: 22-06-2026

---

##  DSA Questions Solved
(Binary search on answers)
- [Allocate Minimum Pages](https://www.geeksforgeeks.org/problems/allocate-minimum-number-of-pages0937/1)
- [Split Array Largest Sum](https://leetcode.com/problems/split-array-largest-sum/)

### C++ Code

[Allocate Minimum Pages]
```cpp
 int fun (vector<int> &arr, int maxPages){
        int sum=0;
        int k=1;
        
        for(int i=0;i<arr.size();i++){
            if(sum+arr[i]>maxPages){
                sum=arr[i];
                k++;
            } 
            else{
                sum+=arr[i];
            }
        }
        return k;
    }
    
    int findPages(vector<int> &arr, int k) {
        // code here
        
        if(arr.size()<k) return -1;
        
        int low=*max_element(arr.begin(), arr.end());
        int high=0;
        
        for(int i:arr){
            high+=i;
        }
        int ans=-1;
        while(low<=high){
            int mid=(low+high)/2;
            int x=fun(arr, mid);

            
            if(x<=k){
                high=mid-1;
                ans=mid;
            }
            else if(x>k){
                low=mid+1;
            }
        }
        return ans;
    }
```

[Split Array Largest Sum]

```cpp

int fun(vector<int> &nums, int maxSum){
        int sum=0;
        int k=1;
        for(int i=0;i<nums.size();i++){
            if(sum+nums[i]>maxSum){
                sum=nums[i];
                k++;
            }
            else{
                sum+=nums[i];
            }
        }
        return k;
    }


    int splitArray(vector<int>& nums, int k) {
        
        if(k>nums.size()) return -1;
        
        int low=*max_element(nums.begin(), nums.end());
        int high=0;
        
        for(int x: nums){
            high+=x;
        }

        int ans = -1;
        
        while(low<=high){
            int mid=(low+high)/2;
            if(fun(nums, mid)<=k){
                ans=mid;
                high=mid-1;
            }
            else low=mid+1;
        }
        return ans;
    }

```