# Day 28-50 Days of Code

 Date: 16-06-2026

---

##  DSA Questions Solved
(Binary search on answers)
- [Minimum Number of Days to Make m Bouquets](https://leetcode.com/problems/minimum-number-of-days-to-make-m-bouquets/)



####  C++ Code

[Minimum Number of Days to Make m Bouquets]

```cpp
 bool possible(vector<int>& bloomDay, int day ,int m, int k){
        int cnt=0;
        int bloom=0;
        for(int i=0;i<bloomDay.size();i++){
            if(bloomDay[i]<=day){
                cnt++;
            }
            else {
                bloom+=cnt/k;
                cnt=0;
            }
        }
        bloom+=cnt/k;
        if(bloom>=m) return true;
        return false;
}

    int minDays(vector<int>& bloomDay, int m, int k) {
        
        int low=*min_element(bloomDay.begin(), bloomDay.end());
        int high=*max_element(bloomDay.begin(), bloomDay.end());
        int ans=-1;
        while(low<=high){
            int mid=(low+high)/2;
            if(!possible(bloomDay, mid, m, k)){
                low=mid+1;
            }
            else {
                high=mid-1;
                ans=mid;
            }
        }

        return ans;
    }
```