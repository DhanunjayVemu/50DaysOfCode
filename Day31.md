
# Day 31-50 Days of Code

 Date: 20-06-2026

---

##  DSA Questions Solved
(Binary search on answers)
- [Capacity To Ship Packages Within D Days](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/)
- []()

### C++ Code
[Capacity To Ship Packages Within D Days]

```cpp
 int fun(vector<int>&arr, int num){
        int package=0, days=1;
        for(int i=0;i<arr.size();i++){
            if(package+arr[i]>num){
                days++;
                package=arr[i];
            }
            else package+=arr[i];
        }
        return days;
    }

    int shipWithinDays(vector<int>& weights, int days) {
        
        int low=*max_element(weights.begin(), weights.end());
        int high=0;
        int ans=-1;
        for(int i: weights){
            high+=i;
        }
        while(low<=high){
            int mid=(low+high)/2;
            int val =fun(weights, mid);
            if(val<=days){
                ans=mid;
                high=mid-1;
            }
            else low=mid+1;
        }
        return ans;
    }
```